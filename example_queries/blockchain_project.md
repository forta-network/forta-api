# Query details of a blockchain project

## What information will I get?

This query will return details of a specific blockchain project. The original data source is at [ethereums-lists/contracts github repository](https://github.com/ethereum-lists/contracts#projects-entries).

## How to execute this query?

Step 1: Go to [Forta API Sandbox](https://studio.apollographql.com/sandbox?endpoint=https%3A%2F%2Fapi.forta.network%2Fgraphql). Make sure the endpoint is set to `https://api.forta.network/graphql` in the top left corner before proceeding to the next steps.
<p align="left">
  <img src="screenshots/sandbox_endpoint.png" alt="Sandbox Endpoint Screenshot" width="300"/>
</p>

Step 2: Create a new workspace.
<p align="left">
  <img src="screenshots/new_workspace.png" alt="New Workspace Screenshot" width="300"/>
</p>

Step 3: Paste the following query in the `Operation` panel. For more details on the available project fields, please checkout the [Project Schema](https://studio.apollographql.com/sandbox/schema/reference/objects/Project).

```graphql
query Project($projectId: String!) {
  project(id: $projectId) {
    name
    id
    token {
      address
      chainId
    }
  }
}
```

<p align="left">
  <img src="screenshots/operation_panel.png" alt="Operation Panel Screenshot" width="500"/>
</p>

Step 4: Replace the placeholders in the following query parameters and paste them in the `Variable` panel.
```json
{
  "projectId": "<BLOCK_CHAIN_PROJECT_ID>"
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
