# Mandrill

[Mandrill](https://mandrillapp.com/) is a transactional email service developed by MailChimp.

!!! note "Credentials"
    You can find authentication information for this node [here](/integrations/builtin/credentials/mandrill/).


## Basic Operations

* Message
    * Send message based on template.
    * Send message based on HTML.

## Example Usage

This workflow allows you to send an email using a template via Mandrill. You can also find the [workflow](https://n8n.io/workflows/571) on this website. This example usage workflow uses the following two nodes.

- [Start](/integrations/builtin/core-nodes/n8n-nodes-base.start/)
- [Mandrill]()

The final workflow should look like the following image.

![A workflow with the Mandrill node](/_images/integrations/builtin/app-nodes/mandrill/workflow.png)

### 1. Start node

The start node exists by default when you create a new workflow.

### 2. Mandrill node

1. First of all, you'll have to enter credentials for the Mandrill node. You can find out how to do that [here](/integrations/builtin/credentials/mandrill/).
2. Select the template you would like to use from the *Template* dropdown list.
3. Enter the email address from which you want to send the email in the *From Email* field.
4. Enter the recipient email address in the *To Email* field.
5. Click on *Execute Node* to run the workflow.




