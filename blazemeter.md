---
layout: post
title: BlazeMeter Tutorial
permalink: /blazemeter/
---

EDITING

**Pre-requisites**: Installation of CloudFoundry Tool

In this tutorial, a sample jsp application will be deployed in Bluemix. Blazemeter will be used to test the site url if it can handle multiple virtual users accessing at the same time.

#### Create a Bluemix Account or Login
1. Go to [Bluemix](https://ibm.biz/bluemixph) and signup/login.

#### Deploy an Application
1. Open a terminal, and create a new directory named `blazemeterT` in the root directory.

	```
	> mkdir blazemeterT
	> cd blazemeterT
	```
	
2. Download the war file (the war file contains the application), and move it in the `blazemeterT` directory.
3. Login to Bluemix using the cf tool by typing this to the terminal:
>Go to the path directory of `blazemeterT`. Make sure that the `dev` space was already created inside your bluemix account.
	
	```		
	> cf login -a https://api.ng.bluemix.net -s dev
	```
	
	`-a` to specify the API endpoint (`https://api.ng.bluemix.net`)
	
	`-s` to specify space name (`dev`)
	
4. You will be asked for your email and password (bluemix account).
5. Upload the sample jsp application's war file by pushing it to the cloud.

	```
	> cf push blazetutorial-<name> -m 256M -p blazemeter.war
	```
	
	`-m` to specify the memory to be allocated for the application being pushed (`256M`)
	
	`-p` to specify the file to be uploaded (`blazemeter.war`)
	
	`<name>` is for you to have a unique bluemix url
	
6. Go to your [Bluemix](https://ibm.biz/bluemixph) browser and click Dashboard from the top navigator.
7. From the Dashboard, you'll see your project `blazetutorial-<name>`. Click the Deploy button.
8. 










