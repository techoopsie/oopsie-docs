---
title: What is an Application?
permalink: /docs/what-is-an-application/
---

An *Application Model* acts like a template and holds a number of resources to store data. An applicaiton model can be released for later use on a Site.

An Application contains:

- Any number of Resources
- One Authorization Model (Optional)

### Workflow:
------
**1.** Create an Application.

**2.** Create a Resource in your Application.

**3.** Model your Resource.

**4.** Repeat **2** to **3** until you are satisfied.

**3.** Create a release.

### Create an Application
------

**1.** In the sidebar menu of the OOPSIE dashboard click on the *Application Models* menu item.

**2.** Click the *Create Application* button.

**3.** Enter a name for your application and choose an [Authorization Model](/docs/what-is-auth). Authorization is optional but we strongly recommend choosing one since your application will be totally open for anyone. If no Authorization Model exist then  you can create one using one of the two buttons. When ready click *OK* to create your application.

**4.** Now your browser should load the Application Models view and your application should be in the list of applications. By clicking on the row you will navigate to the applicaiton view. You can also delete the application if you aren't satisfied with it.

### Create a Resource
------

If you followed the steps in the previous chapter *Create an Application* the you should now be in the *Application Models* view. In this view you model your application by adding resources, creating releases and other configurations for your application model.

To create a resource for your application model head over to the [Resource Section](/docs/resources) in this guide.

### Create a release of your Application
------

When you are done modelling your Application you should tag it (create a release) that you can use on a Site.

![Create release of Applic.ation](/img/create-release2.png "Create release of Application")

### The API / Docs
------

While you are modelling your Application you can always look how you will use your Application later on when it is Deployed on a Site. 

The documentation is generated using Swagger.


![Documentation of Application](/img/docs-app.png "Documentation of Application")
