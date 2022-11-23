# JotForm Trigger

[JotForm](https://www.jotform.com/) is an online form building service. JotForm's software creates forms with a drag and drop creation tool and an option to encrypt user data.

!!! note "Credentials"
    You can find authentication information for this node [here](/integrations/builtin/credentials/jotForm/).



## Example Usage

This workflow allows you to receive updates for form events in JotForm. You can also find the [workflow](https://n8n.io/workflows/541) on the website. This example usage workflow would use the following node.

- [JotForm Trigger]()

The final workflow should look like the following image.

![A workflow with the JotForm Trigger node](/_images/integrations/builtin/trigger-nodes/jotformtrigger/workflow.png)


### 1. JotForm Trigger node

1. First of all, you'll have to enter credentials for the JotForm Trigger node. You can find out how to do that [here](/integrations/builtin/credentials/jotForm/).
2. Select the form you want to receive updates for from the *Form* dropdown list.
3. Click on *Execute Node* to run the workflow.

!!! note "Activate workflow for production"
    You'll need to save the workflow and then click on the Activate toggle on the top right of the screen to activate the workflow. Your workflow will then be triggered as specified by the settings in the JotForm Trigger node.

