---
layout: post
title: Quick start to Swagger
image: /img/abhi_1.jpg
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
It's just a resource like any other jax-rs resource you expose via jersey. 
the basePath doesn't affect where the swagger.json is located, but it is the context root of your application.

'/' is the context root of my jersey resources.

dependency = node.js
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
sudo apt-get install -y nodejs
sudo apt-get install -y build-essential

**4 Steps to integrate swagger into rest api:**

1. setup using jersey

https://github.com/swagger-api/swagger-core/wiki/Swagger-Core-Jersey-2.X-Project-Setup-1.5

at the end of this step swagger.json will be generated

2. clone the git directory 
run the index.html file

3. load your swagger.json location into the URL

4. add CORS support on the server side by sending requests

make rest calls from UI

