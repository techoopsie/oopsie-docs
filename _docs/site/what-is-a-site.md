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
In the *Origins* box you enter url's that has access to your site. E.g. http://example.com. You can also add a * (star) to allow all urls. Lets say you hava a browser client that will access your OOPSIE site for data. The code for the client is fetched from the site http://myclientcode.com and you want only clients from this url to have access to your OOPSIE site data, then you enter the url http://myclientcode.com in the origins box. This is a browser security feature, Cross-Origin Resource Sharing, CORS. 

> **Warning**<br>
> This will not prevent other types of clients to access the OOPSIE site. You always want to secure your data using the authorization features provided by OOPSIE such as *Api Keys* or *Site Users*

##### Other properties #####

- Customer ID: Identifies the site owner when making requests to the production site.
- Site ID: Identifies the site when making requests to the production site.
- API url: The url of the produciton site. Shown when a production site is chosen.

These three properties is whta you need when accessing the site using REST or any of the SDKs.

##### Adding An Application #####

> **Prerequisites**<br>
> Create and release an *[Application](/docs/what-is-an-application)*

In the *Applications* panel click *ADD APPLICATION* and choose app and version. The cosen applications are lited and you can see if they are active or not. Initially apps are inactive and you need to deploy the site an then activate your app. Active means that the app and its resources are accessible from the internet.


##### Deployment #####
If everything is configured properly you should be able to swipe the *Deployed* button and within seconds the site will be deployed, don't forget to activate your apps if it is the first time you deploy the site. Your site is most likely not yet accessible, you need to create an *[Api Key](/docs/api-keys)* or  *[Users](/docs/users)*.

##### Auth #####
In the Auth tab you handle [API Keys](/docs/api-keys) and [Users](/docs/users) and how these are handled by the site on a request.

- The ***Only allow API Keys*** option tells the site that only requests with an api key can be handled, *user* requests will be rejected.

- The ***Allowed users to register through API*** option tells the site that, when registering [Users](/docs/users), only users with chosen [Auths](/docs/what-is-auth) can be registered through API (SDK).

### Advanced ###
##### Usage #####

> Prerequisites<br>
> If auth is enabled on your *Resources* then you must first create an *API Key*.

If you want to try it out just head over to the *Usage* tab. This is a Swagger generated documentation of all REST enpoints in your site and gives you the possibility to actually make real REST enpoint calls to the deployed site's application resource.

The endpoints are grouped by *Application/Resource* and if you click on the header it will expand and expose the four REST api HTTP methods available.
- GET - Fetch one or more resource entities from resource
- POST - Create a resource entity
- PUT - Save existing resource entity
- DELETE - Delete resoruce entity

You can click on each of these *methods* an it will open up the endpoint view with information of requst parameters and response. By clicking the *Try it out* button you will be able to enter data that you want to send together with the request.

- ***oopsie-customer-id*** - Prepopulated with the current site's customerID.
- ***oopsie-site-id*** - Prepopulated with the current site's siteID.
- ***body*** - JSON with of the resource's all settable attributes.

The *body* is a JSON view of all the settable attributes and can be changed to something like:

```JSON
{
  "name": "Techoopsie AB",
  "city": "Växjö"
}
```
If you have auth enabled you need you api key. Click the padlock on the resource header you want to try and fill in your api key in the box. Now you can click the *Execute* button and it will make a call to the site and a response will be shown just below the buttons in panel with a response code 201.

<img src="/img/post-response.png" width="850">

Below we see the interesting part, the response bodu. Along with your posted attribute data you see five other attributes. These are data inserted by default for every call made to a POST or PUT.

```JSON
{
  "name": "Techoopsie AB",
  "city": "Växjö",
  "crb": "cb3524eb-3d83-4784-b681-75c1e85ac4ef",
  "cra": "2017-11-03T07:22:38.464Z",
  "chb": "cb3524eb-3d83-4784-b681-75c1e85ac4ef",
  "cha": "2017-11-03T07:22:38.464Z",
  "eid": "52f0d234-9c00-47e3-b595-ac700345e2fb"
}
```

##### Entity Identification #####

- ***eid*** - Uniquely identifies a specific resource entity.

This is a UUID that you use when you want to later fetch specific entities.

##### Audit #####

- ***crb*** -  Created By. The id of "creator"subject creating the data, in this case the api key. (POST)
- ***cra*** -  Created At. The time the POST occurded (POST)
- ***chb*** -  Changed By. The id of subject changing the data, in this case the api key. (POST/PUT)
- ***cha*** -  Changed At. The time the change occurded (POST/PUT)


