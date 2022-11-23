# GitLab

[GitLab](https://gitlab.com/) is a web-based DevOps lifecycle tool that provides a Git-repository manager providing wiki, issue-tracking, and continuous integration/continuous installation pipeline features.

!!! note "Credentials"
    You can find authentication information for this node [here](/integrations/builtin/credentials/gitlab/).


## Basic Operations

* Issue
    * Create a new issue
    * Create a new comment on an issue
    * Edit an issue
    * Get the data of a single issue
    * Lock an issue
* Repository
    * Get the data of a single repository
    * Returns issues of a repository
* Release
    * Create a new release
    * Delete a new release
    * Get a new release
    * Get all releases
    * Update a new release
* User
    * Returns the repositories of a user

## Example Usage

This workflow allows you to get the details of a GitLab repository. You can also find the [workflow](https://n8n.io/workflows/465) on the website. This example usage workflow uses the following two nodes.
- [Start](/integrations/builtin/core-nodes/n8n-nodes-base.start/)
- [GitLab]()

The final workflow should look like the following image.

![A workflow with the GitLab node](/_images/integrations/builtin/app-nodes/gitlab/workflow.png)

### 1. Start node

The start node exists by default when you create a new workflow.

### 2. GitLab node

1. First of all, you'll have to enter credentials for the GitLab node. You can find out how to do that [here](/integrations/builtin/credentials/gitlab/).
2. Select the 'Repository' option from the *Resource* dropdown list.
3. Select the 'Get' option under the *Operation* field.
4. Enter the project owner in the *Project Owner* field.
5. Enter the project name in the *Project Name* field.
6. Click on *Execute Node* to run the workflow.
