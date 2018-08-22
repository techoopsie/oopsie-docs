---
title: Views
permalink: /docs/views/
---

### Overview

Views give you the possibility to retrieve your data in a different way than the default one. By default a resource gets a default primary view "byId" and is used as the default view when fetching data. But you can of course create your own views or alter the default "byId" view. If your apps or systems need to fetch data in different manners or filter on specific attributes then you create several views to support this filtering.

In distributed environments this is a very important concept. Since your resource data is spread across several machines and partitions OOPSIE makes your data redundant so it can be efficiently returned when you ask for it. This means that OOPSIE can handle enormous amount of data but still very fast return it to the apps when needed.

In the [Resource](/docs/resources) panel locate the view button and click on it to enter View details. Here you create or alter the views depending on how you want to retrieve the data.

> *Remember!*
> A partition can't grow too big so add primary keys if needed. See the "Advanced" section in the [Resource](/docs/resources) overview.

### Example

If you have a Resource with name *Persons* and it has three Attributes, *firstName*, *lastName* and *civicNo* (also has id by default). You want to, by default, retrieve *Persons* entities by *lastName* in ascending order and secondly by *firstName* in ascending order, then create a new view, or change the default, so it has lastName as the first clustering key and firstName as the second clustering key using ascending order on both. But you also have another page where the user will search for persons using its civicNo instead, here a second view comes handy. If you create a view that is called for eg. *byCivicNo* and add your Attribute *civicNo* you will be able to retrieve your data easily using this view filtered by a persons *civic no*.

#### Advanced
You might wonder why you can't just filter on civicNo when fetching the *Persons* entities, why the need of an extra view? Since OOPSIE distributes its data to several nodes in a distributed server infrastructure it would be very insufficiant to ask all nodes in OOPSIE if it stores a *Persons* entity with a civicNo=value. It is much better to restructure the data in a *View* so OOPSIE easily can ask the node that has the entity to fetch the data.


#### Partition key

You mark an attribute as a partition key and can of course hold any valid value for the type you defined on that attribute. You can have several attributes marked as partition key on a resource view.

The Partition Key is an advanced feature responsible for data distribution across nodes and partitions in the OOPSIE infrastructure. For every resource OOPSIE keeps track of the amount of data it can store per partition. This means that if you know that your data will grow infinite then you *MUST* add a partition key so your data can be spread out on several partitions an be able to handle more entities. The amount of data on a resource view partition is approx. 500 MB.

So defining a partition key can be extremely useful for data that grows infinite. The OOPSIE Site API will throw an error when max data is reached for a partition. Below we list some things to think of when using partition keys:

- If your data will grow infinite add a partition key to your resource.
- If you define a partition key then a valid value has to be included in the query every time you want to retrieve data.

An example that stores persons ...

- city
- lastName
- firstName

... and city is used as a Partition Key.

Your data will be partitioned by city and you will not be able to have several million persons (entities) that live in same city.

The entities 

```json

    { 
        "city": "Växjö",
        "firstName": "Samuel",
        "lastName": "Jackson"
    }
    
    {
        "city": "Växjö",
        "firstName": "Samuel",
        "lastName": "Andersson"
    }
```
will be stored in the same partition while the entities

```json

    { 
        "city": "Los Angeles",
        "firstName": "Samuel",
        "lastName": "Jackson"
    }
    
    {
        "city": "Växjö",
        "firstName": "Samuel",
        "lastName": "Andersson"
    }
```

will **NOT** be stored in the same partition.


#### Clustering key
------

The Clustering Key is responsible for data sorting within the partition. I.e. when fetching data it will be returned according to the clustering key attributes in the resource. In queries it is possible to "filter" data using clustering keys, just like partition keys, but clustering keys are optional in queries. But if they are present then they have to be in order as declared in the queried resource. An example:

If the person resource mentioned in the partition key section above had lastName as clustering key 1 and firstName as clustering key 2 then it is not possible to query with firstName and omit lastName, but lastName can be queried and omit firstName. To accomplish a query by firstName only then you need to create a new [view](/docs/views) for that specific filtering.

Clustering Key can be sorted by:

- ASC - Ascending order
- DESC - Descending order
