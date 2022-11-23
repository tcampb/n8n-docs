# Bannerbear

[Bannerbear](https://www.bannerbear.com/) is an API-based image generation service that automatically generates variations of graphic templates.

!!! note "Credentials"
    You can find authentication information for this node [here](/integrations/builtin/credentials/bannerbear/).


## Basic Operations

* Image
    * Create an image
    * Get an image
* Template
    * Get a template
    * Get all templates

## Example Usage

This workflow allows you to create an image using the Bannerbear welcome template. You can also find the [workflow](https://n8n.io/workflows/544) on the website. This example usage workflow would use the following two nodes.
- [Start](/integrations/builtin/core-nodes/n8n-nodes-base.start/)
- [Bannerbear]()

The final workflow should look like the following image.

![A workflow with the Bannerbear node](/_images/integrations/builtin/app-nodes/bannerbear/workflow.png)

### 1. Start node

The start node exists by default when you create a new workflow.

### 2. Bannerbear node

1. First of all, you'll have to enter credentials for the Bannerbear node. You can find out how to do that [here](/integrations/builtin/credentials/bannerbear/).
2. Select 'Welcome Template' from the *Template ID* dropdown list.
3. Click on the *Add Field* dropdown, select 'Wait for Image', and set the slider is set to 'on'.
4. Click on the *Add Modification* button and select 'message' from the *Name* dropdown list.
5. Enter the text in the *Text* field.
6. Click on *Execute Node* to run the workflow.




