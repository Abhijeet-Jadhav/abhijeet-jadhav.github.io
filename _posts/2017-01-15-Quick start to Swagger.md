---
layout: post
title: Quick start to Swagger
image: /img/REST_api_docs_image.png
tags: [swagger, rest api documentation, jersey]
---


# Swagger 
Swagger is a specification and framework implementation for describing and visualizing RESTful web services.
The specifications can be written in either JSON or YAML. In this blog we will generate swagger.json file accordingly. 

Swagger-core allows you to generate a Swagger spec from the code. Swagger spec in this case will be the generated swagger.json file.
Swagger-ui is used to integrate spec file into your code for the actual display.
Setting it up is fairly easy we will see the detail steps below. It’s a static set of pages you need to host like any web app, 
and configure it to load the swagger.json from your browser.

### swagger.json
The swagger.json doesn't generate a file on your file system. 
It's just a resource like any other JAX-RS resource you expose via jersey. 
The basePath doesn't affect where the swagger.json is located, but it is the context root of your application.

Node.js is prerequisite for installing swagger-ui:
`curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -`
`sudo apt-get install -y nodejs`
`sudo apt-get install -y build-essential`

**6 Steps to integrate swagger into rest api: Setup using jersey**

1. Add dependencies to build.gradle 

``` groovy
compile group: 'io.swagger', name: 'swagger-jersey2-jaxrs', version: '1.5.12'
compile group: 'javax.servlet', name: 'servlet-api', version: '2.5'
```

2. Swagger resource classes

In order to integrate swagger-core with your application we need to add swagger resource classes
to custom Application subclass.

```java
Set<Object> resourceObjs = new HashSet<Object>();
resourceObjs.add(new ResourceClass());
resourceObjs.add(new ApiListingResource()); // swagger resource class
resourceObjs.add(new SwaggerSerializers()); // swagger resource class
RESTApplication restApplication = new RESTApplication(resourceObjs);
ResourceConfig resourceConfig = ResourceConfig.forApplication(restApplication);
```

3. Configure and initialize the Swagger definition within your application

``` java
//Swagger bootstrap

BeanConfig beanConfig = new BeanConfig();
beanConfig.setTitle("SWAGGER REST API");
beanConfig.setDescription("Description");
beanConfig.setVersion("1.0.2");
beanConfig.setSchemes(new String[]{"http"});
beanConfig.setHost("localhost:9797");
beanConfig.setBasePath("");
beanConfig.setResourcePackage("resourceImpl");
beanConfig.setScan(true);
```
swagger.json is generated at the end of this step at this location:
`// swagger json url: http://localhost:9797/swagger.json`

4. Add CORS support 

We need to add CORS suppport on the server side for accepting requests.
Use jersey filters to add these header to your response objects.

``` java
responseContext.getHeaders().add("Access-Control-Allow-Origin","*");
responseContext.getHeaders().add("Access-Control-Allow-Methods","POST, GET, DELETE, PUT, OPTIONS");
responseContext.getHeaders().add("Access-Control-Allow-Headers","Content-Type, api_key, Authorization, x-requested-with, Total-Count, Total-Pages, Error-Message");
responseContext.getHeaders().add("Access-Control-Max-Age","1800");
```
        
5. Load swagger UI

Clone the git directory https://github.com/swagger-api/swagger-ui.git or download zip. Run the index.html file from /dist folder

6. Load your swagger.json 

Replace swagger.json url into the URL in place of default petstore URL.

Visualize your REST API documentation and start making REST calls.
 
Cheers! 

