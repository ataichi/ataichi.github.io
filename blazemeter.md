---
layout: post
title: BlazeMeter Tutorial
permalink: /blazemeter/
---

EDITING

**Pre-requisites**: Installation of CloudFoundry Tool

In this tutorial, a sample jsp application will be deployed in Bluemix. 

Blazemeter will be used to test the site url if it can handle multiple virtual users accessing at the same time.

#### Create a Bluemix Account or Login
1. Go to [Bluemix](https://ibm.biz/bluemixph) and signup/login.

#### Deploy an Application
1. Open a terminal, and create a new directory named `blazemeter` in the root directory.

	```
	> mkdir blazemeter
	> cd blazemeter
	```
	
2. Download the [blaze.war](https://github.com/ataichi/ataichi.github.io/blob/master/downloadables/blaze.war?raw=true) file (the war file that contains the application), and move it in the `blazemeter` directory.
3. Login to Bluemix using the cf tool by typing this to the terminal:
>Go to the path directory of `blazemeter`. Make sure that the `dev` space was already created inside your bluemix account.
	
	```		
	> cf login -a https://api.ng.bluemix.net -s dev
	```
	
	`-a` to specify the API endpoint (`https://api.ng.bluemix.net`)
	
	`-s` to specify space name (`dev`)
	
4. You will be asked for your email and password (bluemix account).
5. Upload the sample jsp application's war file by pushing it to the cloud.

	```
	> cf push blazetutorial-<name> -m 256M -p blaze.war
	```
	
	`-m` to specify the memory to be allocated for the application being pushed (`256M`)
	
	`-p` to specify the file to be uploaded (`blaze.war`)
	
	`<name>` is for you to have a unique bluemix url
	
6. Go to your [Bluemix](https://ibm.biz/bluemixph) browser and click Dashboard from the top navigator.
7. From the Dashboard, you'll see your project `blazetutorial-<name>`. Click the Deploy button within its box.
 
>Take note of the url of the application.

Application deployment successful.

#### Binding a Service
1. From the Dashboard, click the box of the application `blazetutorial-<name>`.
2. Scroll down and look for `ADD A SERVICE OR API`, click it.
3. Scroll down to bottom of the page and click the `Bluemix Labs Catalog`.
4. Enter `postgre` to the search field. Then you should see the postgresql service, click it.
5. Click create. You will be prompted to restage. Click `Restage`.
6. Open to a new browser `http://blazetutorial-<name>.mybluemix.net/userlogin.jsp`. 

>Take note of the login page url.

7.Log in using either as

email: `john_doe@gmail.com` with the password: `johnjojon`.

or

email: `afemaledear@gmail.com` with the password: `doenut`. 
8. After logging in, take note of this url too.

#### Test with BlazeMeter
1. Go to Bluemix. (While logged in) Click `Dashboard` and click `USE SERVICES OR APIS`.
2. In the search bar, type `BlazeMeter`. Choose `BlazeMeter` under DevOps, supply a service name and click `Create`.
3. Wait for it.. until the `OPEN BLAZEMETER DASHBOARD` appears, then click it. You will be redirected to the blazemeter site.
4. Click `Add URL List Test`.
5. Type `Login page` in the http label field. This will be the name of your page in your report. Choose `GET` from the dropdown.
6. Paste the login URL copied earlier from the deployed application in the `Enter request URL` field. (`http://blazetutorial-<name>.mybluemix.net/userlogin.jsp`)
7. Select any from the location in the Load Scenario Properties area. This will indicate where would the virtual users being created be imitated to be coming from.
8. Check the Sandbox mode box. Notice the change in the range of maximum virtual users allowed to be tested.

>Sandbox mode is a security mechanism that protects live servers and data from being damaged. So if you're going to test a website with live data in it, please check the sandbox mode to lighten the load being pushed by blazemeter.

9. Uncheck the sandbox mode.
10. Adjust the virtual users to 50. (Since it's a free plan, it's only up to 50)
11. Let all other values be untouched.
12. Add another url in the Http Urls Test by clicking the + symbol.
13. Enter an http label called as `View Account Page`.
14. In the enter request url field, put `http://blazetutorial-<name>.mybluemix.net/BD0.jsp`. Let the `GET` remain as `GET`.
15. Click `Save` in the top right corner of the page.
16. It will not be saved unless you specify a name of the test.
17. Name your test as `E banking` then click the `Save` button again.
18. In the left of `E banking`, click the green play button.
19. A Launch Test message will be displayed, click the `Launch Servers` button.
20. While the test runs, it displays a real time generated reports. Wait for your test to finish and done.
21. Examine reports especially the `Load Report`. Unclick `ALL` from the Labels and click `View Account Page`. Hover to one of the lines, it displays how long it took for the page to load given the number of virtual users created to be accessing it. 










