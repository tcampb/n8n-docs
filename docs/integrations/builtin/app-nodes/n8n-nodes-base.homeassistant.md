# Home Assistant

[Home Assistant](https://www.home-assistant.io/) is a free and open-source software for home automation that is designed to be the central control system for smart home devices with focus on local control and privacy.

!!! note "Credentials"
    You can find authentication information for this node [here](/integrations/builtin/credentials/homeAssistant/).


## Basic operations

* Camera Proxy
    * Get the camera screenshot
* Config
    * Get the configuration
    * Check the configuration
* Event
    * Create an event
    * Get all events
* Log
    * Get a log for a specific entity
    * Get all logs
* Service
    * Call a service within a specific domain
    * Get all services
* State
    * Create a new record, or update the current one if it already exists (upsert)
    * Get a state for a specific entity
    * Get all states
* Template
    * Create a template

## Example

This workflow allows you to retrieve your current Home Assistant configuration details. This example usage workflow would use the following two nodes.
- [Start](/integrations/builtin/core-nodes/n8n-nodes-base.start/)
- [Home Assistant]()

The final workflow should look like the following image.

![A workflow with the Home Assistant node](/_images/integrations/builtin/app-nodes/homeassistant/workflow.png)

### 1. Start node

The start node exists by default when you create a new workflow.

### 2. Home Assistant node

1. First select your credentials for the Home Assistant node. You can find out how to create credentials [here](/integrations/builtin/credentials/homeAssistant/).
2. From the **Resource** dropdown select **Config**.
3. From the **Operation** dropdown select **Get**.
4. Click on **Execute Node** to run the workflow.

![The Home Assistant node](/_images/integrations/builtin/app-nodes/homeassistant/home_assistant_node.png)
