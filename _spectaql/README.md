## Update API Reference Docs

Instructions for updating the GraphQL API reference docs at [https://docs.forta.network/en/latest/forta-api-reference](https://docs.forta.network/en/latest/forta-api-reference/#introduction)

### Prerequisites

Install [SpectaQL](https://github.com/anvilco/spectaql)
```bash
$ npm install -g spectaql
```

### Instructions

1. Generate docs and see results at `http://localhost:4400`
  ```bash
  $ cd _spectaql && npx spectaql config.yml -D
  ```
2. Copy generated docs to the [Forta docs repo](https://github.com/forta-network/docs) and make a PR to update the reference docs at https://docs.forta.network/en/latest/api/ .
  ```bash
  $ cp -r _spectaql/public/* ~/workspace/docs/docs/forta-api-reference/
  ```
