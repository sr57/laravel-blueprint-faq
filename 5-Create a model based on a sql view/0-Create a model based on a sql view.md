In standard Blueprint create models, controllers, seeders and associated components (https://blueprint.laravelshift.com/docs/generating-components/)

Sql view is a way to combine several tables (or views) and do select queries on it like we do on table, so a datatable view can be based on a sql view. 

To create sql views we have to use another component and for that we choose the keyword "sqls"

To analyse the config, draft.yaml file, we have to create a SqlLexer and to create the codes a SqlGenerator, and always to register them in the service provider.

A exemple of these steps is given below.

[1-draft.yaml]()

[2-Service Providor]()

[3-SqlLexer]()

[4-SqlGenerator]()


