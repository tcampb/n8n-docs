# MSG91

[MSG91](https://msg91.com/) is an enterprise SMS Solution providing Bulk SMS, Transactional SMS API, Regional SMS, OTP Verification APIs, Promotional SMS via powerful, and a robust SMS Gateway.

!!! note "Credentials"
    You can find authentication information for this node [here](/integrations/builtin/credentials/msg91/).


## Basic Operations

* SMS
    * Send SMS

## Example Usage

This workflow allows you to send an SMS using MSG91. You can also find the [workflow](https://n8n.io/workflows/511) on the website. This example usage workflow would use the following two nodes.
- [Start](/integrations/builtin/core-nodes/n8n-nodes-base.start/)
- [MSG91]()

The final workflow should look like the following image.

![A workflow with the MSG91 node](/_images/integrations/builtin/app-nodes/msg91/workflow.png)

### 1. Start node

The start node exists by default when you create a new workflow.

### 2. MSG91 node

1. First of all, you'll have to enter credentials for the MSG91 node. You can find out how to do that [here](/integrations/builtin/credentials/msg91/).
2. Enter the sender ID in the *Sender ID* field. You can find instructions on how to obtain the sender ID in the FAQs below.
3. Enter the phone number to which you'll be sending the message in the *To* field.
4. Enter you message in the *Message* field.
5. Click on *Execute Node* to run the workflow.


## FAQs

### How do I find my Sender ID?

1. Log in to your MSG91 dasboard and click on 'Sender Id' in the left panel.
2. If you don't already have one, click on *Add Sender Id +*, fill in the details, and click on the *Save Sender Id* button.
