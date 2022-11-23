# User management

!!! info "Feature availability"
		
		* Available on self-hosted and selected Cloud plans. Refer to [Cloud Pricing](https://n8n.io/pricing/){:target=_blank .external-link} for more information.
		* Not available on Desktop.
		* Cloud users don't need to configure SMTP, and can't configure email templates.


User management in n8n allows you to invite people to work in your n8n instance. It includes:

* Login and password management
* Adding and removing users
* Two account types: owner and member

!!! note "Privacy"
    The user management feature doesn't send personal information, such as email or username, to n8n.


## Account types

There are two account types, owner and member. The account type affects the user permissions and access.

* Owner: this is the account that set up user management. There's one owner account for each n8n instance. You can't transfer ownership.
  The owner can:
    * Add and remove users
    * See all workflows
    * Delete tags
		* See all credentials (but not the sensitive information)
* Members: these are normal n8n users.
  Members can:
    * See all workflow tags, create new tags, and assign tags to their workflows. Members can't delete tags.
    * Change their own password.
    * See their own workflows.

!!! note "Create a member-level account for the owner"
    We recommend that owners create a member-level account for themselves. Owners can see all workflows, but there is no way to see who created a particular workflow, so there is a risk of overriding other people's work if you build and edit workflows as an owner.


## Set up on self-hosted n8n

There are three stages to set up user management in n8n:

1. Configure your n8n instance to use your SMTP server.
2. Start n8n and follow the setup steps in the app.
3. Invite users.

### Step one: SMTP

You need an SMTP server for user management to send invites and password resets. Get the following information from your SMTP provider:

* Server name
* SMTP username
* SMTP password
* SMTP sender name

To set up SMTP with n8n, configure the SMTP environment variables for your n8n instance. For information on how to set environment variables, refer to [Configuration](/hosting/configuration/)

| Variable | Type | Description | Required? |
| -------- | ---- | ----------- | --------- |
| `N8N_EMAIL_MODE` | string | smtp | Required |
| `N8N_SMTP_HOST` | string | _your_SMTP_server_name_ | Required |
| `N8N_SMTP_PORT` | number | _your_SMTP_server_port_ Default is `465`.| Optional |
| `N8N_SMTP_USER` | string | _your_SMTP_username_ | Required |
| `N8N_SMTP_PASS` | string | _your_SMTP_password_ | Required |
| `N8N_SMTP_SENDER` | string | You can select the sender name from the sender addresses. Example: "N8N _contact@n8n.com_"| Required |
| `N8N_SMTP_SSL` | boolean | Whether to use SSL for SMTP (true) or not (false). Defaults to `true`. | Optional | 
| `N8N_UM_EMAIL_TEMPLATES_INVITE` | string | Full path to your HTML email template. This overrides the default template for invite emails. | Optional |
| `N8N_UM_EMAIL_TEMPLATES_PWRESET` | string | Full path to your HTML email template. This overrides the default template for password reset emails. | Optional |

If your n8n instance is already running, you need to restart it to enable the new SMTP settings.

!!! note "More configuration options"
    There are more configuration options available as environment variables. Refer to [Environment variables](/hosting/environment-variables/) for a list. These include options to disable tags, workflow templates, and the personalization survey, if you don't want your users to see them.


!!! note "New to SMTP?"
    If you're not familiar with SMTP, this [blog post by SendGrid](https://sendgrid.com/blog/what-is-an-smtp-server/) offers a short introduction, while [Wikipedia's Simple Mail Transfer Protocol article](https://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol) provides more detailed technical background.


### Step two: in-app setup

When you set up user management for the first time, you create an owner account.

1. Open n8n. The app displays a signup screen.
2. Enter your details. Your password must be at least eight characters, including at least one number and one capital letter.
3. Click **Next**. n8n logs you in with your new owner account.

### Step three: invite users

You can now invite other people to your n8n instance.

1. Sign in with your owner account.
2. Click your user icon > **Settings**. n8n opens your **Personal settings** page.
3. Click **Users** to go to the **Users** page.
4. Click **Invite**.
5. Enter the new user's email address.
6. Click **Invite user**. n8n sends an email with a link for the new user to join.

## Set up on n8n Cloud

!!! warning "Irreversible upgrade"
	Once you upgrade your Cloud instance to an n8n version with user management, you can't downgrade your version.

### Step one: in-app setup

When you set up user management for the first time, you create an owner account.

1. Open n8n. The app displays a signup screen.
2. Enter your details. Your password must be at least eight characters, including at least one number and one capital letter.
3. Click **Next**. n8n logs you in with your new owner account.

### Step two: invite users

You can now invite other people to your n8n instance.

1. Sign in with your owner account.
2. Click your user icon > **Settings**. n8n opens your **Personal settings** page.
3. Click **Users** to go to the **Users** page.
4. Click **Invite**.
5. Enter the new user's email address.
6. Click **Invite user**. n8n sends an email with a link for the new user to join.

## Manage users

The **Settings** > **Users** page shows all users, including ones with pending invitations.

### Delete a user

1. Click the menu icon by the user you want to delete.
2. Confirm you want to delete them.
3. If they're an active user, choose whether to copy their workflow data and credentials to a new user, or permanently delete their workflows and credentials.

### Resend an invitation to a pending user

Click the menu icon by the user, then click **Resend invite**.

## Skipping or disabling user management

You don't have to use n8n's user management feature. You can:

* Leave it enabled, but choose to skip the setup step. You can use n8n as normal. If you want to set up user management later, go to **Settings** > **Users**.
* Self-hosted only: Disable the feature completely using the `N8N_USER_MANAGEMENT_DISABLED` environment variable. Setting this environment variable to `true` completely hides the feature in your n8n instance. You can't use this setting if you have already set up an owner account.

## Best practices

This sections contains advice on best practices relating to user management in n8n.

* We recommend that owners create a member-level account for themselves. Owners can see all workflows, but there is no way to see who created a particular workflow, so there is a risk of overriding other people's work if you build and edit workflows as an owner.
* Users must be careful not to edit the same workflow simultaneously. It is possible to do it, but the users will overwrite each other's changes.
* To move workflows between accounts, export the workflow as JSON, then import it to the new account. Note that this action loses the workflow history.
* Webhook paths must be unique across the entire instance. This means each webhook path must be unique for all workflows and all users. By default, n8n generates a long random value for the webhook path, but users can edit this to their own custom path. If two users set the same path value:
    * The path works for the first workflow that is run or activated.
    * Other workflows will error if they try to run with the same path.
* If you run n8n behind a reverse proxy, set the following environment variables so that emails are generated with the correct URL:
  * `N8N_HOST`
  * `N8N_PORT`
  * `N8N_PROTOCOL`
  * `N8N_EDITOR_BASE_URL`
  More information on these variables is available in [Environment variables](/hosting/environment-variables/).
* You can't use n8n's user management with basic auth. If your n8n instance currently uses basic auth to authenticate the user, you must remove this before setting up user management.
