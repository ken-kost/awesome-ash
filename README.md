# Awesome Ash [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A list of awesome Ash libraries, DSLs and Resources.

The Elixir backend framework for unparalleled productivity. Declarative tools that let you stop wasting time. Use with Phoenix LiveView or build APIs in minutes for your front-end of choice.

![Cool_Ashley_logo](cool-ashley.png)

## Contents
- [Ash](#ash) - A declarative, resource-based framework for building Elixir applications.
- [AshPostgres](#ashpostgres) - A postgres data layer for Ash Framework.
- [AshGraphql](#ashgraphql) - The extension for building GraphQL APIs with Ash.
- [AshJsonApi](#ashjsonapi) - The JSON:API support for Ash Framework resources.
- [AshAi](#ashai) - Structured outputs, vectorization and tool calling for your Ash application.
- [AshPhoenix](#ashphoenix) - Utilities for using Ash with Phoenix.
- [AshAuthentication](#ashauthentication) - Authentication extension for the Ash Framework.
- [Reactor](#reactor) - An asynchronous, graph-based execution engine.
- [AshAdmin](#ashadmin) - A super-admin UI for Ash Framework, built with Phoenix LiveView.
- [AshPaperTrail](#ashpapertrail) - The extension for keeping an audit log of changes to your Ash resources.
- [AshOban](#ashoban) - The extension for integrating Ash resources with Oban.
- [AshEvents](#ashevents) - An event-architecture extension for Ash.
- [AshStateMachine](#ashstatemachine) - The extension for building state machines with Ash resources.
- [AshArchival](#asharchival) - An Ash extension to implement archival (soft deletion) for resources.
- [AshCloak](#ashcloak) - An Ash extension to seamlessly encrypt and decrypt resource attributes.
- [AshSqlite](#ashsqlite) - An SQLite data layer for Ash Framework.
- [AshSync](#ashsync) - Real-time sync for Postgres-backed Ash & Phoenix applications.
- [AshDoubleEntry](#ashdoubleentry) - A customizable double entry bookkeeping system backed by Ash resources.
- [AshCsv](#ashcsv) - A CSV data layer for Ash Framework.
- [OpentelemetryAsh](#opentelemetryash) - The Open Telemetry integration for Ash Framework.
- [AshBlog](#ashblog) - A Blog data layer backed by markdown files.
- [AshMoney](#ashmoney) - The extension for working with money types in Ash.
- [AshAppsignal](#ashappsignal) - The AppSignal APM integration for Ash Framework.
- [AshOps](#ashops) - An Ash extension which generates mix tasks for actions.
- [AshGeo](#ashgeo) - Tools for using Geo, Topo and PostGIS with Ash.

---

## [Ash](https://hexdocs.pm/ash/readme.html) 

[![git-hub](git.svg)](https://github.com/ash-project/ash) [![hex](hex.svg)](https://hex.pm/packages/ash) [![elixir-observer](eob.svg)](https://elixir-observer.com/packages/ash)

### DSL

#### [Domain](https://hexdocs.pm/ash/dsl-ash-domain.html)
- domain - General domain configuration.

- resources - List the resources of this domain.
   - resource - A resource present in the domain.
   - define - Defines a function with the corresponding name and arguments.
  - define_calculation - Defines a function with the corresponding name and arguments, that evaluates a calculation.

- execution - Options for how requests are executed using this domain.

- authorization - Options for how requests are authorized using this domain.

#### [Resource](https://hexdocs.pm/ash/dsl-ash-resource.html)

- attributes - A section for declaring attributes on the resource.
  - attribute - Declares an attribute on the resource.
  - create_timestamp - Declares a non-writable attribute with a create default of `&DateTime.utc_now/0`.
  - update_timestamp - Declares a non-writable attribute with a create and update default of `&DateTime.utc_now/0`.
  - integer_primary_key - Declares a generated, non writable, non-nil, primary key column of type integer.
  - uuid_primary_key - Declares a non writable, non-nil, primary key column of type `uuid`, which defaults to `Ash.UUID.generate/0`.
  - uuid_v7_primary_key - Declares a non writable, non-nil, primary key column of type `uuid_v7`, which defaults to `Ash.UUIDv7.generate/0`.
- relationships - A section for declaring relationships on the resource.
  - has_one - Declares a `has_one` relationship. In a relational database, the foreign key would be on the *other* table.
  - has_many - Declares a `has_many` relationship. There can be any number of related entities.
  - many_to_many - Declares a `many_to_many` relationship. Many to many relationships require a join resource.
  - belongs_to - Declares a `belongs_to` relationship. In a relational database, the foreign key would be on the *source* table.

- actions - A section for declaring resource actions.
    - action - Declares a generic action. A combination of arguments, a return type and a run function.
    - create - Declares a `create` action. For calling this action, see the `Ash.Domain` documentation.
    - read - Declares a `read` action. For calling this action, see the `Ash.Domain` documentation.
    - update - Declares a `update` action. For calling this action, see the `Ash.Domain` documentation.
    - destroy - Declares a `destroy` action. For calling this action, see the `Ash.Domain` documentation.

- code_interface - Functions that will be defined on the resource.
  - define - Defines a function with the corresponding name and arguments.
  - define_calculation - Defines a function that evaluates a calculation.

- resource - General resource configuration.

- identities - Unique identifiers for the resource.
  - identity - Represents a unique constraint on the resource.

- changes - Declare changes that occur on create/update/destroy actions
  - change - A change to be applied to the changeset.

- preparations - Declare preparations for read actions.
  - prepare - Declares a preparation for queries.

- validations - Declare validations prior to performing actions against the resource.
  - validate - Declares a validation for creates and updates.

- aggregates - Declare named aggregates on the resource.
  - count - Declares a count aggregate.
  - exists - Declares an exists aggregate.
  - first - Gets first matching value.
  - sum - Sums values.
  - list - Gets list of values.
  - max - Gets maximum value.
  - min - Gets minimum value.
  - avg - Calculates average.
  - custom - Custom aggregate implementation.

- calculations - Declare named calculations.
  - calculate - Declares a calculation.

- multitenancy - Configure multitenancy behavior.

### Resources

- [Get Started](https://hexdocs.pm/ash/get-started.html)

- [From Simple to Sophisticated](https://hexdocs.pm/ash/what-is-ash.html#an-example-from-simple-to-sophisticated)

## [AshPostgres](https://hexdocs.pm/ash_postgres/readme.html) 
[![git-hub](git.svg)](https://github.com/ash-project/ash_postgres) [![hex](hex.svg)](https://hex.pm/packages/ash_postgres) [![elixir-observer](eob.svg)](https://elixir-observer.com/packages/ash_postgres)

### DSL

#### [DataLayer](https://hexdocs.pm/ash_postgres/dsl-ashpostgres-datalayer.html)

- postgres - Postgres data layer configuration.
  - custom_indexes - A section for configuring indexes to be created by the migration generator.
  - custom_statements - A section for configuring custom statements to be added to migrations.
  - manage_tenant - Configuration for the behavior of a resource that manages a tenant.
  - references - A section for configuring the references (foreign keys) in resource migrations.
  - check_constraints - A section for configuring the check constraints for a given table.

### Resources

- [Get Started](https://hexdocs.pm/ash_postgres/get-started-with-ash-postgres.html)

- [Setting AshPostgres up with an existing database](https://hexdocs.pm/ash_postgres/set-up-with-existing-database.html)

---

## [AshGraphql](https://hexdocs.pm/ash_graphql/readme.html) 
[![git-hub](git.svg)](https://github.com/ash-project/ash_graphql) [![hex](hex.svg)](https://hex.pm/packages/ash_graphql) [![elixir-observer](eob.svg)](https://elixir-observer.com/packages/ash_graphql)

### DSL

#### [Domain](https://hexdocs.pm/ash_graphql/dsl-ashgraphql-domain.html)

- graphql - Domain level configuration for GraphQL.
  - queries - Queries to expose for the resource.
  - mutations - Mutations (create/update/destroy actions) to expose for the resource.
  - subscriptions - Subscriptions to expose for the resource.

#### [Resource](https://hexdocs.pm/ash_graphql/dsl-ashgraphql-resource.html)

- graphql - Configuration for a given resource in graphql.
  - queries - Queries (read actions) to expose for the resource.
  - mutations - Mutations (create/update/destroy actions) to expose for the resource.
  - subscriptions - Subscriptions (notifications) to expose for the resource.
  - managed_relationships - Generates input objects for `manage_relationship` arguments on resource actions.

### Resources

- [Get Started](https://hexdocs.pm/ash_graphql/getting-started-with-graphql.html)

---

## [AshJsonApi](https://hexdocs.pm/ash_json_api/readme.html) 
[![git-hub](git.svg)](https://github.com/ash-project/ash_json_api) [![hex](hex.svg)](https://hex.pm/packages/ash_json_api) [![elixir-observer](eob.svg)](https://elixir-observer.com/packages/ash_json_api)

### DSL

#### [AshJsonApi.Domain](https://hexdocs.pm/ash_json_api/dsl-ashjsonapi-domain.html)

- json_api - Global configuration for JSON:API.
  - open_api - OpenAPI configurations.
  - routes - Route configurations for JSON:API endpoints.

#### [AshJsonApi.Resource](https://hexdocs.pm/ash_json_api/dsl-ashjsonapi-resource.html)

### Resources

- [Get Started](https://hexdocs.pm/ash_json_api/getting-started-with-ash-json-api.html)

## [AshAi](https://hexdocs.pm/ash_ai/readme.html) 
[![git-hub](git.svg)](https://github.com/ash-project/ash_ai) [![hex](hex.svg)](https://hex.pm/packages/ash_ai) [![elixir-observer](eob.svg)](https://elixir-observer.com/packages/ash_ai)

### DSL

### Resources

---

## [AshPhoenix](https://hexdocs.pm/ash_phoenix/readme.html) 
[![git-hub](git.svg)](https://github.com/ash-project/ash_phoenix) [![hex](hex.svg)](https://hex.pm/packages/ash_phoenix) [![elixir-observer](eob.svg)](https://elixir-observer.com/packages/ash_phoenix)

### DSL

### Resources

---

## [AshAuthentication](https://hexdocs.pm/ash_authentication/readme.html) 
[![git-hub](git.svg)](https://github.com/ash-project/ash_authentication) [![hex](hex.svg)](https://hex.pm/packages/ash_authentication) [![elixir-observer](eob.svg)](https://elixir-observer.com/packages/ash_authentication)

### DSL

### Resources

---

## [Reactor](https://hexdocs.pm/reactor/readme.html) 
[![git-hub](git.svg)](https://github.com/ash-project/reactor) [![hex](hex.svg)](https://hex.pm/packages/reactor) [![elixir-observer](eob.svg)](https://elixir-observer.com/packages/reactor)

### DSL

### Resources

---

## [AshAdmin](https://hexdocs.pm/ash_admin/readme.html) 
[![git-hub](git.svg)](https://github.com/ash-project/ash_admin) [![hex](hex.svg)](https://hex.pm/packages/ash_admin) [![elixir-observer](eob.svg)](https://elixir-observer.com/packages/ash_admin)

### DSL

### Resources

---

## [AshPaperTrail](https://hexdocs.pm/ash_paper_trail/readme.html) 
[![git-hub](git.svg)](https://github.com/ash-project/ash_paper_trail) [![hex](hex.svg)](https://hex.pm/packages/ash_paper_trail) [![elixir-observer](eob.svg)](https://elixir-observer.com/packages/ash_paper_trail)

### DSL

### Resources

---

## [AshOban](https://hexdocs.pm/ash_oban/readme.html) 
[![git-hub](git.svg)](https://github.com/ash-project/ash_oban) [![hex](hex.svg)](https://hex.pm/packages/ash_oban) [![elixir-observer](eob.svg)](https://elixir-observer.com/packages/ash_oban)

### DSL

### Resources
- [Sending Emails with Ash Framework](https://www.zachdaniel.dev/p/sending-emails-with-ash)

---

## [AshEvents](https://hexdocs.pm/ash_events/readme.html) 
[![git-hub](git.svg)](https://github.com/ash-project/ash_events) [![hex](hex.svg)](https://hex.pm/packages/ash_events) [![elixir-observer](eob.svg)](https://elixir-observer.com/packages/ash_events)

### DSL

### Resources

---

## [AshStateMachine](https://hexdocs.pm/ash_state_machine/readme.html) 
[![git-hub](git.svg)](https://github.com/ash-project/ash_state_machine) [![hex](hex.svg)](https://hex.pm/packages/ash_state_machine) [![elixir-observer](eob.svg)](https://elixir-observer.com/packages/ash_state_machine)

### DSL

### Resources

---

## [AshArchival](https://hexdocs.pm/ash_archival/readme.html) 
[![git-hub](git.svg)](https://github.com/ash-project/ash_archival) [![hex](hex.svg)](https://hex.pm/packages/ash_archival) [![elixir-observer](eob.svg)](https://elixir-observer.com/packages/ash_archival)

### DSL

### Resources

---

## [AshCloak](https://hexdocs.pm/ash_cloak/readme.html) 
[![git-hub](git.svg)](https://github.com/ash-project/ash_cloak) [![hex](hex.svg)](https://hex.pm/packages/ash_cloak) [![elixir-observer](eob.svg)](https://elixir-observer.com/packages/ash_cloak)

### DSL

### Resources

---

## [AshSqlite](https://hexdocs.pm/ash_sqlite/readme.html) 
[![git-hub](git.svg)](https://github.com/ash-project/ash_sqlite) [![hex](hex.svg)](https://hex.pm/packages/ash_sqlite) [![elixir-observer](eob.svg)](https://elixir-observer.com/packages/ash_sqlite)

### DSL

### Resources

---

## [AshSync](https://hexdocs.pm/ash_sync/readme.html) 
[![git-hub](git.svg)](https://github.com/ash-project/ash_sync) [![hex](hex.svg)](https://hex.pm/packages/ash_sync)

### DSL

### Resources

---

## [AshDoubleEntry](https://hexdocs.pm/ash_double_entry/readme.html) 
[![git-hub](git.svg)](https://github.com/ash-project/ash_double_entry) [![hex](hex.svg)](https://hex.pm/packages/ash_double_entry) [![elixir-observer](eob.svg)](https://elixir-observer.com/packages/ash_double_entry)

### DSL

### Resources

---

## [AshCsv](https://hexdocs.pm/ash_csv/readme.html)
[![git](git.svg)](https://github.com/ash-project/ash_csv) [![hex](hex.svg)](https://hex.pm/packages/ash_csv) [![elixir-observer](eob.svg)](https://elixir-observer.com/packages/ash_csv)

### DSL

### Resources

---

## [OpentelemetryAsh](https://hexdocs.pm/opentelemetry_ash/readme.html)
[![git](git.svg)](https://github.com/ash-project/opentelemetry_ash) [![hex](hex.svg)](https://hex.pm/packages/opentelemetry_ash) [![elixir-observer](eob.svg)](https://elixir-observer.com/packages/opentelemetry_ash)

### DSL

### Resources

---

## [AshBlog](https://hexdocs.pm/ash_blog/readme.html)
[![git-hub](git.svg)](https://github.com/ash-project/ash_blog) [![hex](hex.svg)](https://hex.pm/packages/ash_blog)

### DSL

### Resources

---

## [AshMoney](https://hexdocs.pm/ash_money/readme.html)
[![git-hub](git.svg)](https://github.com/ash-project/ash_money) [![hex](hex.svg)](https://hex.pm/packages/ash_money) [![elixir-observer](eob.svg)](https://elixir-observer.com/packages/ash_money)

### DSL

### Resources

---

## [AshAppsignal](https://hexdocs.pm/ash_appsignal/readme.html)
[![git-hub](git.svg)](https://github.com/ash-project/ash_appsignal) [![hex](hex.svg)](https://hex.pm/packages/ash_appsignal) [![elixir-observer](eob.svg)](https://elixir-observer.com/packages/ash_appsignal)

### DSL

### Resources

---

## [AshOps](https://hexdocs.pm/ash_ops/readme.html)
[![git-hub](git.svg)](https://github.com/ash-project/ash_ops) [![hex](hex.svg)](https://hex.pm/packages/ash_ops) [![elixir-observer](eob.svg)](https://elixir-observer.com/packages/ash_ops)

### DSL

### Resources

---

## [AshGeo](https://hexdocs.pm/ash_geo/readme.html)
[![git-hub](git.svg)](https://github.com/bcksl/ash_geo) [![hex](hex.svg)](https://hex.pm/packages/ash_geo) [![elixir-observer](eob.svg)](https://elixir-observer.com/packages/ash_geo)

### DSL

### Resources

---

## Contributing

Please refer to the guidelines at [contributing.md](https://github.com/ken-kost/awesome-ash#contributing.md) for details.
