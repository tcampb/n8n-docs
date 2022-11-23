# Shopify Trigger

[Shopify](https://www.shopify.com/) is an e-commerce platform that allows users to set up an online store and sell their products.

!!! note "Credentials"
    You can find authentication information for this node [here](/integrations/builtin/credentials/shopify/).



## Example Usage

This workflow allows you to receive updates when a new order is created in Shopify. You can also find the [workflow](https://n8n.io/workflows/547) on the website. This example usage workflow would use the following node.

- [Shopify Trigger]()

The final workflow should look like the following image.

![A workflow with the Shopify Trigger node](/_images/integrations/builtin/trigger-nodes/shopifytrigger/workflow.png)


### 1. Shopify Trigger node

1. First of all, you'll have to enter credentials for the Shopify Trigger node. You can find out how to do that [here](/integrations/builtin/credentials/shopify/).
2. Select 'Orders create' from the *Topic* dropdown list.
3. Click on *Execute Node* to run the workflow.

!!! note "Activate workflow for production"
    You'll need to save the workflow and then click on the Activate toggle on the top right of the screen to activate the workflow. Your workflow will then be triggered as specified by the settings in the Shopify Trigger node.

