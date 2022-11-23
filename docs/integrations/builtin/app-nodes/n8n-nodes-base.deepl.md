# DeepL

[DeepL](https://deepL.com) is a machine translation service that allows you to translate text to different languages.

!!! note "Credentials"
    You can find authentication information for this node [here](/integrations/builtin/credentials/deepL/).


## Basic Operations

* Language
    * Translate data

## Example Usage

This workflow allows you to translate cocktail instructions to French. You can also find the [workflow](https://n8n.io/workflows/998) on n8n.io. This example usage workflow uses the following nodes.
- [Start](/integrations/builtin/core-nodes/n8n-nodes-base.start/)
- [HTTP Request](/integrations/builtin/core-nodes/n8n-nodes-base.httprequest/)
- [DeepL]()

The final workflow should look like the following image.

![A workflow with the DeepL node](/_images/integrations/builtin/app-nodes/deepl/workflow.png)

### 1. Start node

The Start node exists by default when you create a new workflow.

### 2. HTTP Request node (GET)

This node will make a GET request to the API `https://www.thecocktaildb.com/api/json/v1/1/random.php` to fetch a random cocktail. This information gets passed on to the next node in the workflow.

1. Enter `https://www.thecocktaildb.com/api/json/v1/1/random.php` in the ***URL*** field.
2. Click on ***Execute Node*** to run the node.

In the screenshot below, you will notice that the node makes a GET request to the API and returns information about a random cocktail.

![Using the HTTP Request node to get the information about a random cocktail](/_images/integrations/builtin/app-nodes/deepl/httprequest_node.png)

### 3. DeepL node (translate: language)

This node will translate the cocktail instructions that we got from the previous node to French. To translate the instructions in your language, select your language instead.

1. First of all, you'll have to enter credentials for the DeepL node. You can find out how to do that [here](/integrations/builtin/credentials/deepL/).

2. Click on the gears icon next to the ***Text*** field and click on ***Add Expression***.
3. Select the following in the ***Variable Selector*** section: Current Nodes > Input Data > JSON > drinks > [item: 0] > strInstructions. You can also add the following expression: `{{$json["drinks"][0]["strInstructions"]}}`.
4. Select 'French' from the ***Target Language*** dropdown list.
5. Click on ***Execute Node*** to run the node.

In the screenshot below, you will notice that the node translates the instructions of the cocktail to French.

![Using the DeepL node to translate the instructions to French](/_images/integrations/builtin/app-nodes/deepl/deepl_node.png)
