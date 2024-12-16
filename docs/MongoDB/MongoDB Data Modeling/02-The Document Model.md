
> [!IMPORTANT] How does Mongo store the Documents
> - While they're displayed in a JSON format, they're stored in the database in a format called BSON.
> - BSON support data types unavailable in JSON.
> - BSON supports additional data types, like Date, numbers and ObjectIds.


> [!WARNING] The `_id` field
> Every document requires an `_id` field, which acts as a primary key.
> - If an inserted document doesn't include the `_id` field, MongoDB automatically generates an ObjectId for the `_id` field.
## The [MongoDB](MongoDB/MongoDB%20Data%20Modeling/01-MongoDB.md) Data Modeling Phases
- Data that is accessed together should be stored together.

![](MongoDB/img/Pasted%20image%2020241128151012.png)

1. Workload -> What are the main pieces of data, or entities, stored? Which of those entities change over time and how?
2. Identifying and modeling the relationships that exist between those entities.
3. Applying design patterns to create a schema.
---
# Database Workload
- Encompasses all the operations a database handles at any particular moment.
- Identifying read and write operations will help us understand what data is accessed together. -> We'll be able to refer back to these findings when we decide which data should be stored together.

> [!IMPORTANT] Entities
> Things that exist in our database and are unique and independent of each other.


> [!IMPORTANT] Attributes
> The individual properties that describe an entity.

---
# Modeling Data Relationships
- Can entity A be related to more than one entity B?
- Can entity B be related to more than one entity A?

- **One-to-One Relationship**: A publisher can only have one headquarters, and  a headquarters can only belong to one publisher.
![](MongoDB/img/Pasted%20image%2020241129084313.png)

- **One-to-Many**: One book can have multiple reviews. On the other hand, a single review can only be related to one book. 
![](MongoDB/img/Pasted%20image%2020241129084513.png)

- **Many-to-Many Relationship**: A book can have multiple authors, and an author can write more than one book.
![](MongoDB/img/Pasted%20image%2020241129084611.png)



> [!IMPORTANT] Reference
> Separate documents linked using a key.
> - Most often these documents come from different collections.


> [!IMPORTANT] Embedding
> We include the child document within the parent document.


> [!WARNING] How do we decide whether to reference or embed a relationship? Guidelines
> Data that is accessed together should be stored together.
> - Simplicity -> Would keeping the pieces of information together lead to a simpler data model and code?
> - Go together -> Do the pieces of information have a "has-a", "contains", or similar relationship?
> - Query Atomicity -> Does the application query the pieces of information together?
> - Update Complexity -> Are the pieces of information updated together? 
> - Archival -> Should the pieces of information be archived at the same time?
> - Cardinality -> Is there a high cardinality(current or growing) in the child side of the relationship? 
> - Data Duplication -> Would data duplication be too complicated to manage and undesired?
> - Document Size -> Would the combined size of the pieces of information take too much memory or transfer bandwidth for the application?
> - Document Growth -> Would the embedded piece grow without bound?
> - Workload -> Are the pieces of information written at different times in a write-heavy workload?
> - Individuality -> For the child side of the relationship, can the pieces exist by themselves without a parent?


