# AWS Comprehend

[AWS Comprehend](https://aws.amazon.com/comprehend/) is a natural language processing (NLP) service that uses machine learning to find insights and relationships in a text.

!!! note "Credentials"
    You can find authentication information for this node [here](/integrations/builtin/credentials/aws/).


## Basic Operations

**Text**

- Identify the dominant language
- Analyse the sentiment of the text


## Example Usage

This workflow allows you to analyze the sentiment of feedback received via a Typeform submission and send a message on Mattermost if that feedback is negative. You can also find the [workflow](https://n8n.io/workflows/965) on n8n.io. This example usage workflow uses the following nodes.
- [Typeform Trigger](/integrations/builtin/trigger-nodes/n8n-nodes-base.typeformtrigger/)
- [AWS Comprehend]()
- [IF](/integrations/builtin/core-nodes/n8n-nodes-base.if/)
- [Mattermost](/integrations/builtin/app-nodes/n8n-nodes-base.mattermost/)
- [No Operation, do nothing](/integrations/builtin/core-nodes/n8n-nodes-base.noop/)

The final workflow should look like the following image.

![A workflow with the AWS Comprehend node](/_images/integrations/builtin/app-nodes/awscomprehend/workflow.png)

### 1. Typeform Trigger node

This node will trigger the workflow when a feedback form is submitted. Make sure to create a feedback form for your event.

1. Select 'Access Token' from the ***Authentication*** dropdown list.
2. Enter the credentials for the Typeform Trigger node. You can find out how to do that [here](/integrations/builtin/credentials/typeform/).
3. Select the event feedback form from the ***Form*** dropdown list.
4. Click on ***Execute Node*** to run the node.

In the screenshot below, you will notice that the node triggers the workflow when feedback is submitted. We will pass this feedback to the next nodes in the workflow.

![Using the Typeform Trigger node to trigger the workflow when a feedback form is submitted](/_images/integrations/builtin/app-nodes/awscomprehend/typeformtrigger_node.png)

### 2. AWS Comprehend node (detectSentiment: text)

This node will analyze the sentiment of the feedback that we got from the previous node. We will pass the analysis score to the next node in the workflow.

1. First of all, you'll have to enter credentials for the AWS Comprehend node. You can find out how to enter credentials for this node [here](/integrations/builtin/credentials/aws/).
2. Select 'Detect Sentiment' from the ***Operation*** dropdown list.
3. Click on the gears icon next to the ***Text*** field and click on ***Add Expression***.

4. Select the following in the ***Variable Selector*** section: Current Node > Input Data > JSON > What did you think about the event? You can also add the following expression: `{{$json["What did you think about the event?"]}}`. If you want to analyze the sentiment for a different question, select that question instead.
5. Click on ***Execute Node*** to run the node.

In the screenshot below, you will notice that the node analyzes the sentiment of the feedback and gives a score based on that.

![Using the AWS Comprehend node to analyze the sentiment](/_images/integrations/builtin/app-nodes/awscomprehend/awscomprehend_node.png)


### 3. IF node

This node will check if the sentiment we got from the previous node is negative. If the sentiment is negative, it will return true otherwise false.

1. Click on ***Add Condition*** and select 'String'.
2. Click on the gears icon next to the ***Value 1*** field and click on ***Add Expression***.
3. Select the following in the ***Variable Selector*** section: Current Node > Input Data > JSON > Sentiment. You can also add the following expression: `{{$json["Sentiment"]}}`.
4. Enter `NEGATIVE` in the ***Value 2*** field.
5. Click on ***Execute Node*** to run the node.

In the screenshot below, you will notice that the node checks the sentiment that we received from the previous node and returns `true` if the sentiment is negative.

![Using the IF node to check if the sentiment](/_images/integrations/builtin/app-nodes/awscomprehend/if_node.png)

### 4. Mattermost node (post: message)

This node will send the feedback and the analysis score to the `feedback` channel in Mattermost. If you have a different channel, use that instead.

1. Create a Mattermost node connected to the 'true' output of the IF node.
2. You'll have to enter credentials for the Mattermost node. You can find out how to enter credentials for this node [here](/integrations/builtin/credentials/mattermost/).
3. Select a channel from the ***Channel ID*** dropdown list.
4. Click on the gears icon next to the ***Message*** field click on ***Add Expression***.

5. Enter the following message in the ***Expression*** field: `You got new feedback with a score of {{$json["SentimentScore"]["Negative"]}}. Here is what it says:{{$node["Typeform Trigger"].json["What did you think about the event?"]}}`.
6. Click on ***Execute Node*** to run the workflow.

In the screenshot below, you will notice that the node sends the feedback and the analysis score to the `feedback` channel in Mattermost.

![Using the Mattermost node to send the feedback and the analysis score](/_images/integrations/builtin/app-nodes/awscomprehend/mattermost_node.png)

### 5. NoOp node

Adding this node here is optional, as the absence of this node won't make a difference to the functioning of the workflow.

1. Create a ***NoOp*** node connected to the 'false' output of the IF node.
2. Click on ***Execute Node*** to run the node.

![Using the NoOp node](/_images/integrations/builtin/app-nodes/awscomprehend/noop_node.png)

!!! note "Activate workflow for production"
    This example workflow uses the Typeform Trigger node. You'll need to save the workflow and then click on the Activate toggle on the top right of the screen to activate the workflow. Your workflow will then be triggered when a new form is submitted.

