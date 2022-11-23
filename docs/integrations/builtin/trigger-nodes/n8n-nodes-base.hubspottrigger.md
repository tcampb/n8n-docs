# HubSpot Trigger

[HubSpot](https://www.hubspot.com/) provides tools for social media marketing, content management, web analytics, landing pages, customer support, and search engine optimization.

!!! note "Credentials"
    For this node, you will have to retrieve the App ID and Client secret from the 'Using OAuth' section as well as the Developer API Key from the 'Using Developer API Key' section. You can find authentication information for this node [here](/integrations/builtin/credentials/hubspot/).


!!! note "Webhooks"
    If you activate a second trigger, the previous trigger stops working. This is because the trigger registers a new webhook with HubSpot when activated. HubSpot only allows one webhook at a time. 


## Example Usage

This workflow allows you to receive updates when a new contact is created in HubSpot. You can also find the [workflow](https://n8n.io/workflows/628) on the website. This example usage workflow would use the following node.

- [HubSpot Trigger]()

The final workflow should look like the following image.

![A workflow with the HubSpot Trigger node](/_images/integrations/builtin/trigger-nodes/hubspottrigger/workflow.png)


### 1. HubSpot Trigger node

1. First of all, you'll have to enter credentials for the HubSpot Trigger node. You can find out how to do that [here](/integrations/builtin/credentials/hubspot/).
2. Enter the HubSpot App ID in the ***App ID*** field. You can find out how to obtain the ***App ID*** in the link above.
3. Click on ***Execute Node*** to run the workflow.

!!! note "Activate workflow for production"
    You'll need to save the workflow and then click on the Activate toggle on the top right of the screen to activate the workflow. Your workflow will then be triggered as specified by the settings in the HubSpot Trigger node.





