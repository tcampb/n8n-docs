# Mailjet

[Mailjet](https://www.mailjet.com/) is a cloud-based email sending and tracking system. The platform allows professionals to send both marketing emails and transactional emails. It includes tools for designing emails, sending massive volumes and tracking these messages.

!!! note "Credentials"
    You can find authentication information for this node [here](/integrations/builtin/credentials/mailjet/).


## Basic Operations

* Email
    * Send a email
    * Send a email template
* SMS
    * Send a sms

## Example Usage

This workflow allows you to send an email using Mailjet. You can also find the [workflow](https://n8n.io/workflows/520) on this website. This example usage workflow uses the following two nodes.

- [Start](/integrations/builtin/core-nodes/n8n-nodes-base.start/)
- [Mailjet]()

The final workflow should look like the following image.

![A workflow with the Mailjet node](/_images/integrations/builtin/app-nodes/mailjet/workflow.png)

### 1. Start node

The start node exists by default when you create a new workflow.

### 2. Mailjet node

1. First of all, you'll have to enter credentials for the Mailjet node. You can find out how to do that [here](/integrations/builtin/credentials/mailjet/).
2. Enter the email address from which you want to send the email in the *From Email* field.
3. Enter the recipient email address in the *To Email* field.
4. Enter the subject for the email in the *Subject* field.
5. Enter the content of the email in the *Text* field.
6. Click on *Execute Node* to run the workflow.
