---
title: Quickstart
permalink: /docs/quickstart/
---

>Estimated time: 15 - 30m

This guide will show you how to create and deploy your first Site with Oopsie within minutes. We will go step by step until you have your Site running in our Sandbox environment.

The result of this guide will be a deployed Site ( *TodoSite* ) that has an Application ( *TodoApp* ) with one Resource ( *Todo* ) that has two Attributes ( *name*, *done* ). We will be able to POST(create), GET(retrieve), PUT(update) and DEL(delete) Todo entities via a simple API or use one of our SDKs (SDKs are not included in this guide yet) 

Altough Oopsie is created to handle a huge amount of traffic and data ( Big Data ), it also works for smaller apps as well, that wants to have the possibility to scale from 1 request a day to 100k requests per second. Why should you have to care about big and complex backends instead of working on your idea?

The place that all the modelling and deployment of your site takes place is in our [Dashboard](http://oopsie-dev.techoopsie.com).

### Prerequisits:
------

- Oopsie account ( Don't have one? Create one at [Dashboard](http://oopsie.io))
- Internet access ( which you obviously have? )

That's it! Isn't it great!?

### Create your first Application
------

We will start by creating an [Application](/docs/what-is-an-application).
Everything we will do will be in our [Dashboard](http://oopsie.io), so if you are not there yet you should navigate there in another tab.

**1.** Navigate to Application Models in the sidebar and press the button that says *Create Application*.

   ![Navigate to Application](/img/sidebar-app.png "Navigate to Application")

**2.** Fill in the name you want for you Application, we will use *TodoApp* for this example (you may add an [Authorization](/docs/what-is-an-authorization) but we will skip this in the quickstart) and press *OK*.

   ![Create Application](/img/create-app.png "Create Application")


**3.** You should now see your new Application in the table. Click it! Hopefully you don't get too scared when you enter your new Application ( It's not too much there YET )
 
   ![New empty Application](/img/created-app.png "New empty Application")

**4.** Take a look at the top tabs, you should see *Resources*, *Application* and *Docs*.

   - Resources - this is where you model your different [Resources](/docs/resources) in your Application.
   - Application - Here you have general things about your Application, like change the name or create a release.
   - Docs - If you would like to see what your endpoints will look like on your site, this is where to look. It's a generated Swagger documentation for you.

   ![Empty Application](/img/app-without-resources.png "Empty Application")

**5.** We probably don't want to change the name of our Application ( yet ), so we will start by creating a [Resource](/docs/resources). Give it the name *Todo*.

   ![Create Resource](/img/create-resource.png "Create Resource")

**6.** Now that we have a resource we can actually start the real modelling, the Attributes. As stated in the beginning of this quickstart we will have two Attributes, one called *name* that should probably be a *TEXT_64* and one called *done* that is a boolean. When you are done press the save button in the upper right corner of the [Resource](/docs/resources)

   >**Note:** You probably wonder what all these *Partition Key*, *Cluster Key*, etc is but we will not worry about that now. You can read more about it later.

   ![Create Attributes](/img/both-attributes-created.png "Create Attributes")

**7.** Your application is done! Gob job! What we need to do now is create a release of it, to deploy it to a Site.

   Navigate to the *Application* tab and *Create a release* called 1.0 ( You may give a description if you'd like ).

   ![Create Release](/img/create-release-3.png "Create Release")

   ![Create Release Dialog](/img/create-release-dialog.png "Create Release Dialog")

   ![Release Created](/img/release-created.png "Release Created")



By now you should have an Application called *TodoApp* with a Resource by name *Todo* that has 2 Attributes, *name* and *done* and your first release 1.0.

### Create your first Site
------

A Site contains a number of Applications, may have an Authorization and is possible to deploy to go Live with.

**1.** Navigate to Site from the sidebar.

   ![Site sidebar](/img/site-sidebar.png "Site sidebar")

**2.** Create your site, *TodoSite*

   ![Create Site](/img/create-site.png "Create Site")

   ![Site create](/img/site-created.png "Site create")

**3.** When you enter the site you will see something like this. As you can see you may not deploy the site yet because you need to have at least one Application and a Production site ( which Oopsie cloud to deploy too ).

   ![Entered Site](/img/entered-site.png "Entered Site")

**4.** We will start by adding a Production Site and a Origin ( safetynet so other sites can't use your Site in a browser directly ). You will find these settings in the *General Settings* panel. Use *Sandbox* since that one is for free, it will be rate limited pretty hard and should not be used in production.

   ![General settings](/img/general-settings.png "General settings")

   When you have filled it in you save by pressing the checkbox at the top of the panel.

**5.** Last thing to do before we may deploy our Site is to add at least one Application, good thing we have one! You do this in the *Applications* panel.

   ![Add Application to Site](/img/add-app-to-site.png "Add Application to Site")

**6.** By now the Deploy button should be enabled, but still red, which means your Site is Undeployed. Go ahead and deploy it!

   ![Site ready to deploy](/img/site-ready-to-deploy.png "Site ready to deploy")

*7.** By now your Site should be deployed, but your Application is not active, active it by clicking activate.

### Test your Site

If you have followed all the previous steps you should now have a deployed Site, ready to be used. Last thing to do is storing some todos and getting them.

There are alot of different ways to use your Site, either through a REST Api or by using one of our SDKs for Javascript, Java, etc.

In this guide we will test our Site by using the REST Api because this we can do directly from Oopsie dashboard. If you look at your tabs in the Site view you will see there is a tab called *Usage*, click on it.

Here you can see an autogenerated swagger documentation of your site and it's even possible to test it by clicking the button *try-it-out* per endpoint.

![Site Usage](/img/site-usage.png "Site Usage")

As you can see you have your app there with the different http methods (GET,POST,PUT,DELETE). Scroll down to *TodoApp/Todo* and press on the blue GET panel.

![Site Usage Todo Application](/img/site-todo-app.png "Site Usage Todo Application")

![Site Usage Get](/img/site-usage-get.png "Site Usage Get")

If you now press *try-it-out*, you can test to retrieve your Todos.

![Site Usage Get Try it out](/img/site-usage-get-try-it-out.png "Site Usage Get Try it out")

Go ahead and create, get, update and delete some of your Todos :)

Maybe you would like to be able to get your *Todos* by *name*, no problem, just create a [View](/docs/views) or update your app to have a [*Clustering Key*](/docs/attributes#Clustering Key) for it! 

### Done

Hope you enjoyed this Quickstart, if you have any feedback or would like other tutorials, feel free to contact us or create a pull request to this repository ( button right below will guide you to it ).