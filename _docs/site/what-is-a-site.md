---
title: Site
permalink: /docs/what-is-a-site/
---

With a *Site* you publish released *[Applications](/docs/what-is-an-application)* and make them accessible from the internet through a REST api, or even better, by using any of the SDKs for rapid development towards your *OOPSIE Site*. Any released *Application* can be part of any *Site* that you have created. This means that you can reuse the applications models and orchestrate them in sites in any way you want. Lets assume you have created some awesome apps and put these in a Site and your customer was really satisfied. You then get the oppertunity to sell in this to another. Just go ahead an create *(copy function pending)* a new *Site* with the same configuration and deploy it. Nnow you will have two satisfied customers, or as many you like.

A site is totally isolated from other sites you have deployed and also within a *Site* the applications don't "know" about each other. This is very powerful since you can have some applications inactive for upgrade while others are up running and serving your business, this is called micro service management.

> Upgrade of applications in a deployed site is currently not available in the Sandbox environment.

### Creating a Site ###
Hit the menu icon in the top left corner and navigate to the *Sites* view. Click the *CREATE SITEe* button and give it suitable name and click ok. Now you will see something similair to the screenshot below.

<img src="/img/sites-view.png" width="650">

Click the row and you will enter the *Site View* for the chosen site. Three tabs are available, *General*, *Auth*, and *Usage*.

<img src="/img/site-view.png" width="850">

### Manage a site ###

In the *General Settings* panel you change the name of your site, choose a *Production Site* and set *Origins*. Changing name is prettey straight forward but lets talk about the other two properties you can edit.

##### Production Site ######
The  *Production Site* listbox lists all available OOPSIE payment plans. At the moment only Sandbox is available.

##### Origins #####
In the *Origins* box you enter url's that has access to your site. E.g. http://example.com. You can also add a * (star) to allow all urls. Lets say you hava a browser client that will access your OOPSIE site for data. The code for the client is fetched from the site http://myclientcode.com and you want only clients from this url to have access to your OOPSIE site data, then you enter the url http://myclientcode.com in the origins box. This is a browser specific security feature, Cross-Origin Resource Sharing, CORS. This will not prevent other types of clients to access the OOPSIE site.

> You always want to secure your data using the authorization features provided by OOPSIE such as *Api Keys* or *Site Users* managment.

##### Other properties #####

- Customer ID: Identifies the site owner when making requests to the production site.
- Site ID: Identifies the site when making requests to the production site.
- API url: The url of the produciton site. Shown when a production site is chosen.

These three properties is whta you need when accessing the site using REST or any of the SDKs.

##### Adding An Application #####

> *Prerequisites*<br>
> Create and release an *[Application](/docs/what-is-an-application)*

In the *Applications* panel click *ADD APPLICATION* and chooes app and version. The cosen applications are lited and you can see if they are active or not. Initially apps are inactive and you need to deploy the site an then activate your app. Active means that the app and its resources are accessible from the internet.


##### Deployment #####
If everything is configured properly you should be able to swipe the *Deployed* button and within seconds the site will be deployed, don't forget to activate your apps if it is the first time you deploy the site. Your site is most likely not yet accessible, you need to create an *[Api Key](/docs/api-keys)* or  *[Users](/docs/users)*.

##### Usage #####