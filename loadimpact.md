---
layout: post
title: Load Impact Tutorial
permalink: /loadimpact/
---

**Pre-requisites**: Installation of CloudFoundry Tool

In this tutorial, a sample jsp application will be deployed in Bluemix. 

Load Impact will be used to test the site if it can handle multiple virtual users from across the world accessing at the same time.

#### Create a Bluemix Account or Login
1. Go to [Bluemix](https://ibm.biz/bluemixph) and signup/login.

#### Deploy an Application
1. Open a terminal, and create a new directory named `loadimpact` in the root directory.

	```
	> mkdir loadimpact
	> cd loadimpact
	```
	
2. Download the [blaze.war](https://github.com/ataichi/ataichi.github.io/blob/master/downloadables/blaze.war?raw=true) file (the war file that contains the application), and move it in the `loadimpact` directory.
3. Login to Bluemix using the cf tool by typing this to the terminal:
>Go to the path directory of `loadimpact`. Make sure that the `dev` space was already created inside your bluemix account.
	
	```		
	> cf login -a https://api.ng.bluemix.net -s dev
	```
	
	`-a` to specify the API endpoint (`https://api.ng.bluemix.net`)
	
	`-s` to specify space name (`dev`)
	
4. You will be asked for your email and password (bluemix account).
5. Upload the sample jsp application's war file by pushing it to the cloud.

	```
	> cf push loadimpact-<name> -m 256M -p blaze.war
	```
	
	`-m` to specify the memory to be allocated for the application being pushed (`256M`)
	
	`-p` to specify the file to be uploaded (`blaze.war`)
	
	`<name>` is for you to have a unique bluemix url
	
6. Go to your [Bluemix](https://ibm.biz/bluemixph) browser and click Dashboard from the top navigator.
7. From the Dashboard, you'll see your project `loadimpacttutorial-<name>`. Click the Deploy button within its box.
 
>Take note of the url of the application.

Application deployment successful.

#### Binding a Service
1. From the Dashboard, click the box of the application `loadimpacttutorial-<name>`.
2. Scroll down and look for `ADD A SERVICE OR API`, click it.
3. Scroll down to bottom of the page and click the `Bluemix Labs Catalog`.
4. Enter `postgre` to the search field. Then you should see the postgresql service, click it.
5. Click create. You will be prompted to restage. Click `Restage`.
6. Open to a new browser `http://loadimpacttutorial-<name>.mybluemix.net/userlogin.jsp`. 

>Take note of the login page url.

7.Log in using either as

email: `john_doe@gmail.com` with the password: `johnjojon`.

or

email: `afemaledear@gmail.com` with the password: `doenut`. <br>
8. After logging in, take note of this url too.

#### Testing with Load Impact
1. Go to Bluemix. (While logged in) Click `Dashboard` and click `USE SERVICES OR APIS`.
2. In the search bar, type `Load`. Choose `Load Impact` under DevOps, supply a service name and click `Create`.
3. Click the `OPEN LOAD IMPACT DASHBOARD`.
4. You will be asked to enter a URL to test. Paste the login URL copied earlier from the deployed application. `http://loadimpacttutorial-<name>.mybluemix.net/BD0.jsp`
5. Put `100` to Max VUs, and 5 in Duration (mins).
6. Click the `Run test` option.
7. To see the reports, click `Tests` from the left menu. Click the name of the recent test made, and then click `View results`.

>If you are interested to know advanced testing with load impact, they have their own youtube channel that will guide you [here](https://www.youtube.com/channel/UC8ryLdIbmkVJq4Zt613oZPQ).


#### Delete the Sample Application for Housekeeping
1. Go to [Bluemix](www.ibm.biz/bluemixph).
2. Click `Dashboard`.
3. From the Applications List, click the gear icon.
4. Choose `Delete App`.
