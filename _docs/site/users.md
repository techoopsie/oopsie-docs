---
title: Users
permalink: /docs/users/
---

If you app is very user frequent then you most likely want to create the users through the API using any of the available SDKs. But some types of users such as Admin you don't want to be created from client side.

Adding a user is pretty straight forward, just fill in all the fields required and hand over the user name (email) and password in a secure manner to the site user you want to have access to your site. Although you are not choosing the *User* [Auth](/docs/what-is-auth) all users will get this Auth.

> WARNING!<br>Be careful with the Auth option *Admin* since this Auth always have all permissions to all resources on the site.

