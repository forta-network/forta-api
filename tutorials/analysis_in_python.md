# Query Alerts for Analysis with Python

With the following code, you can query alerts emitted between specified start and end date and convert the data into a pandas dataframe.
You can also tweak the number of alerts you'd like to analyze with the `ALERT_COUNT_LIMIT` parameter.
For more details on the available data fields, please checkout the [GraphQL Reference Doc](https://docs.forta.network/en/latest/forta-api-reference/)

```python
import pandas as pd
import requests

forta_api = "https://api.forta.network/graphql"
headers = {"content-type": "application/json"}

# start and end date needs to be in the format: YYYY-MM-DD
START_DATE = "2022-04-20"
END_DATE = "2022-04-21"
ALERT_COUNT_LIMIT = 100000

query = """
query exampleQuery($input: AlertsInput) {
  alerts(input: $input) {
    alerts {
      name
      protocol
      findingType
      source {
        transactionHash
        block {
          number
          chainId
          timestamp
          hash
        }
        bot {
          id
        }
      }
      severity
      metadata
      alertId
      addresses
      description
      hash
    }
    pageInfo {
      hasNextPage
      endCursor {
        blockNumber
        alertId
      }
    }
  }
}
"""

query_variables = {
  "input": {
    "first": 100,
    "blockDateRange": {
      "startDate": START_DATE,
      "endDate": END_DATE
    }
  }
}

all_alerts = []
next_page_exists = True

while next_page_exists and len(all_alerts) < ALERT_COUNT_LIMIT:
    # query Forta API
    payload = dict(query=query, variables=query_variables)
    response = requests.request("POST", forta_api, json=payload, headers=headers)

    # collect alerts
    data = response.json()['data']['alerts']
    alerts = data['alerts']
    all_alerts += alerts

    # get next page of alerts if it exists
    next_page_exists = data['pageInfo']['hasNextPage']
    # endCursor contains alert Id and block number.
    # This is needed to get the next page of alerts.
    end_cursor = data['pageInfo']['endCursor']
    query_variables['input']['after'] = end_cursor

df = pd.DataFrame.from_dict(all_alerts)

len(df) # size: ALERT_COUNT_LIMIT = 100000
```
