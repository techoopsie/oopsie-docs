---
title: Java SDK
permalink: /docs/java-sdk/
---


## Install

### Maven
``` 
	<dependency>
		<groupId>io.oopsie</groupId>
  		<artifactId>oopsie-sdk-java</artifactId>
  		<version>1.0-RC4</version>
	</dependency>
``` 

### Prerequisites
* [Register](https://oopsie.io/create-account) yourself and your company at [oopsie](https://oopsie.io)
* [Login](https://dashboard.oopsie.io) to the dashboard and deploy an oopsie site.
* Customer ID, Site ID and API Key information fetched from *[Site View](/docs/what-is-a-site)*

### Initialize site

```
    Site librarySite = new Site(apiUrl, customerId, siteId, apiKey);
    librarySite.init();
    
    ...
    
```

### Choose app and resource

```
    Application bookApp = librarySite.getApplication("BookApp");
    Resource bookRes = bookApp.getResource("Book");
    
    ...
    
```

### Create entity (HTTP POST)

```
	Statement stmnt = bookRes.create()
		.withParam("Title", "The Master and Margarita")
    		.withParam("Author", "bulgakov, mikhail");
    ResultSet result = librarySite.execute(stmnt);
    Row row = result.one();
    UUID bookId = row.getUUID("eid");
    
    ...
    
```

### Get entity (HTTP GET)
```
	stmnt = bookRes.get().withParam("eid", bookId);
	ResultSet result = librarySite.execute(stmnt);
	String author = result.one().getString("Author");
	
	...
	
```

### Save entity (HTTP PUT)
```
	Map<String, Object> params = new HashMap();
	params.put("eid", bookId);
	params.put("Title", "The Master and Margarita");
	params.put("Author", "Bulgakov, Mikhail");
	
	stmnt = bookRes.save().withParams(params);
	ResultSet result = librarySite.execute(stmnt);
	
	...
	
```

### Delete entity (HTTP DELETE)
```
	stmnt = bookRes.delete().withParam("eid", bookId);
	librarySite.execute(stmnt);
	
	...
	
```

### Save Partitial entity (HTTP PATCH)

Soon available.

