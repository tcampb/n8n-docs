# Processing different data types

In this chapter, you will learn how to process different types of data using [n8n core nodes](/workflows/nodes/).


## HTML and XML data

You're most likely familiar with HTML and XML.

!!! note "HTML vs. XML"

    HTML is a markup language used to describe the structure and semantics of a web page. XML looks similar to HTML, but the tag names are different, as they describe the kind of data they hold.

If you need to process HTML or XML data in your n8n workflows, use the [HTML Extract node](/integrations/builtin/core-nodes/n8n-nodes-base.htmlextract/) or [XML node](/integrations/builtin/core-nodes/n8n-nodes-base.xml/).

The HTML Extract node allows you to extract HTML content of a webpage, by referencing CSS selectors. This is useful if you want to collect structured information from a website (web-scraping).

### Exercise

Use the HTTP Request node to make a GET request to the URL `https://www.daysoftheyear.com/days/mar/2022/`. Then, connect an HTML Extract node and configure it to extract the date of the returned events.

??? note "Show me the solution"

	Configure the HTTP Request node with the following parameters:

	- Authentication: None
	- Request Method: GET
	- URL: https://www.daysoftheyear.com/days/mar/2022/

	The result should look like this:

	<figure><img src="/_images/courses/level-two/chapter-two/exercise_html_httpRequestNode.png" alt="" style="width:100%"><figcaption align = "center"><i>Result of HTTP Request node</i></figcaption></figure>

	Connect an *HTML Extract node* to the HTTP Request node and configure the former's parameters:

	- Source Data: JSON
	- JSON Property: data
	- Extraction Values:
		- Key: event
		- CSS Selector: .js-link-target
		- Return Value: HTML

		You can add more values to extract more data.

	The result should look like this:

	<figure><img src="/_images/courses/level-two/chapter-two/exercise_html_htmlExtractNode.png" alt="" style="width:100%"><figcaption align = "center"><i>Result of HTML Extract node</i></figcaption></figure>
	</details>


The XML node allows you to convert XML to JSON and JSON to XML. This operation is useful if you work with different web services that use either XML or JSON, and need to get and submit data between them in the two formats.

### Exercise

In a previous exercise, you used an HTTP Request node to make a request to an API. Now, use the XML node to convert the JSON output to XML.

??? note "Show me the solution"

	Get data from the Poemist API using the HTTP Request node and connect an XML node to it with the following parameters:

	- Mode: **JSON to XML**
	- Property name: **data**

	The result should look like this:

	<figure><img src="/_images/courses/level-two/chapter-two/exercise_html_xmlNode_json.png" alt="" style="width:100%"><figcaption align = "center"><i>XML node (JSON to XML) – JSON View</i></figcaption></figure>

	<figure><img src="/_images/courses/level-two/chapter-two/exercise_html_xmlNode_table.png" alt="" style="width:100%"><figcaption align = "center"><i>XML node (JSON to XML) – Table View</i></figcaption></figure>

	To transform data the other way around, select the mode **XML to JSON**.


## Date, time, and interval data

Date and time data types include `DATE`, `TIME`, `DATETIME`, `TIMESTAMP`, and `YEAR`. The dates and times can be passed in different formats, for example:

- `DATE`: March 29 2022, 29-03-2022, 2022/03/29
- `TIME`: 08:30:00, 8:30, 20:30
- `DATETIME`: 2022/03/29 08:30:00
- `TIMESTAMP`: 1616108400 (Unix timestamp), 1616108400000 (Unix ms timestamp)
- `YEAR`: 2022, 22

If you need to convert date and time data to different formats, and calculate dates, use the [Date & Time node](/integrations/builtin/core-nodes/n8n-nodes-base.datetime/).

You can also schedule workflows to run at a specific time, interval, or duration, using the two trigger nodes:

- [Schedule Trigger](/integrations/builtin/core-nodes/n8n-nodes-base.scheduletrigger/) triggers the workflow at fixed dates and/or times (for example, every Monday at 9am).
- [Interval node](/integrations/builtin/core-nodes/n8n-nodes-base.interval/)} triggers the workflow in regular intervals of time (for example, every 10 minutes).

In some cases, you might need to pause the workflow execution. This might be necessary, for example, if you know that a service doesn't process the data instantly or it is generally slower, so you don't want the incomplete data to be passed to the next node. In this case, you can use the [Wait node](/integrations/builtin/core-nodes/n8n-nodes-base.wait/) after the node that you want to delay. The Wait node pauses the workflow execution and resumes it at a specific time, after a time interval, or on a webhook call.


### Exercise

Build a workflow that adds five days to an input date. Then, if the calculated date occurred after today, the workflow waits 1 minute before [setting](/integrations/builtin/core-nodes/n8n-nodes-base.set/) the calculated date as a value. The workflow should be triggered every 30 minutes.

??? note "Show me the solution"

	You can build this workflow using the data from the *Customer Datastore node*, the three nodes for managing date and time, an *IF node* for conditional routing, and a *Set node* for setting the new calculated date. The workflow looks like this:

	<figure><img src="/_images/courses/level-two/chapter-two/exercise_dateTime.png" alt="" style="width:100%"><figcaption align = "center"><i>Workflow for transforming dates</i></figcaption></figure>

	To check the configuration of each node, you can copy the JSON code of this workflow and paste it in your Editor UI.

	```json
	{
		"nodes": [
			{
				"parameters": {
					"action": "calculate",
					"value": "={{$json[\"created\"]}}",
					"duration": 5,
					"options": {}
				},
				"name": "Date & Time",
				"type": "n8n-nodes-base.dateTime",
				"typeVersion": 1,
				"position": [
					880,
					1500
				]
			},
			{
				"parameters": {
					"unit": "hours"
				},
				"name": "Interval",
				"type": "n8n-nodes-base.interval",
				"typeVersion": 1,
				"position": [
					520,
					1500
				]
			},
			{
				"parameters": {
					"unit": "minutes"
				},
				"name": "Wait",
				"type": "n8n-nodes-base.wait",
				"typeVersion": 1,
				"position": [
					1240,
					1500
				],
				"webhookId": "d17effb8-ad90-4a74-bb88-daa3d3d18583"
			},
			{
				"parameters": {
					"conditions": {
						"dateTime": [
							{
								"value1": "={{$json[\"data\"]}}",
								"value2": "2022-02-03T11:45:38.932Z"
							}
						]
					}
				},
				"name": "IF",
				"type": "n8n-nodes-base.if",
				"typeVersion": 1,
				"position": [
					1060,
					1500
				]
			},
			{
				"parameters": {
					"values": {
						"string": [
							{
								"value": "={{$node[\"IF\"].json[\"data\"]}}"
							}
						]
					},
					"options": {}
				},
				"name": "Set",
				"type": "n8n-nodes-base.set",
				"typeVersion": 1,
				"position": [
					1420,
					1500
				]
			},
			{
				"parameters": {
					"operation": "getAllPeople",
					"returnAll": true
				},
				"name": "Customer Datastore",
				"type": "n8n-nodes-base.n8nTrainingCustomerDatastore",
				"typeVersion": 1,
				"position": [
					700,
					1500
				]
			}
		],
		"connections": {
			"Date & Time": {
				"main": [
					[
						{
							"node": "IF",
							"type": "main",
							"index": 0
						}
					]
				]
			},
			"Interval": {
				"main": [
					[
						{
							"node": "Customer Datastore",
							"type": "main",
							"index": 0
						}
					]
				]
			},
			"Wait": {
				"main": [
					[
						{
							"node": "Set",
							"type": "main",
							"index": 0
						}
					]
				]
			},
			"IF": {
				"main": [
					[
						{
							"node": "Wait",
							"type": "main",
							"index": 0
						}
					]
				]
			},
			"Customer Datastore": {
				"main": [
					[
						{
							"node": "Date & Time",
							"type": "main",
							"index": 0
						}
					]
				]
			}
		}
	}
	```


## Binary data

So far, you have mainly worked with text data. But what if you want to process data that is not text? For example, images or PDF files. This is binary data, as it is represented in the binary numeral system. In this form, binary data doesn't offer you useful information, so it needs to be converted into a readable form.

In n8n, you can process binary data with the following nodes:

- [Move Binary Data node](/integrations/builtin/core-nodes/n8n-nodes-base.movebinarydata/) to move data between binary and JSON properties.
- [Read Binary File node](/integrations/builtin/core-nodes/n8n-nodes-base.readbinaryfile/) to read a file from the host machine that runs n8n.
- [Read Binary Files](/integrations/builtin/core-nodes/n8n-nodes-base.readbinaryfiles/) to read multiple files from the host machine that runs n8n.
- [Write Binary File](/integrations/builtin/core-nodes/n8n-nodes-base.writebinaryfile/) to write a file to the host machine that runs n8n.
- [Spreadsheet File node](/integrations/builtin/core-nodes/n8n-nodes-base.spreadsheetfile/) to read from or write to spreadsheet files of different formats (for example, CSV, XLSX).

To read or write a binary file, you need to write the path (location) of the file in the node's `File Name` parameter.

!!! warning "Naming the right path"

	The file path looks slightly different on n8n cloud compared to desktop or self-hosted:

	- n8n desktop and self-hosted: `./Documents/my_file.json`
	- n8n cloud: `/home/node/.n8n/my_file.json`


### Exercise

Make an HTTP request to get this PDF file: `https://media.kaspersky.com/pdf/Kaspersky_Lab_Whitepaper_Anti_blocker.pdf.` Then, use the Move Binary Data node to convert the file from binary to JSON, with [base64](https://developer.mozilla.org/en-US/docs/Glossary/Base64){:target="_blank" .external-link} encoding.

??? note "Show me the solution"

	In the HTTP Request node, you should see the PDF file in JSON, Table, and Binary view, like this:

	<figure><img src="/_images/courses/level-two/chapter-two/exercise_binaryData_httpRequest_file.png" alt="" style="width:100%"><figcaption align = "center"><i>HTTP Request node to get PDF</i></figcaption></figure>

	When you convert the PDF from binary to JSON with base64 encoding using the *Move Binary Data node*, the result should look like this:

	<figure><img src="/_images/courses/level-two/chapter-two/exercise_binaryData_moveData_btoj.png" alt="" style="width:100%"><figcaption align = "center"><i>Move Binary Data node (Binary to JSON) with base64 encoding</i></figcaption></figure>

	To check the configuration of the nodes, you can copy-paste the JSON code of the workflow:

	```json
	{
		"nodes": [
			{
				"parameters": {
					"url": "https://media.kaspersky.com/pdf/Kaspersky_Lab_Whitepaper_Anti_blocker.pdf",
					"responseFormat": "file",
					"options": {}
				},
				"name": "HTTP Request",
				"type": "n8n-nodes-base.httpRequest",
				"typeVersion": 1,
				"position": [
					1340,
					1080
				]
			},
			{
				"parameters": {
					"setAllData": false,
					"options": {
						"encoding": "base64"
					}
				},
				"name": "Move Binary Data",
				"type": "n8n-nodes-base.moveBinaryData",
				"typeVersion": 1,
				"position": [
					1600,
					1080
				]
			}
		],
		"connections": {
			"HTTP Request": {
				"main": [
					[
						{
							"node": "Move Binary Data",
							"type": "main",
							"index": 0
						}
					]
				]
			}
		}
	}
	```



### Exercise

Make an HTTP request to the Poemist API `https://www.poemist.com/api/v1/randompoems` and move the returned data from JSON to binary. Then, write the new binary data to a file. Finally, to check that it worked out, read the generated binary file referencing it with an expression in the node.

??? note "Show me the solution"

	The workflow for this exercise looks like this:

	<figure><img src="/_images/courses/level-two/chapter-two/exercise_binaryData.png" alt="" style="width:100%"><figcaption align = "center"><i>Workflow for moving JSON to binary data</i></figcaption></figure>

	To check the configuration of the nodes, you can copy-paste the JSON code of the workflow:

	```json
	{
		"nodes": [
			{
				"parameters": {
					"filePath": "={{$json[\"fileName\"]}}"
				},
				"name": "Read Binary File",
				"type": "n8n-nodes-base.readBinaryFile",
				"typeVersion": 1,
				"position": [
					1060,
					500
				]
			},
			{
				"parameters": {
					"url": "https://www.poemist.com/api/v1/randompoems",
					"options": {
						"splitIntoItems": true
					}
				},
				"name": "HTTP Request",
				"type": "n8n-nodes-base.httpRequest",
				"typeVersion": 1,
				"position": [
					520,
					500
				]
			},
			{
				"parameters": {
					"fileName": "/home/node/.n8n/poemist.json"
				},
				"name": "Write Binary File",
				"type": "n8n-nodes-base.writeBinaryFile",
				"position": [
					880,
					500
				],
				"typeVersion": 1
			},
			{
				"parameters": {
					"mode": "jsonToBinary",
					"options": {}
				},
				"name": "Move Binary Data",
				"type": "n8n-nodes-base.moveBinaryData",
				"position": [
					700,
					500
				],
				"typeVersion": 1
			}
		],
		"connections": {
			"HTTP Request": {
				"main": [
					[
						{
							"node": "Move Binary Data",
							"type": "main",
							"index": 0
						}
					]
				]
			},
			"Write Binary File": {
				"main": [
					[
						{
							"node": "Read Binary File",
							"type": "main",
							"index": 0
						}
					]
				]
			},
			"Move Binary Data": {
				"main": [
					[
						{
							"node": "Write Binary File",
							"type": "main",
							"index": 0
						}
					]
				]
			}
		}
	}
	```
