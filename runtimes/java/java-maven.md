---
title: Java Maven
position: 3
shortdesc: Maven is essentially a project management and comprehension tool...
---

# Deploy Java Maven projects

Clever Cloud offers you to run your Java Maven projects. You can deploy this kind of project without changing your code, but running it on Clever Cloud needs some configuration files, to add parameters like your targeted container for instance.


## Overview
Maven is essentially a project management and comprehension tool and as such provides a way to help with managing:

* Builds
* Documentation
* Reporting
* Dependencies
* SCMs
* Releases
* Distribution


## About Cargo
To run your app, you can, for example, use plugins like cargo
(<a href="http://cargo.codehaus.org/Maven2+plugin">Find it here</a>).
Your application must be set to listen on the port 8080.

## Create an application

1. Create a new app by clicking on the **Add an application** button, in the headbar.
2. Select the language/framework: <figure class="cc-content-img"><img src="/assets/images/select-lang.png"></figure>
3. Select the scalability options: <figure class="cc-content-img"><img src="/assets/images/select-scalab.png"/></figure>
3. Enter your application's name and description, choose your deployment zone and click "Create".
<figure class="cc-content-img"><img src="/assets/images/choose-name.png"/></figure>
5. *Optional*: <a href="/addons/add-an-addon/">add an add-on</a>

## Necessary information

The `clevercloud/maven.json` (maven.json file in clevercloud folder which is at the root of you application) file must contain the _goal_ field to indicate how to start your application:

```javascript
  {
    "deploy": {
      "goal": "yourgoal"
    }
  }
```

An example of what can be found as a goal value is:  

```haskell
"-Dtest.active=false -Dexec.mainClass=\"com.example.Main\" assembly:jar-with-dependencies exec:java"
```

## Optional configuration

The full configuration can look like the following:

```haskell
{
  "build": {
    "type": "<string>",
    "goal": "<string>"
  },
  "deploy": {
    "goal": "<string>"
  },
  "hooks": {
     "postDeploy": "<string>"
  }
}
```
You can use the following properties:

* ``build``
    * ``"type"`` can be ``"maven"``, ``"gradle"`` or ``"ant"``.
    * ``"goal"`` is the target you want to use to build your project.
* ``deploy``
    * ``"goal"`` the goal/target and options you want to execute to
		  deploy/run you project. (This one is mandatory.)
* ``hooks``
    * ``postDeploy`` execute a custom script after the deployment. Some frameworks or custom applications might require bootstrapping before the application may run.
You can achieve this by creating a custom script with your commands and adding the associated file name.

## Deploy on Clever Cloud

Application deployment on Clever Cloud is via Git. Follow [these steps](/clever-cloud-overview/add-application/) to deploy your application.
