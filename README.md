## fhirbase in Paris

### What is fhirbase?

Relational storage for FHIR resources in PostgreSQL.

Fhirbase implements essential part of FHIR standard directly in postgres.

Fhirbase could be installed in a minutes on top of standard postgresql
with version more than 9.4.
Fhirbase also could be installed on hosted postgres like Amazon RDS and Heroku.

### Why we've started fhirbase?

Our team is mostly polyglot programmers - clojure, ruby, js, sometimes java, c# etc
So the idea was to move most of FHIR implementation inside database for reuse.

Also we know that data is a heart of many applications and postgresql is a perfect
tool to deal with data:

* reuse on diff platforms
* performance, data & logic locality

### Who is an audience of fhirbase?

Fhirbase is designed for development of new applications based on FHIR.

It handles essential part of FHIR standard implementation details and
allows you focus on implementation of buisness features using platform of your choice,
which only has to have a connectors to postgresql.

We alse expect, that for some complicated cases FHIR abstraction layer could be skipped
and you could use SQL directly for analytic, ad-hock queries or batch updates and migrations.

So from some point of view fhirbase is just ordinary (smart) postgresql database.

### Why postgresql?

Postgresql is most advanced opensource database:

* pure open source
* good experience with postgresql in production for a decade
* jsonb - binary json format
* advanced indexing with GIST & GIN (Generalized Search Tree & Generalized Inverted Index)
* extensibility (extensions, different procedural languages etc)

Postgres is a operating system for the data :)

### What parts of FHIR has already been implemented?

 * CRUD
 * history
 * transactions (partially)
 * search

### How fhirbase structured?

* Fhirbase consists of API facade implemented as a set of procedures.
* Reloadable code modules, which make API works
* Schema migrations (which allows update existing instance of fhirbase)
* tables to store resources

### How fhirbase stores resources?

fhirbase stores each resoure type in dedicated tables.
One for actual versions and another for historical versions.

For example Patient resource will be saved in
**patient** & **patient_history** tables

Most of tables have similar structure:

 * logical_id
 * version_id
 * resource_type
 * resource content (as a binary json datatype)

For search we inherites all resource tables from resource table.
Yeh postgresql support table inheretance :)
When we make query against **resource** table, it searches thro all resource types.

### What is fhirbase API?

Fhirbase API is aligned with FHIR REST interactions:

* CRUD
* history
* transaction
* search

### How fhirbase use metadata?

Initial installation of fhirbase consists of several tables for meta-resources.

* struturedefinition
* searchparameters
* valuesets, namesystems and conceptmaps

### How fhirbase implements search?

* build dynamic query

### How fhirbase makes search fast?

### Performance

### Usage

* fhirplace
* netrika laboratory buss

### What is fhirbase roadmap?

* migrate to PLV8

* incorporate terminology
* referencial consistency
* validate structure definition and value sets
* Connectors: .NET, HAPI, clj, js, ruby etc
