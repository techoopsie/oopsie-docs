---
title: Api keys
permalink: /docs/api-keys/
---

If Auth is enabled on your *Application Resources* then you need an *API Key* or a [User](/docs/users) to access the resource.

Creating an *API Key* is pretty straight forward. Make sure you have your site deployed and navigate to the *Auth* tab in the site view. If you decide to undeploy your site your *API Keys* will still be available when you deploy again.

>**Always be carefull with your Api keys!<br> If you think one is compromised, revoke it immediatelly!**

You can create as many *API Keys* that you want and each of them can have different permissisons configured on *Resource* level. This is a really powerful feature that makes it possible for you to issue keys to your trusted third party users with different access rights. Furthermore, you can enter an optional expires date and revoking a key is as simple as clicking the *Revoke API Key* button*.

You will get the option of downloading the key and the first part of the file name is the id of the *API Key* (***\<api-key-id\>.oopsie.apikey***). Copy the whole file 
content into your client (SDK to init Site object) when you want to call the site.

> **WARNING!**<br>We DO NOT store any secret (the key part) so loosing it means lost for ever. If you loose it then you should immediatelly revoke the key!