# Forta API Example Queries, Tutorials, and Issue Tracker

![forta_detection](https://user-images.githubusercontent.com/3497137/188163437-70d0ae07-ce0c-4840-aad8-08612bcaf211.gif)


This repository contains tutorials and example queries to try in the [Forta API Sandbox](https://studio.apollographql.com/sandbox?document=query%20exampleQuery%20%7B%0A%20%23%20first%205%20alerts%0A%20alerts%20%7B%0A%20%20%20%20pageInfo%20%7B%0A%20%20%20%20%20%20hasNextPage%0A%20%20%20%20%20%20endCursor%20%7B%0A%20%20%20%20%20%20%20%20alertId%0A%20%20%20%20%20%20%20%20blockNumber%0A%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%0A%20%20%20%20alerts%20%7B%0A%20%20%20%20%20%20createdAt%0A%20%20%20%20%20%20name%0A%20%20%20%20%20%20protocol%0A%20%20%20%20%20%20findingType%0A%20%20%20%20%20%20source%20%7B%0A%20%20%20%20%20%20%20%20transactionHash%0A%20%20%20%20%20%20%20%20block%20%7B%0A%20%20%20%20%20%20%20%20%20%20number%0A%20%20%20%20%20%20%20%20%20%20chainId%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20bot%20%7B%0A%20%20%20%20%20%20%20%20%20%20id%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20severity%0A%20%20%20%20%20%20metadata%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D&endpoint=https%3A%2F%2Fapi.forta.network%2Fgraphql). It also tracks Forta API's feature requests, bug reports, and feedback.

To learn more about Forta, please visit [forta.org](https://forta.org/).

For more details on this API, please check out the developer documentation at [docs.forta.network](https://docs.forta.network/en/latest/api/)

## Explore Example Queries
Explore the following queries in the [Forta API Sandbox](https://studio.apollographql.com/sandbox?document=query%20exampleQuery%20%7B%0A%20%23%20first%205%20alerts%0A%20alerts%20%7B%0A%20%20%20%20pageInfo%20%7B%0A%20%20%20%20%20%20hasNextPage%0A%20%20%20%20%20%20endCursor%20%7B%0A%20%20%20%20%20%20%20%20alertId%0A%20%20%20%20%20%20%20%20blockNumber%0A%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%0A%20%20%20%20alerts%20%7B%0A%20%20%20%20%20%20createdAt%0A%20%20%20%20%20%20name%0A%20%20%20%20%20%20protocol%0A%20%20%20%20%20%20findingType%0A%20%20%20%20%20%20source%20%7B%0A%20%20%20%20%20%20%20%20transactionHash%0A%20%20%20%20%20%20%20%20block%20%7B%0A%20%20%20%20%20%20%20%20%20%20number%0A%20%20%20%20%20%20%20%20%20%20chainId%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20bot%20%7B%0A%20%20%20%20%20%20%20%20%20%20id%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20severity%0A%20%20%20%20%20%20metadata%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D&endpoint=https%3A%2F%2Fapi.forta.network%2Fgraphql).

* [Query recent alerts emitted by a specific detection bot](example_queries/recent_alerts.md)
* [Query today's alerts associated with certain addressees](example_queries/todays_alerts.md)
* [Query past alerts by block number or date range](example_queries/past_alerts.md)
* [Query a list of blockchain projects](example_queries/blockchain_projects_list.md)
* [Query details of a blockchain project](example_queries/blockchain_project.md)

## Explore Tutorials

* [Query alerts for analysis with python](tutorials/analysis_in_python.md)
* [Calculate bot stats with python](https://github.com/forta-network/starter-kits/blob/main/anomalous-token-transfers-ml-py/daily_model_stats.ipynb)

## Contribute

* [🐛 Report a bug.](https://github.com/forta-network/forta-api/issues/new?assignees=&labels=bug&template=bug-report.md&title=%5BBUG%5D+)
* [🚀 Request a feature.](https://github.com/forta-network/forta-api/issues/new?assignees=&labels=enhancement&template=feature-request.md&title=%5BFEATURE%5D)
* [🤔 Search on Discourse for similar questions or ask for help there.](https://gov.forta.network/c/start-here/faqs/11)
* [💬 Ask questions on Discord or let us know if you're interested in making code contributions!](https://discord.gg/38eg5EP3F9)

