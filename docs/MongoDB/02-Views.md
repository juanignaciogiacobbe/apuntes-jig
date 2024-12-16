
> [!IMPORTANT] Creating Views
> `db.createCollection()`
> `db.createView()`


> [!WARNING] View Names are included in collection list output
> Operations that list collections, such as `db.getCollectionInfos()` and `db.getCollectionNames()`, include views in their outputs.
> Avoid referring directly to sensitive fields and values in view definitions.

## `db.createCollection()`
```
db.createCollection(
  "<viewName>",
  {
    "viewOn" : "<source>",
    "pipeline" : [<pipeline>],
    "collation" : { <collation> }
  }
)
```
## `db.createView()`
```
db.createView(
  "<viewName>",
  "<source>",
  [<pipeline>],
  {
    "collation" : { <collation> }
  }
)
```


> [!WARNING] Restrictions
> - You must create views in the same database as the source collection.
> - A view definition `pipeline` cannot include the `$out` of the `$merge` stage. -> This restriction also applies to embedded pipelines, such as pipelines used in `$lookup` or `$facet` stages.
> - You cannot rename a view once its created.
