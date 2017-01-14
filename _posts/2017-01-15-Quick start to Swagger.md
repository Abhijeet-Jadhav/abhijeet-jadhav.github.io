---
layout: post
title: Quick start to Swagger
image: /img/abhi_1.jpg
tags: [swagger, rest api documentation, jersey]
---


# Swagger Notes
Swagger is used to generate the swagger from an existing API.

The swagger.json doesn't generate a file on your file system. 
It's just a resource like any other jax-rs resource you expose via jersey. 
the basePath doesn't affect where the swagger.json is located, but it is the context root of your application.

##Swagger-core 
Allows you to generate a Swagger spec from the code. And that’s the json file generated swagger.json .
'/' is the context root of my jersey resources.

##Swagger-UI
The next step is to take swagger-ui and integrate it into your code for the actual display.
Setting it up is fairly easy. 
It’s a static set of pages you need to host like any web app, 
and configure it to load the swagger.json from your app.

dependency = node.js
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
sudo apt-get install -y nodejs
sudo apt-get install -y build-essential



