---
title: Resources
permalink: /docs/resources/
---

An application is usually modeled with objects, e.g. a person object or an employee object. These objects holds information about specific object entities, e.g. a person object entity could be a person with name Dalai Lama. In OOPSIE these objects are called a *Resource* and the information resides in *Attributes* such as *name*. A Resources may contain any number of Attributes of various types. All resource entities also gets a unique id and specific resource entities can be queried using this id. To create more advanced queries a resource can be modeled with *Views* to get resource results in a specific manner. To secure the access of resources each resource may have its *Authorization* altered to control specific rights using *Permissions".

------  
### Create a Resource

**1.** Create an application model by following the steps in the section *[What is an applicaton?](/docs/what-is-an-application)*.

**2.** In the *Application Model* view click the blue round button to crate a Resource.

**3.** In the dialog enter an name for your resource and click *Create Resource*.

**4.** In your *application Model* view your resource should appear and you are now able to add attributes so you can fill your resource with data.

------
#### The Resource Panel

In the resource panel you model your *Resource*. Your resource will hold information for each resource entity and you add attributes for specific data, e.g. name, age etc. In the section [Attributes](/docs/attributes) you will learn more about attributes and how to add them to your resource.

You can also create views of your resource. making it easy to query the resource using other attribute than the primary "byId" view using the id mentioned in the first chapter of this document. In the section [Views](/docs/views) you will learn more about views and how to create them.

In the section [Resource Auth](/docs/res-auth) you will learn more about resoruce autorization and how to manage it for your resource.

> When a site is deployed you can update the applications to another version. Note that some updates are not supported.
> **NOT SUPPORTED UPDATES - The most important ones (Not all are listed)**
> * Changing the name of an attribute is not supported.
> * Changing the data type of an attribute is not supported.
> * Changing the key and/or value data type of collection attributes.
> * Changing the type of a resource is not supported.

##### Advanced

A resource can be seen as a database table and it actually is, luckily you don't have to bother about such stuff as databases. But, some advanced configuration needs to be considered.

Since OOPSIE Cloud is deployed on a so called distributed server environment it will distribute its data to several server nodes and partitions. To keep track of where the data resides OOPSIE by default adds a hidden *Partition Key* so OOPSIE API easily can fetch the data at the right place without asking all the nodes for the specific resource entity, that would take alot of time to do so.

A partition in OOPSIE can't grow too big, but pretty big for most of the cases so we actually don't need to think of this most of the time. For each resource OOPSIE will keep track of the resource partition size and eventually the API will give response with an error if the partition has grown to its max, approx. 500 MB. With this in mind it is important for you to understand your data and to model the resources correct. So, if you know that your resource will grow infinite, e.g. sensor based data produced every second, then you need to add your own *Partition Keys* so your resource won't grow too big and eventually complain.