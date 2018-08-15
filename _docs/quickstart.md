---
title: Quickstart
permalink: /docs/quickstart/
---

>Estimated time: 15 - 30m

This guide will show you how to create and deploy your first Site with OOPSIE within minutes. We will guide you step by step until you have your Site running.

The result of this guide will be a deployed *[Site](/docs/what-is-a-site)* ( *TodoSite* ) that has an *[Application](/docs/what-is-an-application)* ( *TodoApp* ) with one *[Resource](/docs/resources)* ( *Todo* ) that has two Attributes ( *name*, *done* ). We will be able to POST(create), GET(fetch), PUT(update) and DELETE(delete) Todo entities via a simple API or use one of our SDKs.

Altough OOPSIE is created to handle a huge amount of traffic and data ( Big Data ), it also works for smaller apps as well, e.g. apps taht wants to have the possibility to scale from 1 request a day to 10k requests per second. Why should you have to care about big and complex backends instead of working on your idea?

The place that all the modelling and deployment of your site takes place is in our [Dashboard](https://dashboard-next.oopsie.io).

### Prerequisits:
------

- OOPSIE account ( Don't have one? Create one at [oopsie.io](https://oopsie.io/create-account))
- Internet access ( which you obviously have? )

### Workflow to get your site up and running
-  Create an *[Application](/docs/what-is-an-application)*
-  Create a *[Resource](/docs/resources)*
-  Add *[Attributes](/docs/attributes)* to the *[Resource](/docs/resources)*
-  Create a release of the *[Application](/docs/what-is-an-application)*
-  Create a *[Site](/docs/what-is-a-site)*
-  Add the *[Application Release](/docs/what-is-an-application)* to the *[Site](/docs/what-is-a-site)*
-  Set the *General Settings* of your *[Site](/docs/what-is-a-site)* and create *[API Key](/docs/api-keys)* if *[Auth](/docs/res-auth)* is enabled

### Create your first Application
------

We will start by creating an [Application](/docs/what-is-an-application).
Everything we will do will be in our [Dashboard](https://dashboard-next.oopsie.io), so if you are not there yet you should navigate there in another tab. The default view in the dashboard is the [Sites](/docs/what-is-a-site) view. Just hit the menu button in the left upper corner and then follow the steps below.

**1.** Navigate to application models view by clicking "Application MOdels", the highlighted item in the sidebar image below.
<img src="/img/sidebar-app.png" width="150">

**2.** When Application Models view is loaded nothing is really shown since you don't have any apps yet. You should see a big blue round button with a plus in your right bottom corner though, click it. Fill in the name you want for you Application, we will use *TodoApp* for this example, press *OK* (you may add an [Authorization](/docs/what-is-an-authorization) but we will skip this in the quickstart).
<img src="/img/create-app.png" width="550">
> **Warning**<br>
> A deployed application or a resource with no authorization will be publicly accessible on the internet. Remember to undeploy if you go live with your example application. Read more about [Authorization](/docs/what-is-an-authorization)*

**3.** You should now see your new Application in the table. Click it! 
<img src="/img/created-app.png" width="550">

**4.** Now you have entered the view of your Application "TodoApp". The first time you enter the application's view a message is shown since you have not created any resources in your app. A resource can be seen as an object in your application and defines the structure of your data for that object. You will learn more about this in the *[Resource](/docs/resources)* section.
<img src="/img/app-without-resources.png" width="550">

**5.** Create a [Resource](/docs/resources) by clicking the blue round button in your right bottom corner. Give it the name *Todo*.
<img src="/img/create-resource.png" width="550">

**6.** Now that we have a resource we can actually start the real modeling, adding the [Attributes](/docs/attributes). As stated in the beginning of this quickstart we will have two Attributes, one called *name* of type *Text* and one called *done* that is of type *Boolean*. Click the "pen" button and then click "Add Attribute" for each of them. When done click the save button.
<img src="/img/both-attributes-created.png" width="450">
   >**Note:**
   >All resources always have an id attribute and is added by default. This id identifies a specific resource entitiy you have saved. You don't need to worry about setting values for id, this is handled by OOPSIE when you save entities/objects in your application.

**7.** Your application is done! What we need to do now is create a release of it so we are able to deploy it to a Site. Click the "Release" button on the top right corner and then click "Create Release" enter "1.0" ( You may give a description if you'd like ).
<img src="/img/create-release-dialog.png" width="650">

When you create your first release of an application you get the option to navigate to the Sites view, do this.

By now you should have an Application called *TodoApp* with a Resource by name *Todo* that has 2 Attributes, *name* and *done* and your first release 1.0.

### Create your first Site
------

With sites you choose which applications you want to deploy and all applications in a site share the same access point (url) and other configurations such as security and authorization. An application model can be used in several sites.

**1.** Navigate to Site from the sidebar if you are not already there.

**2.** Create your site by clicking the blue round button and name it *TodoSite*

<img src="/img/create-site.png" width="550">

**3.** Enter your site by clicking the row with your site, you might need to click the save button first. You can not deploy the site yet because you need to have at least one Application and a Production site (the OOPSIE cloud to deploy too).

<img src="/img/entered-site.png" width="650">

**4.** We will start by adding a Production Site and a Origin (safetynet so other sites can't use your Site in a browser directly). You will find these settings in the *General Settings* panel. Use *Free* since that one you can use at no charge, it will be *Limited* pretty hard and should not be used in production. Click the pen button in the "General Settings" panel. For the Origin option just enter a the star character "*".

**5.** Last thing to do before we may deploy our Site is to add at least one Application, good thing we have one! You do this in the *Applications* panel.

<img src="/img/add-app-to-site.png" width="550">

**6.** By now the Deploy button should be enabled, but still red, which means your Site is Undeployed. Go ahead and deploy it!

<img src="/img/site-ready-to-deploy.png" width="650">

**7.** By now your Site should be deployed, but your Application is not active, activate it by clicking activate. Click application row to expand it if you can't see the "Activate" button.

### Test your Site

If you have followed all the previous steps you should now have a deployed Site, ready to be used. Last thing to do is storing some todos and getting them.

There are alot of different ways to use your Site, either through a REST Api or by using one of our SDKs for Javascript, Java, etc.

In this guide we will test our Site by using the REST Api because this we can do directly from Oopsie dashboard. If you look at your tabs in the Site view you will see there is a tab called *Usage*, click on it.

Here you can see an autogenerated swagger documentation of your site and it's even possible to test it by clicking the button *try-it-out* per endpoint.

<img src="/img/site-usage.png" width="650">

As you can see you have your app there with the different http methods (GET,POST,PUT,DELETE). Scroll down to *TodoApp/Todo* and press on the blue GET panel.

<img src="/img/site-todo-app.png" width="650">

<img src="/img/site-usage-get.png" width="650">

If you now press *try-it-out*, you can test to retrieve your Todos.

<img src="/img/site-usage-get-try-it-out.png" width="650">

Go ahead and create, get, update and delete some of your Todos :)

Maybe you would like to be able to get your *Todos* by *name*, no problem, just create a [View](/docs/views) or update your app to have a [*Clustering Key*](/docs/attributes#Clustering Key) for it! 

### Done

Hope you enjoyed this Quickstart, if you have any feedback or would like other tutorials, feel free to contact us or create a pull request to this repository ( button right below will guide you to it ).