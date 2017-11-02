---
title: Views
permalink: /docs/views/
---

### Overview

Views give you the possibility to retrieve your data in a different way than the default one. When you add the [Attributes](/docs/attributes) you can choose a different query (filtering) order and also change the sorting order.

In the [Resource](/docs/resources) panel locate the view button and click on it to enter View details.

<img src="/img/add-view.png" width="350">

### Example

If you have a Resource with name *Persons* and it has three Attributes, *firstName*, *lastName* and *civicNo*. You want to, by default, retrieve *Persons* entities by *lastName* in ascending order and secondly by *firstName* in ascending order, this you declare when you add your attributes. But you also have another page where the user will search for persons using its civicNo instead, here a view comes handy. if you create a view that is called for eg. *byCivicNo* and add your Attribute *civicNo* you will be able to retrieve your data easily using this view.

#### Advanced
You might wonder why you can't just filter on civicNo when fetching the *Persons* entities, why the need of an extra view? Since OOPSIE distributes its data to several nodes in a distributed server infrastructure it would be very insufficiant to ask all nodes in OOPSIE if it stores a *Persons* entity with a civicNo=value. It is much better to restructure the data in a *View* so OOPSIE easily can ask the node that has the entity to fetch the data.