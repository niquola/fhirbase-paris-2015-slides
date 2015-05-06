## fhirbase in Paris

* What is fhirbase?

Relational storage of FHIR resources in PostgreSQL.
Fhirbase implements essential part of FHIR standard directly in postgres.

Fhirbase could be installed in a minutes on top of standard postgresql with version more than 9.4.
Also fhirbase could be hosted in Amazon RDS and on Heroku Postgres.

* Who are fhirbase user?

Fhirbase is good choice for development brand new applications based on FHIR.

Fhirbase handles essential part of FHIR standard implementation details and
allows you focus on implementation of buisness features using any platform of your choice,
which has connectors to postgresql.

* Why we've started fhirbase?

Our team is mostly polygloth programmers - clojure, ruby, js, sometimes java, c# etc
So the idea was to move most of FHIR implementation inside database for reuse.

Leaking abstractions...

* Why postgresql?

Postgresql is most advanced opensource database:

 * pure open source
 * good expirience with postgresql in production for a decade
 * jsonb - binary json format
 * advanced indexing with GIST & GIN
 * plenty of procedural languages sql, plpgsql, plv8 (js), plpython


* What parts of FHIR has already been implemented?

 * CRUD
 * transactions
 * versioning
 * search

* What is fhirbase API?

Fhirbase API is aligned with FHIR rest interactions:

 * CRUD
 * history
 * transaction

* How fhirbase structured?

* How fhirbase stores resources?

 fhirbase store each resoure in dedicated tables - on for current version and another for historical:
 for example Patient resource will be saved in patient & patient_history tables

 All tables has similar structure:

 * logical_id
 * version_id
 * resource content

* How fhirbase use metadata?

 Initial installation of fhirbase consists of several tables for meta-resources.

 * struturedefinition
 * searchparameters
 * valuesets, namesystems and concept_maps

* How fhirbase implements versioning?
* How fhirbase implements search?

  * build dynamic query

* How fhirbase makes search fast?

* Problem - advanced search
* Problem - acidentally complicated search API
* Problem - not full & not consistent meta-information
* Problem - updates of base resources

* Ideas - advanced search
* Ideas - distribute metadata in tabular format
* Ideas - transaction temporal ids
* Ideas - create/update
* Ideas - a lot of http stuff in core api

* How to start with fhirbase?

* Where i could get fhirbase?

* How fhirbase could be updated?
  * migrations

* How to use fhirbase in production?

* What is fhirbase roadmap?

 * incorporate terminology
 * referencial consistency
 * validate structure definition and value sets
 * migrate to PLV8

* Commertial production package for fhirbase

* Connectors
  * .NET
  * .HAPI
  * clj, js, ruby etc
