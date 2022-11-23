# n8n Trigger

The n8n Trigger node gets triggered when the n8n instance is started or restarted. The n8n Trigger node can be used to notify when the n8n instance starts.

## Node Reference

- Events
    - ***Instance started:*** Triggers when the n8n instance is started or restarted

## Example Usage

This workflow allows you to receive a message on Mattermost when your n8n instance starts. You can also find the [workflow](https://n8n.io/workflows/1058) on n8n.io. This example usage workflow uses the following nodes.
- [n8n Trigger]()
- [Mattermost](/integrations/builtin/app-nodes/n8n-nodes-base.mattermost/)

The final workflow should look like the following image.

![A workflow with the Webhook node](/_images/integrations/builtin/core-nodes/n8ntrigger/workflow.png)

### 1. n8n Trigger node

The n8n Trigger node will trigger the workflow whenever n8n starts.

1. Select 'Instance started' from the ***Events*** dropdown list.

In the screenshot below, you will notice that the node triggers the workflow when the n8n instance starts.

![Using the n8n Trigger node to trigger the workflow](/_images/integrations/builtin/core-nodes/n8ntrigger/n8ntrigger_node.png)

### 2. Mattermost node (post: message)

This node will send a message in the `workflow` channel on Mattermost.

1. First of all, you'll have to enter credentials for the Mattermost node. You can find out how to enter credentials for this node [here](/integrations/builtin/credentials/mattermost/).
2. Select a channel from the ***Channel ID*** dropdown list.
3. Click on the gears icon next to the ***Message*** field click on ***Add Expression***.

4. Enter the following message in the ***Expression*** field: `Your n8n instance started at {{$json["timestamp"]}}.`.
5. Click on ***Execute Node*** to run the workflow.

In the screenshot below, you will notice that the node sends a message to Mattermost.

![Using the Mattermost node to send a message to a channel](/_images/integrations/builtin/core-nodes/n8ntrigger/mattermost_node.png)

!!! note "Activate workflow for production"
    This example workflow uses the n8n Trigger node, which is a Trigger node. You'll need to save the workflow and then click on the Activate toggle on the top right of the screen to activate the workflow.

