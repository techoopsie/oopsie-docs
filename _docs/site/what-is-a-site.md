---
title: Site
permalink: /docs/what-is-a-site/
---

With a *Site* you publish released *[Applications](/docs/what-is-an-application)* and make them accessible from the internet through a REST api, or even better, by using any of the SDKs for rapid development towards your *OOPSIE Site*. Any released *Application* can be part of any *Site* that you have created. This means that you can reuse the applications models and orchestrate them in sites in any way you want. Lets assume you have created some awesome apps and put these in a Site and your customer was really satisfied. You then get the oppertunity to sell in this to another. Just go ahead an create *(copy function pending)* a new *Site* with the same configuration and deploy it. Now you will have two satisfied customers, or as many you like.

A site is totally isolated from other sites you have deployed and also within a *Site* the applications don't "know" about each other. This is very powerful since you can have some applications inactive for upgrade while others are up running and serving your business, this is called micro service management.

### Creating a Site ###
Hit the menu icon in the top left corner and navigate to the *Sites* view. Click the blue round button in the bottom right corner and give the new site a suitable name and click ok.

You will now see your new site slide in as a new row. Click the row and you will enter the *Site View* for the chosen site. Here you will see three panels and some buttons all used to manage your site.

### Manage a site ###

In the *General Settings* panel you change the name of your site, choose a *Production Site* and set *Origins*. Changing name is pretty straight forward but lets talk about the other two properties you can edit.

##### Production Site ######
The  *Production Site* listbox lists all available OOPSIE payment plans. At the moment only Free is available.

##### Origins #####
In the *Origins* box you enter url's that has access to your site. E.g. http://example.com. You can also add a * (star) to allow all urls. Lets say you have a browser client that will access your OOPSIE site for data. The code for the client is fetched from the site http://myclientcode.com and you want only clients from this url to have access to your OOPSIE site data, then you enter the url http://myclientcode.com in the origins box. This is a browser security feature, Cross-Origin Resource Sharing, CORS. 

> **Warning**<br>
> This will not prevent other types of clients to access the OOPSIE site. You always want to secure your data using the authorization features provided by OOPSIE such as *Api Keys* or *Site Users*

##### Other properties #####

- Customer ID: Identifies the site owner when making requests to the production site.
- Site ID: Identifies the site when making requests to the production site.
- API url: The url of the produciton site. Shown when a production site is chosen.

These three properties is what you need when accessing the site using REST or any of the SDKs.

##### Adding An Application #####

> **Prerequisites**<br>
> Create and release an *[Application](/docs/what-is-an-application)*

In the *Applications* panel click *ADD APPLICATION* and choose app and version. The chosen applications are listed and you can see if they are active or not. Initially apps are inactive and you need to deploy the site an then activate your app. Active means that the app and its resources are accessible from the internet.

##### Update Application Version #####

> **Prerequisites**<br>
> Create and release an *[Application](/docs/what-is-an-application)*
> Deploy a Site with an application

In the Application panel all your deployed applications are listed. First, make sure that the application you want to upgrade, or downgrade for that matter, is deactivated. You deactivate by swiping the button so it turns red. Click the "UPDATE APPLICATION" button and choose a new version. If the version update could not be fullfilled you will be prompted about the why it could no be updated. Furthermore, in some cases a default value needs to be entered if any attribute is either changed or added. NOte that if you update to a version that has removed an attribute the data for that removed attribute will be lost.

> **NOT SUPPORTED UPDATES - The most important ones (Not all are listed)**
> * Changing the name of an attribute is not supported.
> * Changing the data type of an attribute is not supported.
> * Changing the key and/or value data type of collection attributes.
> * Changing the type of a resource is not supported.


##### Deployment #####
If everything is configured properly you should be able to swipe the *Deployed* button and within seconds the site will be deployed, don't forget to activate your apps if it is the first time you deploy the site. Your site is most likely not yet accessible since you probably configured your resources wiht the auth option on. You need to create an *[Api Key](/docs/api-keys)* or  *[Users](/docs/users)*.

##### Auth #####
In the upper right corner an Auth button is available, click to handle [API Keys](/docs/api-keys) and [Users](/docs/users) and how these are handled by the site on a request.

- The ***Only allow API Keys*** option tells the site that only requests with an api key can be handled, *user* requests will be rejected.

- The ***Allowed users to register through API*** option tells the site that, when registering [Users](/docs/users), only users with chosen [Auths](/docs/what-is-auth) can be registered through API (SDK). A good idea is to NOT let the admin role be registerable through API/clients, since the admin role has access to everything.

### Advanced ###
##### View Usage #####

> Prerequisites<br>
> If auth is enabled on your *Resources* then you must first create an *API Key*.

If you want to try it out just head over to the *View Usage* view by clicking the *View Usage* button in the upper right corner. This is a Swagger generated documentation of all REST endpoints in your site and gives you the possibility to actually make real REST endpoint calls to the deployed site's application resource.

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

Below we see the interesting part, the response body. Along with your posted attribute data you see that id attribute has got a value generated by the API.

```JSON
{
  "name": "Techoopsie AB",
  "city": "Växjö",
  "id": "52f0d234-9c00-47e3-b595-ac700345e2fb"
}
```

##### Entity Identification #####

- ***id*** - Uniquely identifies a specific resource entity.

This is a UUID that you use when you want to later fetch specific entities.



