---
title: Resources
permalink: /docs/resources/
---

An application is usually modeled with objects, e.g. a person object or an employee object. These objects holds information about specific object entities, e.g. a person object entity could be a person with name Dalai Lama. In OOPSIE these objects are called a *Resource* and the information resides in *Attributes* such as *name*. A Resources may contain any number of Attributes of various types. All resource entities also gets a unique id (eid) and specific resource entities can be queried using this eid. To create more advanced queries a resource can be modeled with *Views* to get resource results in a specific manner. To secure the access of resources each resource may have its *Authorization* altered to control specific rights using *Permissions".

------
### Create a Resource

**1.** Create an application model by following the steps in the section *[What is an applicaton?](/docs/what-is-an-application)*.

**2.** In the *Application Model* view click the button *Create Resource*.

**3.** In the dialog enter an name for your resource and click *OK*. In the dialog an *Advanced* option is available. This option has only one choice at the moment but in the near future it will be possible to choose different types of resources for specific puposes, e.g. timebased resource types for sensor data.

**4.** In your *application Model* view your resource should appear and you are now able to add attributes so you can fill your resource with data.

<img src="/img/resource-panel.png" width="650">

------
#### The Resource Panel

In the resource panel you model your *Resource*. Your resource will hold information for each resource entity and you add attributes for specific data, e.g. name, age etc. In the section [Attributes](/docs/attributes) you will learn more about attributes and how to add them to your resource.

You can also create views of your resource. making it easy to query the resource using other attribute than the defult eid mentioned in the first chapter of this document. In the section [Views](/docs/views) you will learn more about views and how to create them.

In the section [Resource Auth](/docs/res-auth) you will learn more about resoruce autorization and how to manage it for your resource.

##### Advanced

A resource can be seen as a database table and it actually is, luckily you don't have to bother about such stuff as databases. But, some advanced configuration needs to be considered.

Since OOPSIE Cloud is deployed on a so called distributed server environment it will distribute its data to several server nodes or partitions. To keep track of where the data resides OOPSIE by default adds a hidden *Partition Key* so OOPSIE API easily can fetch the data at the right place without asking all the nodes for the specific resource entity, that would take alot of time to do so.

A partition in OOPSIE can't grow too big, but pretty big for most of the cases so we actually don't need to think of this most of the time. For each resource OOPSIE calculates how many entities a resource partition can hold. Depending on the amount of attributes and the type and size of the attributes OOPSIE recalculates the partition entity max size when you save your resource. Hover over the blue information icon in the panel header to see how many entities you can store for the current configuration.

So, if you know that your resource will grow infinite, e.g. sensor based data produced every second, then you need to add your own *Partition Key* so your resource won't grow too big and eventually complain. In our examples section we give you an example of using partition keys to come around this. Head over to [Sensor Data Example](/docs/sensor) to have a look.