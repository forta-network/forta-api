# Query recent alerts emitted by a specific detection bot

## What information can I get?

This query will return specified detection bots' alerts that were created since 10 minutes ago. This query can be useful if you'd like to take immediate action such as the following after receiving the alerts:

Some example use cases:
* As a dApp owner, warn or notify my users of potential threats and governance changes in the dApp.
* As a developer, automate mitigation steps after receiving a combination of alerts from 2 or more detection bots.

## How to execute this query?

Step 1: Go to [Forta API Sandbox](https://studio.apollographql.com/sandbox?document=query%20exampleQuery%20%7B%0A%20%23%20first%205%20alerts%0A%20alerts%20%7B%0A%20%20%20%20pageInfo%20%7B%0A%20%20%20%20%20%20hasNextPage%0A%20%20%20%20%20%20endCursor%20%7B%0A%20%20%20%20%20%20%20%20alertId%0A%20%20%20%20%20%20%20%20blockNumber%0A%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%0A%20%20%20%20alerts%20%7B%0A%20%20%20%20%20%20createdAt%0A%20%20%20%20%20%20name%0A%20%20%20%20%20%20protocol%0A%20%20%20%20%20%20findingType%0A%20%20%20%20%20%20source%20%7B%0A%20%20%20%20%20%20%20%20transactionHash%0A%20%20%20%20%20%20%20%20block%20%7B%0A%20%20%20%20%20%20%20%20%20%20number%0A%20%20%20%20%20%20%20%20%20%20chainId%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20bot%20%7B%0A%20%20%20%20%20%20%20%20%20%20id%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20severity%0A%20%20%20%20%20%20metadata%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D&endpoint=https%3A%2F%2Fapi.forta.network%2Fgraphql). Make sure the endpoint is set to `https://api.forta.network/graphql` in the top left corner before proceeding to the next steps.
<p align="left">
  <img src="screenshots/sandbox_endpoint.png" alt="Sandbox Endpoint Screenshot" width="300"/>
</p>

Step 2: Create a new workspace.
<p align="left">
  <img src="screenshots/new_workspace.png" alt="New Workspace Screenshot" width="300"/>
</p>

Step 3: Paste the following query in the `Operation` panel. For more details on the available alert fields, please checkout the [AlertsResponse Schema](https://studio.apollographql.com/sandbox/schema/reference/objects/AlertsResponse).

```graphql
query recentAlerts($input: AlertsInput) {
  alerts(input: $input) {
    pageInfo {
      hasNextPage
      endCursor {
        alertId
        blockNumber
      }
    }
    alerts {
      createdAt
      name
      protocol
      findingType
      source {
        transactionHash
        block {
          number
          chainId
        }
        bot {
          id
        }
      }
      severity
      metadata
      scanNodeCount
    }
  }
}
```

<p align="left">
  <img src="screenshots/operation_panel.png" alt="Operation Panel Screenshot" width="500"/>
</p>

Step 4: Replace the placeholders in the following query parameters and paste them in the `Variable` panel. For more details on the available query parameters, please checkout the [AlertsInput Schema](https://studio.apollographql.com/sandbox/schema/reference/inputs/AlertsInput)
```json
{
  "input": {
    "first": 5,
    "bots": [<BOT_ID_A>, <BOT_ID_B>],
    "createdSince": 600000,
    "chainId": 1
  }
}
```

<p align="left">
  <img src="screenshots/variable_panel.png" alt="Variable Panel Screenshot" width="500"/>
</p>

Step 5: Click on the blue submit button on the `Operation` panel to execute the query.

The button will look like the following:

> NOTE: The button text will be different depending on the query name.

<p align="left">
  <img src="screenshots/query_submit_button.png" alt="Query Submit Button Screenshot" width="500"/>
</p>

And that's it! You should be able to see the query results in the `Response` panel on the right.

## The results are paginated, how do I get the next page?

If the output returns `"hasNextPage": true`, add the `after` query parameter in the `input` object to get the next page of alerts and execute the query.

```javascript
{
  "input": {
    ...
    "after": {
      "blockNumber": "<END_CURSOR_BLOCK_NUMBER>",
      "alertId": "<END_CURSOR_ALERT_ID>"
    }
  }
}
```

## Additional Filters

### Filter alerts by number of scan node confirmations

The following input filter will return alerts with `scanNodeCount` ranging from 2 to 10 (inclusive).
You don't need to define both `gte` and `lte` at the same time.

```javascript
{
  "input": {
    ...
    // scanNodeCount is the number of scan nodes that found the alert
    "scanNodeConfirmations": {
      "gte": 2,
      "lte": 10
    }
  }
}
```

If you're only interested in alerts with a `scanNodeCount` of 3, make sure the `gte` and `lte` value matches.

```javascript
{
  "input": {
    ...
    "scanNodeConfirmations": {
      "gte": 3,
      "lte": 3
    }
  }
}
```

