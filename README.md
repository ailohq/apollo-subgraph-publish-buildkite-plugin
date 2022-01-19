# Apollo subgraph publish Buildkite Plugin

Introspects a schema running on a certain url and publishes it to Apollo

## Example

Add the following to your `pipeline.yml`:

```yml
steps:
  - command: echo 'Update federated schema'
    plugins:
      - ailohq/apollo-subgraph-publish#v1.1.0:
          schemas:
            - name: admin
              url: https://authz.dev.ailo.io/admin/graphql
            - name: agency
              url: https://authz.dev.ailo.io/agency/graphql
            - name: consumer
              url: https://authz.dev.ailo.io/consumer/graphql
          graph_name: financial-report
          environment: dev
```

## Configuration

### `graph_name` (Required, string)

Name of the current subgraph

### `environment` (Required, string)

Current environment (read, variant in apollo terms) of the federated graph

### `schemas` (Required, array of objects)

Each item in this array represents a single schema to be published.
    - `name` - schema name 
    - `url` - url to introspect to obtain the schema


## Developing

To lint the `plugin.yml` file:

```sh
docker-compose run --rm lint
```

To run the tests:

```shell
docker-compose run --rm  tests
```

## Releasing

Bump the version in README example and publish it as a git tag.
