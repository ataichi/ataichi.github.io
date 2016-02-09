---
layout: post
title: BlazeMeter Tutorial
permalink: /blazemeter/
---

EDITING

In this tutorial, an sample jsp application will be deployed in Bluemix. Blazemeter will be used to test the site url if it can handle multiple virtual users accessing at the same time.

#### Create a Bluemix Account or Login
1. Go to [Bluemix](https://ibm.biz/bluemixph) and signup/login.

#### Deploy an Application
1. Open a terminal, and create a new directory named `blazemeterT` in the root directory.
	```text		
	> mkdir blazemeterT
	> cd blazemeterT
	```
2. Download the war file (the war file contains the application), and move it in the `blazemeterT` directory.
3. Login to Bluemix using the cf tool by typing this to the terminal:
* Go to the path directory of `blazemeterT`. Make sure that the `dev` space was already created inside your bluemix account.
	```text		
	> cf login -a https://api.ng.bluemix.net -s dev
	```
-a to specify the API endpoint (https://api.ng.bluemix.net)
-s to specify space name (dev)
4. 

