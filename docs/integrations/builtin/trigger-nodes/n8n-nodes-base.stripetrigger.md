# Stripe Trigger

Stripe is a suite of payment APIs that powers commerce for online businesses.

!!! note "Credentials"
    You can find authentication information for this node [here](/integrations/builtin/credentials/stripe/).



## Example Usage

This workflow allows you to receive updates for Stripe events. You can also find the [workflow](https://n8n.io/workflows/545) on the website. This example usage workflow would use the following node.
- [Stripe Trigger]()

The final workflow should look like the following image.

![A workflow with the Stripe Trigger node](/_images/integrations/builtin/trigger-nodes/stripetrigger/workflow.png)


### 1. Stripe Trigger node

1. First of all, you'll have to enter credentials for the Stripe Trigger node. You can find out how to do that [here](/integrations/builtin/credentials/stripe/).
2. Select the `*` option in the *Events* field to receive updates when any event is triggered.
3. Click on *Execute Node* to run the workflow.

!!! note "Activate workflow for production"
    You'll need to save the workflow and then click on the Activate toggle on the top right of the screen to activate the workflow. Your workflow will then be triggered as specified by the settings in the Stripe Trigger node.





