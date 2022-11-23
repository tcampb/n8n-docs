# Emelia

[Emelia](https://emelia.io) is a cold-mailing tool.

!!! note "Credentials"
    You can find authentication information for this node [here](/integrations/builtin/credentials/emelia/).


## Basic Operations

* Campaign
    * Add Contact
    * Create
    * Get
    * Get All
    * Pause
    * Start
* Contact List
    * Add
    * Get All

## Example Usage

This workflow allows you to create a campaign, add a contact, and get the campaign from Emelia. You can also find the [workflow](https://n8n.io/workflows/961) on n8n.io. This example usage workflow uses the following nodes.
- [Start](/integrations/builtin/core-nodes/n8n-nodes-base.start/)
- [Emelia]()

The final workflow should look like the following image.

![A workflow with the Emelia node](/_images/integrations/builtin/app-nodes/emelia/workflow.png)

### 1. Start node

The Start node exists by default when you create a new workflow.

### 2. Emelia node (campaign: create)

This node will create a new campaign in Emelia.

1. First of all, you'll have to enter credentials for the Emelia node. You can find out how to do that [here](/integrations/builtin/credentials/emelia/).
2. Select 'Create' from the ***Operation*** dropdown list.
3. Enter the campaign name in the ***Campaign Name*** field.
4. Click on ***Execute Node*** to run the node.

In the screenshot below, you will notice that the node creates a new campaign.

![Using the Emelia node to create a new campaign](/_images/integrations/builtin/app-nodes/emelia/emelia_node.png)

### 3. Emelia1 node (campaign: addContact)

This node will add a contact to the campaign that we created in the previous node.

1. Select the credentials that you entered in the previous node.
2. Select 'Add Contact' from the ***Operation*** dropdown list.
3. Select the campaign from the ***Campaign ID*** dropdown list.
4. Enter the contact's email address in the ***Contact Email*** field.
5. Click on the ***Add Field*** button and select 'First Name'.
6. Enter the first name in the ***First Name*** field.
7. Click on ***Execute Node*** to run the node.

In the screenshot below, you will notice that the node adds the contact to the campaign that we created in the previous node.

![Using the Emelia node to add a contact to a campaign](/_images/integrations/builtin/app-nodes/emelia/emelia1_node.png)

### 4. Emelia2 node (campaign: get)

This node will get the information about the campaign that we created earlier.

1. Select the credentials that you entered in the previous node.
2. Select 'Get' from the ***Operation*** dropdown list.
3. Click on the gears icon next to the ***Campaign ID*** field and click on ***Add Expression***.
5. Select the following in the ***Variable Selector*** section: Nodes > Emelia > Output Data > JSON > _id. You can also add the following expression: `{{$node["Emelia"].json["_id"]}}`.
6. Click on ***Execute Node*** to run the node.


In the screenshot below, you will notice that the node returns the information of the campaign.

![Using the Emelia node to return the information a campaign](/_images/integrations/builtin/app-nodes/emelia/emelia2_node.png)
