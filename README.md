![Cool Ashley](cool-ashley.png)
# Awesome Ash [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)
A comprehensive list of awesome Ash libraries, DSLs, Resources and Examples.


## Libraries
 - [Ash](#ash---) - A declarative, resource-based framework for building Elixir applications.
 - [AshPostgres](#ashpostgres---) - A postgres data layer for Ash Framework.
 - [AshGraphql](#ashgraphql---) - The extension for building GraphQL APIs with Ash.
 - [AshJsonApi](#ashjsonapi---) - The JSON:API support for Ash Framework resources.
 - [AshAi](#ashai---) - Structured outputs, vectorization and tool calling for your Ash application.
 - [AshPhoenix](#ashphoenix---) - Utilities for using Ash with Phoenix.
 - [AshAuthentication](#ashauthentication---) - Authentication extension for the Ash Framework.
 - [AshAdmin](#ashadmin---) - A super-admin UI for Ash Framework, built with Phoenix LiveView.
 - [AshPaperTrail](#ashpapertrail---) - The extension for keeping an audit log of changes to your Ash resources.
 - [AshOban](#ashoban---) - The extension for integrating Ash resources with Oban.
 - [AshEvents](#ashevents---) - An event-architecture extension for Ash.
 - [AshStateMachine](#ashstatemachine---) - The extension for building state machines with Ash resources.
 - [AshArchival](#asharchival---) - An Ash extension to implement archival (soft deletion) for resources.
 - [AshCloak](#ashcloak---) - An Ash extension to seamlessly encrypt and decrypt resource attributes.
 - [AshSqlite](#ashsqlite---) - An SQLite data layer for Ash Framework.
 - [AshSync](#ashsync---) - Real-time sync for Postgres-backed Ash & Phoenix applications.
 - [AshDoubleEntry](#ashdoubleentry---) - A customizable double entry bookkeeping system backed by Ash resources.
 - [AshCsv](#ashcsv---) - A CSV data layer for Ash Framework.
 - [OpentelemetryAsh](#opentelemetryash---) - The Open Telemetry integration for Ash Framework.
 - [AshBlog](#ashblog---) - A Blog data layer backed by markdown files.
 - [AshMoney](#ashmoney---) - The extension for working with money types in Ash.
 - [AshAppsignal](#ashappsignal---) - The AppSignal APM integration for Ash Framework.
 - [AshOps](#ashops---) - An Ash extension which generates mix tasks for actions.

## [Ash](https://hexdocs.pm/ash/readme.html) [![git](git.png)](https://github.com/ash-project/ash) [![hex](hex.png)](https://hex.pm/packages/ash) [![elixir-observer](observer.png)](https://elixir-observer.com/packages/ash)

### DSL
#### [Ash.Resource](https://hexdocs.pm/ash/dsl-ash-resource.html)
* [attributes](https://hexdocs.pm/ash/dsl-ash-resource.html#attributes) - A section for declaring attributes on the resource.
  * [attribute](https://hexdocs.pm/ash/dsl-ash-resource.html#attributes-attribute) - Declares an attribute on the resource.
  * [create_timestamp](https://hexdocs.pm/ash/dsl-ash-resource.html#attributes-create_timestamp) - Declares a non-writable attribute with a create default of `&DateTime.utc_now/0`.
  * [update_timestamp](https://hexdocs.pm/ash/dsl-ash-resource.html#attributes-update_timestamp) - Declares a non-writable attribute with a create and update default of `&DateTime.utc_now/0`.
  * [integer_primary_key](https://hexdocs.pm/ash/dsl-ash-resource.html#attributes-integer_primary_key) - Declares a generated, non writable, non-nil, primary key column of type integer.
  * [uuid_primary_key](https://hexdocs.pm/ash/dsl-ash-resource.html#attributes-uuid_primary_key) - Declares a non writable, non-nil, primary key column of type `uuid`, which defaults to `Ash.UUID.generate/0`.
  * [uuid_v7_primary_key](https://hexdocs.pm/ash/dsl-ash-resource.html#attributes-uuid_v7_primary_key) - Declares a non writable, non-nil, primary key column of type `uuid_v7`, which defaults to `Ash.UUIDv7.generate/0`.

* [relationships](https://hexdocs.pm/ash/dsl-ash-resource.html#relationships) - A section for declaring relationships on the resource.
  * [has_one](https://hexdocs.pm/ash/dsl-ash-resource.html#relationships-has_one) - Declares a `has_one` relationship. In a relational database, the foreign key would be on the *other* table.
  * [has_many](https://hexdocs.pm/ash/dsl-ash-resource.html#relationships-has_many) - Declares a `has_many` relationship. There can be any number of related entities.
  * [many_to_many](https://hexdocs.pm/ash/dsl-ash-resource.html#relationships-many_to_many) - Declares a `many_to_many` relationship. Many to many relationships require a join resource.
  * [belongs_to](https://hexdocs.pm/ash/dsl-ash-resource.html#relationships-belongs_to) - Declares a `belongs_to` relationship. In a relational database, the foreign key would be on the *source* table.

* [actions](https://hexdocs.pm/ash/dsl-ash-resource.html#actions) - A section for declaring resource actions.
    * [action](https://hexdocs.pm/ash/dsl-ash-resource.html#actions-action) - Declares a generic action. A combination of arguments, a return type and a run function.
    * [create](https://hexdocs.pm/ash/dsl-ash-resource.html#actions-create) - Declares a `create` action. For calling this action, see the `Ash.Domain` documentation.
    * [read](https://hexdocs.pm/ash/dsl-ash-resource.html#actions-read) - Declares a `read` action. For calling this action, see the `Ash.Domain` documentation.
    * [update](https://hexdocs.pm/ash/dsl-ash-resource.html#actions-update) - Declares a `update` action. For calling this action, see the `Ash.Domain` documentation.
    * [destroy](https://hexdocs.pm/ash/dsl-ash-resource.html#actions-destroy) - Declares a `destroy` action. For calling this action, see the `Ash.Domain` documentation.

* [code_interface](https://hexdocs.pm/ash/dsl-ash-resource.html#code_interface) - Functions that will be defined on the resource.
  * [define](https://hexdocs.pm/ash/dsl-ash-resource.html#code_interface-define) - Defines a function with the corresponding name and arguments
  * [define_calculation](https://hexdocs.pm/ash/dsl-ash-resource.html#code_interface-define_calculation) - Defines a function that evaluates a calculation

* [resource](https://hexdocs.pm/ash/dsl-ash-resource.html#resource) - General resource configuration

* [identities](https://hexdocs.pm/ash/dsl-ash-resource.html#identities) - Unique identifiers for the resource
  * [identity](https://hexdocs.pm/ash/dsl-ash-resource.html#identities-identity) - Represents a unique constraint on the resource.

* [changes](https://hexdocs.pm/ash/dsl-ash-resource.html#changes) - Declare changes that occur on create/update/destroy actions
  * [change](https://hexdocs.pm/ash/dsl-ash-resource.html#changes-change) - A change to be applied to the changeset

* [preparations](https://hexdocs.pm/ash/dsl-ash-resource.html#preparations) - Declare preparations for read actions
  * [prepare](https://hexdocs.pm/ash/dsl-ash-resource.html#preparations-prepare) - Declares a preparation for queries

* [validations](https://hexdocs.pm/ash/dsl-ash-resource.html#validations) - Declare validations prior to performing actions against the resource
  * [validate](https://hexdocs.pm/ash/dsl-ash-resource.html#validations-validate) - Declares a validation for creates and updates

* [aggregates](https://hexdocs.pm/ash/dsl-ash-resource.html#aggregates) - Declare named aggregates on the resource
  * [count](https://hexdocs.pm/ash/dsl-ash-resource.html#aggregates-count) - Declares a count aggregate
  * [exists](https://hexdocs.pm/ash/dsl-ash-resource.html#aggregates-exists) - Declares an exists aggregate
  * [first](https://hexdocs.pm/ash/dsl-ash-resource.html#aggregates-first) - Gets first matching value
  * [sum](https://hexdocs.pm/ash/dsl-ash-resource.html#aggregates-sum) - Sums values
  * [list](https://hexdocs.pm/ash/dsl-ash-resource.html#aggregates-list) - Gets list of values
  * [max](https://hexdocs.pm/ash/dsl-ash-resource.html#aggregates-max) - Gets maximum value
  * [min](https://hexdocs.pm/ash/dsl-ash-resource.html#aggregates-min) - Gets minimum value
  * [avg](https://hexdocs.pm/ash/dsl-ash-resource.html#aggregates-avg) - Calculates average
  * [custom](https://hexdocs.pm/ash/dsl-ash-resource.html#aggregates-custom) - Custom aggregate implementation

* [calculations](https://hexdocs.pm/ash/dsl-ash-resource.html#calculations) - Declare named calculations
  * [calculate](https://hexdocs.pm/ash/dsl-ash-resource.html#calculations-calculate) - Declares a calculation


* [multitenancy](https://hexdocs.pm/ash/dsl-ash-resource.html#multitenancy) - Configure multitenancy behavior

#### [Ash.Domain](https://hexdocs.pm/ash/dsl-ash-domain.html)
* [domain](https://hexdocs.pm/ash/dsl-ash-domain.html#domain) - General domain configuration.
* [resources](https://hexdocs.pm/ash/dsl-ash-domain.html#resources) - List the resources of this domain.
  * [resource](https://hexdocs.pm/ash/dsl-ash-domain.html#resources-resource) - A resource present in the domain.
  * [define](https://hexdocs.pm/ash/dsl-ash-domain.html#resources-define) - Defines a function with the corresponding name and arguments.
  * [define_calculation](https://hexdocs.pm/ash/dsl-ash-domain.html#resources-define_calculation) - Defines a function with the corresponding name and arguments, that evaluates a calculation.
* [execution](https://hexdocs.pm/ash/dsl-ash-domain.html#execution) - Options for how requests are executed using this domain.
* [authorization](https://hexdocs.pm/ash/dsl-ash-domain.html#authorization) - Options for how requests are authorized using this domain.

### Resources
* [Get Started](https://hexdocs.pm/ash/get-started.html)
* [From Simple to Sophisticated](https://hexdocs.pm/ash/what-is-ash.html#an-example-from-simple-to-sophisticated)

## [AshPostgres](https://hexdocs.pm/ash_postgres/readme.html) [![git](git.png)](https://github.com/ash-project/ash_postgres) [![hex](hex.png)](https://hex.pm/packages/ash_postgres) [![elixir-observer](observer.png)](https://elixir-observer.com/packages/ash_postgres)

### DSL
#### [AshPostgres.DataLayer](https://hexdocs.pm/ash_postgres/dsl-ashpostgres-datalayer.html)
* [postgres](https://hexdocs.pm/ash/dsl-ash-resource.html#postgres) - Postgres data layer configuration.
  * [custom_indexes](https://hexdocs.pm/ash_postgres/dsl-ashpostgres-datalayer.html#postgres-custom_indexes) - A section for configuring indexes to be created by the migration generator.
  * [custom_statements](https://hexdocs.pm/ash_postgres/dsl-ashpostgres-datalayer.html#postgres-custom_statements) - A section for configuring custom statements to be added to migrations.
  * [manage_tenant](https://hexdocs.pm/ash_postgres/dsl-ashpostgres-datalayer.html#postgres-manage_tenant) - Configuration for the behavior of a resource that manages a tenant.
  * [references](https://hexdocs.pm/ash_postgres/dsl-ashpostgres-datalayer.html#postgres-references) - A section for configuring the references (foreign keys) in resource migrations.
  * [check_constraints](https://hexdocs.pm/ash_postgres/dsl-ashpostgres-datalayer.html#postgres-check_constraints) - A section for configuring the check constraints for a given table.

### Resources
* [Get Started With Postgres](https://hexdocs.pm/ash_postgres/get-started-with-ash-postgres.html)
* [Setting AshPostgres up with an existing database](https://hexdocs.pm/ash_postgres/set-up-with-existing-database.html)


## [AshGraphql](https://hexdocs.pm/ash_graphql/readme.html) [![git](git.png)](https://github.com/ash-project/ash_graphql) [![hex](hex.png)](https://hex.pm/packages/ash_graphql) [![elixir-observer](observer.png)](https://elixir-observer.com/packages/ash_graphql)

### DSL
#### [AshGraphql.Domain](https://hexdocs.pm/ash_graphql/dsl-ashgraphql-domain.html)
* [graphql](https://hexdocs.pm/ash_graphql/dsl-ashgraphql-domain.html#graphql) - Domain level configuration for GraphQL.
  * [queries](https://hexdocs.pm/ash_graphql/dsl-ashgraphql-domain.html#graphql-queries) - Queries to expose for the resource.
  * [mutations](https://hexdocs.pm/ash_graphql/dsl-ashgraphql-domain.html#graphql-mutations) - Mutations (create/update/destroy actions) to expose for the resource.
  * [subscriptions](https://hexdocs.pm/ash_graphql/dsl-ashgraphql-domain.html#graphql-subscriptions) - Subscriptions to expose for the resource.

#### [AshGraphql.Resource](https://hexdocs.pm/ash_graphql/dsl-ashgraphql-resource.html)
* [graphql](https://hexdocs.pm/ash_graphql/dsl-ashgraphql-resource.html#graphql) - Configuration for a given resource in graphql.
  * [queries](https://hexdocs.pm/ash_graphql/dsl-ashgraphql-resource.html#graphql-queries) - Queries (read actions) to expose for the resource.
  * [mutations](https://hexdocs.pm/ash_graphql/dsl-ashgraphql-resource.html#graphql-mutations) - Mutations (create/update/destroy actions) to expose for the resource.
  * [subscriptions](https://hexdocs.pm/ash_graphql/dsl-ashgraphql-resource.html#graphql-subscriptions) - Subscriptions (notifications) to expose for the resource.
  * [managed_relationships](https://hexdocs.pm/ash_graphql/dsl-ashgraphql-resource.html#graphql-managed_relationships) - Generates input objects for `manage_relationship` arguments on resource actions.

### Resources
* [Getting Started With GraphQL](https://hexdocs.pm/ash_graphql/getting-started-with-graphql.html)

## [AshJsonApi](https://hexdocs.pm/ash_json_api/readme.html) [![git](git.png)](https://github.com/ash-project/ash_json_api) [![hex](hex.png)](https://hex.pm/packages/ash_json_api) [![elixir-observer](observer.png)](https://elixir-observer.com/packages/ash_json_api)

### DSL

### Resources


## [AshAi](https://hexdocs.pm/ash_ai/readme.html) [![git](git.png)](https://github.com/ash-project/ash_ai) [![hex](hex.png)](https://hex.pm/packages/ash_ai) [![elixir-observer](observer.png)](https://elixir-observer.com/packages/ash_ai)

### DSL

### Resources


## [AshPhoenix](https://hexdocs.pm/ash_phoenix/readme.html) [![git](git.png)](https://github.com/ash-project/ash_phoenix) [![hex](hex.png)](https://hex.pm/packages/ash_phoenix) [![elixir-observer](observer.png)](https://elixir-observer.com/packages/ash_phoenix)

### DSL

### Resources


## [AshAuthentication](https://hexdocs.pm/ash_authentication/readme.html) [![git](git.png)](https://github.com/ash-project/ash_authentication) [![hex](hex.png)](https://hex.pm/packages/ash_authentication) [![elixir-observer](observer.png)](https://elixir-observer.com/packages/ash_authentication)

### DSL

### Resources


## [AshAdmin](https://hexdocs.pm/ash_admin/readme.html) [![git](git.png)](https://github.com/ash-project/ash_admin) [![hex](hex.png)](https://hex.pm/packages/ash_admin) [![elixir-observer](observer.png)](https://elixir-observer.com/packages/ash_admin)

### DSL

### Resources


## [AshPaperTrail](https://hexdocs.pm/ash_paper_trail/readme.html) [![git](git.png)](https://github.com/ash-project/ash_paper_trail) [![hex](hex.png)](https://hex.pm/packages/ash_paper_trail) [![elixir-observer](observer.png)](https://elixir-observer.com/packages/ash_paper_trail)

### DSL

### Resources


## [AshOban](https://hexdocs.pm/ash_oban/readme.html) [![git](git.png)](https://github.com/ash-project/ash_oban) [![hex](hex.png)](https://hex.pm/packages/ash_oban) [![elixir-observer](observer.png)](https://elixir-observer.com/packages/ash_oban)

### DSL

### Resources
* [Sending Emails with Ash Framework](https://www.zachdaniel.dev/p/sending-emails-with-ash)


## [AshEvents](https://hexdocs.pm/ash_events/readme.html) [![git](git.png)](https://github.com/ash-project/ash_events) [![hex](hex.png)](https://hex.pm/packages/ash_events) [![elixir-observer](observer.png)](https://elixir-observer.com/packages/ash_events)

### DSL

### Resources


## [AshStateMachine](https://hexdocs.pm/ash_state_machine/readme.html) [![git](git.png)](https://github.com/ash-project/ash_state_machine) [![hex](hex.png)](https://hex.pm/packages/ash_state_machine) [![elixir-observer](observer.png)](https://elixir-observer.com/packages/ash_state_machine)

### DSL

### Resources


## [AshArchival](https://hexdocs.pm/ash_archival/readme.html) [![git](git.png)](https://github.com/ash-project/ash_archival) [![hex](hex.png)](https://hex.pm/packages/ash_archival) [![elixir-observer](observer.png)](https://elixir-observer.com/packages/ash_archival)

### DSL

### Resources


## [AshCloak](https://hexdocs.pm/ash_cloak/readme.html) [![git](git.png)](https://github.com/ash-project/ash_cloak) [![hex](hex.png)](https://hex.pm/packages/ash_cloak) [![elixir-observer](observer.png)](https://elixir-observer.com/packages/ash_cloak)

### DSL

### Resources


## [AshSqlite](https://hexdocs.pm/ash_sqlite/readme.html) [![git](git.png)](https://github.com/ash-project/ash_sqlite) [![hex](hex.png)](https://hex.pm/packages/ash_sqlite) [![elixir-observer](observer.png)](https://elixir-observer.com/packages/ash_sqlite)

### DSL

### Resources


## [AshSync](https://hexdocs.pm/ash_sync/readme.html) [![git](git.png)](https://github.com/ash-project/ash_sync) [![hex](hex.png)](https://hex.pm/packages/ash_sync)

### DSL

### Resources


## [AshDoubleEntry](https://hexdocs.pm/ash_double_entry/readme.html) [![git](git.png)](https://github.com/ash-project/ash_double_entry) [![hex](hex.png)](https://hex.pm/packages/ash_double_entry) [![elixir-observer](observer.png)](https://elixir-observer.com/packages/ash_double_entry)

### DSL

### Resources


## [AshCsv](https://hexdocs.pm/ash_csv/readme.html) [![git](git.png)](https://github.com/ash-project/ash_csv) [![hex](hex.png)](https://hex.pm/packages/ash_csv) [![elixir-observer](observer.png)](https://elixir-observer.com/packages/ash_csv)

### DSL

### Resources


## [OpentelemetryAsh](https://hexdocs.pm/opentelemetry_ash/readme.html) [![git](git.png)](https://github.com/ash-project/opentelemetry_ash) [![hex](hex.png)](https://hex.pm/packages/opentelemetry_ash) [![elixir-observer](observer.png)](https://elixir-observer.com/packages/opentelemetry_ash)

### DSL

### Resources


## [AshBlog](https://hexdocs.pm/ash_blog/readme.html) [![git](git.png)](https://github.com/ash-project/ash_blog) [![hex](hex.png)](https://hex.pm/packages/ash_blog)

### DSL

### Resources


## [AshMoney](https://hexdocs.pm/ash_money/readme.html) [![git](git.png)](https://github.com/ash-project/ash_money) [![hex](hex.png)](https://hex.pm/packages/ash_money) [![elixir-observer](observer.png)](https://elixir-observer.com/packages/ash_money)

### DSL

### Resources


## [AshAppsignal](https://hexdocs.pm/ash_appsignal/readme.html) [![git](git.png)](https://github.com/ash-project/ash_appsignal) [![hex](hex.png)](https://hex.pm/packages/ash_appsignal) [![elixir-observer](observer.png)](https://elixir-observer.com/packages/ash_appsignal)

### DSL

### Resources


## [AshOps](https://hexdocs.pm/ash_ops/readme.html) [![git](git.png)](https://github.com/ash-project/ash_ops) [![hex](hex.png)](https://hex.pm/packages/ash_ops) [![elixir-observer](observer.png)](https://elixir-observer.com/packages/ash_ops)

### DSL

### Resources

