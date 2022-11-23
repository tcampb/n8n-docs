# Data pinning

n8n allows you to 'pin' data during workflow development. Data pinning means saving the output data of a node, and using the saved data instead of fetching fresh data in future workflow executions. 


You can use this when working with data from external sources, to avoid having to repeatedly use the external system. This can save time and resources:

* If your workflow relies on an external system to trigger it, such as a webhook call, being able to pin data means you don't need to use the external system every time you test the workflow.
* If the external resource has data or usage limits, pinning data during tests avoids consuming your resource limits.
* You can fetch and pin the data you want to test, then have confidence that the data is consistent in all your workflow tests.

!!! note "For development only"
    Data pinning isn't available for production workflow executions. It's a feature to help test workflows during development.


## Pin data

To pin data in a node:

1. Run the node to load data.
2. In the **OUTPUT** view, select **Pin data** <span class="inline-image">![Pin data icon](/_images/data/data-pinning/data-pinning-button.png)</span>. When data pinning is active, the button changes to show this <span class="inline-image">![Active pin data icon](/_images/data/data-pinning/data-pinning-button-active.png)</span>.

!!! note "Nodes that output binary data"
    You can't pin data if the output data includes binary data.


## Unpin data

When data pinning is active, the button changes to show this <span class="inline-image">![Active pin data icon](/_images/data/data-pinning/data-pinning-button-active.png)</span>. To unpin data and fetch fresh data on the next execution, select the active **Pin data** <span class="inline-image">![Active pin data icon](/_images/data/data-pinning/data-pinning-button-active.png)</span> icon.



