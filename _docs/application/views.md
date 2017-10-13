---
title: Views
permalink: /docs/views/
---

### Overview

Views give you the possibility to retrieve your data in a different way then the default one.

The [Attributes](/docs/attributes) you add in your view will be possible to use while querying for your data later, you can also decide if you want it to be sorted by *ASC* or *DESC* per [Attribute](/docs/attributes) you add to your View.

### Example

If you have a Resource with name *Person* and it has two Attributes, *firstname* and *lastname*. You want to by default to retrieve all of your *Persons* by *firstname* in descending order. But you also have another page or a table where the user change the ordering to order by *lastname* ascending or descending instead ( or it might be that you want to create a graph or whatever ). This is when a View is perfect, if you create a View that is called for eg. *byLastname* and add your Attribute *lastname* you will be able to retrieve your data by this by quering below url from the REST Api or by using one of our SDKs.

   /resources/:resourceId/views/byLastname