---
title: Attributes
permalink: /docs/attributes/
---

An Attribute is basically data you want to store for later use.
If you are system engineer you may think of an Attribute as a column in a Database Table.

<img src="/img/attribute.png" width="350">


It contains:

- Name
- Type
- Specifics 


The different types that currently exists are:

- Boolean
- Text
- Timestamp
- Decimal
- Biginteger
- Integer
- UUID
- Relation
- Set
- List
- Map


#### Validations
The text type has a two extra fields *min* and *max*. With these fields you can add validations of text length. Furthermore, the collection types Set, List and Map has a *max* field for validating the max size of objects allowed to store in these collections.

#### Partition key

The Partition Key is an advanced feature responsible for data distribution across nodes in the OOPSIE infrastructure. For every resource OOPSIE calculates how many entities it can store per partition. This means that if you know that your data will grow infinite then you *MUST* add a partition key so your data can be spread out on several paritions an be able to handle more entities. The amount of entities that can be stored is:
```
the resource max entities value * the amount of resource partitions
```
So defining a partition key can be extremly useful for data that grows infinite. The OOPSIE Site API will throw an error when max entities is reached for a partition. Below we list some things to think of when using partition keys:

- If your data will grow infinite add a partition key to your resoruce.
- If you define a partition key then it has to be included in the query everytime you want to retrieve data.

An example that stores persons ...

- city
- lastName
- firstName

... and city is used as a Partition Key.

Your data will be partitioned by city and you will not be able to have several million persons (entities) that live in same city.

The entities 

```json
[
    { 
        "city": "Växjö",
        "firstName": "Samuel",
        "lastName": "Jackson"
    }, {
        "city": "Växjö",
        "firstName": "Samuel",
        "lastName": "Andersson"
    }
]
```
will be stored in the same partition while the entities

```json
[
    { 
        "city": "Los Angeles",
        "firstName": "Samuel",
        "lastName": "Jackson"
    }, {
        "city": "Växjö",
        "firstName": "Samuel",
        "lastName": "Andersson"
    }
]
```

will **NOT** be stored in the same partition.


#### Clustering key
------

The Clustering Key is responsible for data sorting within the partition. I.e. when fetching data it will be returned according to the clustering key attributes in the resource. In queries it is possible to "filter" data using clustering keys, just like partition keys, but clustering keys are optional in queries. But if they are present then they have to be in order as declared in the queried resource. An example:

If the person resource mentioned in the partition key section above had lastName as clustering key 1 and firstName as clustering key 2 then it is not possible to query with firstName and omit lastName, but lastName can be queried and omit firstName. To accomplish a query by firstName only then you need to create a [view](/docs/views) of the resource.

Clustering Key can be sorted by:

- ASC - Ascending order
- DESC - Descending order

