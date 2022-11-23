# Line

[Line](https://line.me/en/) is a mobile messenger app that allows you to make free voice calls and send messages.

!!! note "Credentials"
    You can find authentication information for this node [here](/integrations/builtin/credentials/line/).


## Basic Operations

* Notification
    * Sends notifications to users or groups

## Example Usage

This workflow allows you to send daily weather updates via a notification using the Line node. You can also find the [workflow](https://n8n.io/workflows/773) on n8n.io. This example usage workflow uses the following nodes.
- [Cron](/integrations/builtin/core-nodes/n8n-nodes-base.cron/)
- [OpenWeatherMap](/integrations/builtin/app-nodes/n8n-nodes-base.openweathermap/)
- [Line]()

The final workflow should look like the following image.

![A workflow with the Line node](/_images/integrations/builtin/app-nodes/line/workflow.png)

### 1. Cron node

The Cron node will trigger the workflow daily at 9 AM.

1. Click on ***Add Cron Time***.
2. Set hours to 9 in the ***Hour*** field.
3. Click on ***Execute Node*** to run the node.

In the screenshot below, you will notice that the Cron node is configured to trigger the workflow every day at 9 AM.

![Using the Cron node to trigger the workflow daily at 9 am](/_images/integrations/builtin/app-nodes/line/cron_node.png)

### 2. OpenWeatherMap node (Current Weather)

This node will return data about the current weather in Berlin. To get the weather updates for your city, you can enter the name of your city instead.

1. First of all, you'll have to enter credentials for the OpenWeatherMap node. You can find out how to do that [here](/integrations/builtin/credentials/openWeatherMap/).
2. Enter `berlin` in the ***City*** field.
3. Click on ***Execute Node*** to run the node.

In the screenshot below, you will notice that the node returns data about the current weather in Berlin.

![Using the OpenWeatherMap node to get weather updates for Berlin](/_images/integrations/builtin/app-nodes/line/openweathermap_node.png)

### 3. Line node (send: notification)

This node will send a notification with the weather update.

1. First of all, you'll have to enter credentials for the Line node. You can find out how to do that [here](/integrations/builtin/credentials/line/).
2. Click on the gears icon next to the ***Message*** field and click on ***Add Expression***.

3. Enter the following message in the ***Expression*** field: `Hey! The temperature outside is {{$node["OpenWeatherMap"].json["main"]["temp"]}}°C.`.
4. Click on ***Execute Node*** to run the node.


In the screenshot below, you will notice that the node sends a notification with the weather update.

![Using the Line node to send weather updates via a notification](/_images/integrations/builtin/app-nodes/line/line_node.png)

!!! note "Activate workflow for production"
    This example workflow uses the Cron node, which is a Trigger node. You'll need to save the workflow and then click on the Activate toggle on the top right of the screen to activate the workflow. Your workflow will then be triggered as specified by the settings in the Cron node.

