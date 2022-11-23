# OpenWeatherMap

[OpenWeatherMap](https://openweathermap.org/) is an online service that provides weather data. It provides current weather data, forecasts, and historical data.

!!! note "Credentials"
    You can find authentication information for this node [here](/integrations/builtin/credentials/openWeatherMap/).


## Basic Operations

* Returns the current weather data
* Returns the weather data for the next 5 days

## Example Usage

This workflow allows you to get the current weather data for a city. You can also find the [workflow](https://n8n.io/workflows/460) on the website. This example usage workflow would use the following two nodes.
- [Start](/integrations/builtin/core-nodes/n8n-nodes-base.start/)
- [OpenWeatherMap]()

The final workflow should look like the following image.

![A workflow with the OpenWeatherMap node](/_images/integrations/builtin/app-nodes/openweathermap/workflow.png)

### 1. Start node

The start node exists by default when you create a new workflow.

### 2. OpenWeatherMap node

1. First of all, you'll have to enter credentials for the OpenWeatherMap node. You can find out how to do that [here](/integrations/builtin/credentials/openWeatherMap/).
2. Enter the name of the city in the *City* field.
3. Click on *Execute Node* to run the workflow.





