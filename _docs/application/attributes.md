---
title: Attributes
permalink: /docs/attributes/
---

An Attribute is basically data you want to store for later use.
If you are technical you may think of an Attribute as a column in a Database Table.


![Attribute](/img/attribute.png "Attribute")


It contains:

- Name
- Type
- Specifics 


The different types that currently exists are:

- boolean
- time
- date
- timestamp
- decimal
- big integer
- integer
- uuid
- timeuuid
- relation
- set
- list
- map
- tuple



#### Partition key
------

The Partition Key is responsible for data distribution across your nodes. This is nothing you have to worry about. One thing to keep in mind is that it might speed up your results if you have a well thought partition key.

> **NOTE:** If you have a Partition Key it has to be included everytime you want to retrieve data. Use it if you are sure you will always get your data by a specific Attribute.

> **NOTE:** If you are not an advanced user it might be easier to just skip setting a Partition key.

If you specify one of these it is good to think about how many of the same you will have. It will be slower if you reach a specific limit of a specific partition key.
The dashboard will warn you if you will be able to have less then 300k entities per Partition.

For eg. if you have a Resource with the Attributes:

- firstname
- lastname
- civicNo

and firstname is used as a Partition Key.

Your data will be partitioned by firstname and you will not be able to have 1 billion entities that has the same firstname.

The entities 

```json
[
    { 
        "firstname": "Samuel",
        "lastname": "Jacksson"
    }, {
        "firstname": "Samuel",
        "lastname": "Andersson"
    }
]
```
will be stored in the same partition while the entities

```json
[
    { 
        "firstname": "Sam",
        "lastname": "Jacksson"
    }, {
        "firstname": "Samuel",
        "lastname": "Andersson"
    }
]
```

will **NOT** be stored in the same partition.


#### Clustering key
------

The Clustering Key is responsible for data sorting within the partition. It is possible to use the Attribute that is a Clustering Key when you are quering your data.

Clustering Key can be sorted by:

- ASC - Ascending order
- DESC - Descending order

