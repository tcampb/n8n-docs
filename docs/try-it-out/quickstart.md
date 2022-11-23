---
description: A quick example to try out n8n.
---

# The very quick quickstart

This quickstart gives you a very quick taste of n8n. Its aim is to allow you to try out the UI, and introduce you to two key features: workflow templates and expressions. It doesn't include detailed explanations or explore concepts.

You will:

* Load a workflow from the workflow templates library
* Add a node and configure it using expressions.
* Run your first workflow

## Step one: Install and run n8n

!!! note "Skip this section if you've already installed n8n or signed up for a Cloud account"

--8<-- "_snippets/try-it-out/install-run-n8n.md"

## Step two: Open a workflow template

n8n provides a quickstart template using training nodes. This allows you to work with fake data, and avoids setting up credentials.

1. Select **Templates**.
2. Search for `Very quick quickstart`.
3. Select the **Very quick quickstart** template to preview it.
4. Select **Use this workflow** to open the template in your own editor.

This is a basic workflow. It:

1. Gets example data from the Customer Datastore node.
2. Uses the Set node to extract just the data you want, and assign that data to variables. In this example, you use the customer name, ID, and description.

Double click a node to explore its settings and how it processes data.

## Step three: Run the workflow

Select **Execute workflow** to run the workflow to check it's working, and load in data for the next steps.

## Step four: Add a node

Add a third node to message each customer and tell them their description. The Customer Messenger node allows you to send a message to fake recipients.

1. Select the **Add node** <span class="inline-image">![Add node icon](/_images/try-it-out/add-node-small.png)</span> connector on the Set node.
2. Search for **Customer Messenger**. n8n shows a list of nodes that match the search.
3. Select **Customer Messenger (n8n training)** to add the node to the canvas. n8n opens the node automatically.
4. You're going to use [expressions](/code-examples/expressions/) to map in the **Customer ID** and create the **Message**:
	1. Drag **customer_ID** from the **INPUT** panel into the **Customer ID** field in the node settings.
    2. Hover over **Message**. Select the **Expression** tab. n8n opens the expressions editor for this field.
    3. Copy this expression into the editor:
        ```
        Hi {{$json.customer_name}},  Your description is {{$json.customer_description}}
        ```
5. Close the expressions editor, then close the **Customer Messenger** node by clicking outside the node or selecting **Back to canvas**.
6. Select **Execute workflow**. n8n runs the workflow.

The complete workflow should look like this:

![Screenshot of completed quickstart workflow](/_images/try-it-out/quickstart/very-quick-quickstart-workflow.png)


## Next steps

* Read n8n's [longer try it out tutorial](/try-it-out/longer-introduction/) for a more complex workflow, and an introduction to more features and n8n concepts.
* Take the [courses](/courses/).


