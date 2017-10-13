---
title: Quickstart
permalink: /docs/quickstart/
---

>Estimated time: 15 - 30m

This guide will show you how to create and deploy your first Site with Oopsie within minutes. We will go step by step until you have your Site running in our Sandbox environment.

The result of this guide will be a deployed Site ( *TodoSite* ) that has an Application ( *TodoApp* ) with one Resource ( *Todo* ) that has two Attributes ( *name*, *done* ). We will be able to POST(create), GET(retrieve), PUT(update) and DEL(delete) Todo entities via a simple API or use one of our SDKs (SDKs are not included in this guide yet) 

Altough Oopsie is created to handle a huge amount of traffic and data ( Big Data ), it also works for smaller apps as well, that wants to have the possibility to scale from 1 request a day to 100k requests per second. Why should you have to care about big and complex backends instead of working on your idea?

The place that all the modelling and deployment of your site takes place is in our [Dashboard](https://dashboard.oopsie.io).

### Prerequisits:
------

- Oopsie account ( Don't have one? Create one at [oopsie.io](https://oopsie.io/create-account))
- Internet access ( which you obviously have? )

That's it! Isn't it great!?

### Create your first Application
------

We will start by creating an [Application](/docs/what-is-an-application).
Everything we will do will be in our [Dashboard](https://dashboard.oopsie.io), so if you are not there yet you should navigate there in another tab. The default view in the dashboard is the [Sites](/docs/what-is-a-site) view. Just hit the menu button in the left upper corner and then follow the steps below.

**1.** Navigate to Application Models View in the sidebar (highlighted item). Now you should see a *Create Application* button, press it and continue with next step below.

<img src="/img/sidebar-app.png" width="350">

**2.** Fill in the name you want for you Application, we will use *TodoApp* for this example (you may add an [Authorization](/docs/what-is-an-authorization) but we will skip this in the quickstart) and press *OK*.

<img src="/img/create-app.png" width="550">

**3.** You should now see your new Application in the table. Click it! Hopefully you don't get too scared when you enter your new Application ( It's not too much there YET )
 
<img src="/img/created-app.png" width="550">

**4.** Take a look at the top tabs, you should see *Resources*, *Application* and *Docs*.

   - Resources - this is where you model your different [Resources](/docs/resources) in your Application.
   - Application - Here you have general things about your Application, like change the name or create a release.
   - Docs - If you would like to see what your endpoints will look like on your site, this is where to look. It's a generated Swagger documentation for you.

<img src="/img/app-without-resources.png" width="550">

**5.** We probably don't want to change the name of our Application ( yet ), so we will start by creating a [Resource](/docs/resources). Give it the name *Todo*.

<img src="/img/create-resource.png" width="550">

**6.** Now that we have a resource we can actually start the real modelling, the Attributes. As stated in the beginning of this quickstart we will have two Attributes, one called *name* of type *Text* and one called *done* that is of type *Boolean*. For each attribute you need to mark it as done using the check button. When you are done press the save button in the upper right corner of the [Resource](/docs/resources)

   >**Note:** You probably wonder what all these *Partition Key*, *Cluster Key*, etc is but we will not worry about that now. You can read more about it later.

<img src="/img/both-attributes-created.png" width="550">

**7.** Your application is done! Gob job! What we need to do now is create a release of it, to deploy it to a Site.

   Navigate to the *Application* tab and *Create a release* called 1.0 ( You may give a description if you'd like ).

<img src="/img/create-release-3.png" width="550">

<img src="/img/create-release-dialog.png" width="550">

<img src="/img/release-created.png" width="550">

By now you should have an Application called *TodoApp* with a Resource by name *Todo* that has 2 Attributes, *name* and *done* and your first release 1.0.

### Create your first Site
------

With sites you choose which applications you want to deploy and all applications in a site share the same base url and other configurations such as security and authorization. An application model can be used in several sites.

**1.** Navigate to Site from the sidebar.

<img src="/img/site-sidebar.png" width="550">

**2.** Create your site, *TodoSite*

<img src="/img/create-site.png" width="550">

<img src="/img/site-created.png" width="550">

**3.** When you enter the site view you will see something like this. As you can see you may not deploy the site yet because you need to have at least one Application and a Production site (the OOPSIE cloud to deploy too).

<img src="/img/entered-site.png" width="650">

**4.** We will start by adding a Production Site and a Origin (safetynet so other sites can't use your Site in a browser directly). You will find these settings in the *General Settings* panel. Use *Sandbox* since that one is for free, it will be *Rate Limited* pretty hard and should not be used in production.

<img src="/img/general-settings.png" width="550">

   When you have filled it in you save by pressing the check button at the top of the panel.

**5.** Last thing to do before we may deploy our Site is to add at least one Application, good thing we have one! You do this in the *Applications* panel.

<img src="/img/add-app-to-site.png" width="550">

**6.** By now the Deploy button should be enabled, but still red, which means your Site is Undeployed. Go ahead and deploy it!

<img src="/img/site-ready-to-deploy.png" width="650">

**7.** By now your Site should be deployed, but your Application is not active, active it by clicking activate.

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