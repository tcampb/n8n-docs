# Microsoft SQL

[Microsoft SQL](https://www.microsoft.com/en-us/sql-server) is a relational database management system. As a database server, it is a software product with the primary function of storing and retrieving data as requested by other software applications—which may run either on the same computer or on another computer across a network.

!!! note "Credentials"
    You can find authentication information for this node [here](/integrations/builtin/credentials/microsoftSql/).


## Basic Operations

* Execute an SQL query
* Insert rows in database
* Update rows in database
* Delete rows in database


## Example Usage

This workflow allows you to execute an SQL query in Microsoft SQL. You can also find the [workflow](https://n8n.io/workflows/479) on the website. This example usage workflow would use the following two nodes.
- [Start](/integrations/builtin/core-nodes/n8n-nodes-base.start/)
- [Microsoft SQL]()

The final workflow should look like the following image.

![A workflow with the Microsoft SQL node](/_images/integrations/builtin/app-nodes/microsoftsql/workflow.png)

### 1. Start node

The start node exists by default when you create a new workflow.

### 2. Microsoft SQL node

1. First of all, you'll have to enter credentials for the Microsoft SQL node. You can find out how to do that [here](/integrations/builtin/credentials/microsoftSql/).
2. Select 'Execute Query' from the *Operation* dropdown list.
3. Enter your SQL query in the *Query* field.
4. Click on *Execute Node* to run the workflow.
