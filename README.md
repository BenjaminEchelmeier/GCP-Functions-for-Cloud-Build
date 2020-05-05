# GCP Functions for Cloud Build

This is a simple template for basic CI/CD using Google Cloud Platform's Source Repositories, Cloud Build, and Cloud Functions. 

<details>
<summary>GUIDE</summary>
<br>
<!-----
NEW: Your output is on the clipboard!

NEW: Check the "Supress top comment" to remove this info from the output.

Conversion time: 3.878 seconds.


Using this Markdown file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β23
* Tue May 05 2020 11:09:24 GMT-0700 (PDT)
* Source doc: Copy of Deploying Google Cloud Functions in Python with Cloud Build
* Tables are currently converted to HTML tables.
* This document has images: check for >>>>>  gd2md-html alert:  inline image link in generated source and store images to your server.
----->


<p style="color: red; font-weight: bold">>>>>>  gd2md-html alert:  ERRORs: 0; WARNINGs: 0; ALERTS: 16.</p>
<ul style="color: red; font-weight: bold"><li>See top comment block for details on ERRORs and WARNINGs. <li>In the converted Markdown or HTML, search for inline alerts that start with >>>>>  gd2md-html alert:  for specific instances that need correction.</ul>

<p style="color: red; font-weight: bold">Links to alert messages:</p><a href="#gdcalert1">alert1</a>
<a href="#gdcalert2">alert2</a>
<a href="#gdcalert3">alert3</a>
<a href="#gdcalert4">alert4</a>
<a href="#gdcalert5">alert5</a>
<a href="#gdcalert6">alert6</a>
<a href="#gdcalert7">alert7</a>
<a href="#gdcalert8">alert8</a>
<a href="#gdcalert9">alert9</a>
<a href="#gdcalert10">alert10</a>
<a href="#gdcalert11">alert11</a>
<a href="#gdcalert12">alert12</a>
<a href="#gdcalert13">alert13</a>
<a href="#gdcalert14">alert14</a>
<a href="#gdcalert15">alert15</a>
<a href="#gdcalert16">alert16</a>

<p style="color: red; font-weight: bold">>>>>> PLEASE check and correct alert issues and delete this message and the inline alerts.<hr></p>



## Deploying Google Cloud Functions in Python with Cloud Build


### A tutorial by Benjamin Echelmeier


#### Introduction

In this tutorial, we’ll be utilizing the Google Cloud Platform to deploy Cloud Functions in Python using Cloud Build for Continuous Integration or Continuous Deployment. All the technologies used here should be covered in depth, but there is an assumption of basic Python and a degree of understanding cloud technology. 

If you are unfamiliar with Cloud Functions, check out [this quickstart](https://cloud.google.com/functions/docs/quickstart-python) from the Google Cloud documentation; it will guide you through a basic function that we will use to explore Cloud Build.


## 


## Setting up a new Google Cloud Project and Repository

To begin, of course, we’ll need to sign in to (or [create](https://cloud.google.com/)) our Google Cloud account and [create a new project](https://console.cloud.google.com/projectcreate). I’ll be naming mine “my Py Functions”.



<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/Copy-of0.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/Copy-of0.png "image_tooltip")


After the project has been created, head over to your Source Repositories and add a repository.



<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/Copy-of1.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/Copy-of1.png "image_tooltip")




<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/Copy-of2.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/Copy-of2.png "image_tooltip")


 

Go ahead and _Create new Repository _with your chosen name inside your project. 



<p id="gdcalert4" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/Copy-of3.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert5">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/Copy-of3.png "image_tooltip")


I’ll be pushing a clone of [this repository](https://github.com/BenjaminEchelmeier/GCP-Functions-for-Cloud-Build), which contains a slightly modified version of the function mentioned in the introduction, and following the instructions to _Push code from a local Git repository_. (Feel free to fill the repository in whatever way is familiar to you)



<p id="gdcalert5" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/Copy-of4.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert6">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/Copy-of4.png "image_tooltip")


After refreshing our browser, we should have a repository similar to the one pictured below. We have our README and our .py files for our function, which should be familiar, and our cloudbuild.yaml, which is shown and explained later in the “Understanding and Editing Cloudbuild Files” section.



<p id="gdcalert6" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/Copy-of5.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert7">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/Copy-of5.png "image_tooltip")



## Setting up our Cloud Build

Now that we have our dummy code (or other code, if you’ve already customized things for your project) set up in our repository, lets hop back to the _Cloud Console _and navigate to our _Cloud Build _API. 



<p id="gdcalert7" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/Copy-of6.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert8">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/Copy-of6.png "image_tooltip")




Go ahead and _enable_ the API, and navigate to the _Triggers_ menu on the sidebar and _Create a Trigger_.



<p id="gdcalert8" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/Copy-of7.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert9">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/Copy-of7.png "image_tooltip")




Fill in the _name _and _description_, and select the _Push to a branch_ Event to invoke the trigger. Select your repository and your branch (I picked master), and, if you’d like, you can filter out changes to certain files, like my README, so as to avoid triggering unnecessary builds. 



<p id="gdcalert9" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/Copy-of8.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert10">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/Copy-of8.png "image_tooltip")




The defaults should lead directly to your cloudbuild.yaml file. Then we are going to select _add variable_. Those who studied our [cloudbuild.yaml](https://github.com/BenjaminEchelmeier/GCP-Functions-for-Cloud-Build/blob/master/cloudbuild.yaml) file, might recognize the _FUNC_NAME variable. Hopefully it is fairly obvious that the value here will be the name of your Cloud Function. Once this is all to your liking, click _create_.



<p id="gdcalert10" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/Copy-of9.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert11">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/Copy-of9.png "image_tooltip")




Now, we have our trigger, but before the build can run properly we will need to grant permission to build Cloud Functions. Go to _Settings_ on the side bar and _enable_ Cloud Functions, Firebase, and Service Accounts.



<p id="gdcalert11" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/Copy-of10.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert12">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/Copy-of10.png "image_tooltip")


We can now go back to our trigger and click to _run trigger_. This can also be done by pushing a change to our repo.



<p id="gdcalert12" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/Copy-of11.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert13">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/Copy-of11.png "image_tooltip")


You should get a notification of your running build, or you can go to the _history_ tab and select the running build. You can watch magic happen and, hopefully, after a few minutes you have a successful build. If your build failed, try and troubleshoot based on the error message; they tend to be fairly helpful.



<p id="gdcalert13" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/Copy-of12.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert14">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/Copy-of12.png "image_tooltip")


Once your build has succeeded, use the search bar to hop over to your Cloud Functions. There you should find your newly created Cloud Function.



<p id="gdcalert14" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/Copy-of13.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert15">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/Copy-of13.png "image_tooltip")


Congratulations! You just made a CD build for your Cloud Function!


## Customizing and Going Further


### Understanding and Editing Cloudbuild Files

Google has good documentation on how to make a cloudbuild file [here](https://cloud.google.com/cloud-build/docs/build-config), and the documentation should be more than sufficient for making your own cloudbuild file to automate your needs. As you want to adapt and customize (or build from scratch), please look to these docs. They also have a [guide to building a basic configuration file](https://cloud.google.com/cloud-build/docs/configuring-builds/create-basic-configuration) to get new users started, but I’ll be providing a slightly more concrete breakdown of a simple file here. 

First, let's take a look at the cloudbuild.yaml file used in this tutorial.


```
steps:
- name: 'gcr.io/cloud-builders/gcloud'
  args:
    [ 'functions',
      'deploy',
      '$_FUNC_NAME',
      '--runtime',
      'python37',
      '--entry-point',
      'hello_world',
      '--source',
      'https://source.developers.google.com/projects/$PROJECT_ID/repos/$REPO_NAME/ moveable-aliases/$BRANCH_NAME/paths//',
      '--trigger-http',
      '--allow-unauthenticated'
    ]
```


Note that if you want to copy this text to create your own file, you must remove the space in the url. 

Practically any cloudbuild file will have a “steps,” “name,” and “args” field. “Steps” demarks that the contained will be the build steps, as opposed to, for instance, “options” or “tags.” “Name” initiates a step by pointing to a [cloud builder](https://cloud.google.com/cloud-build/docs/cloud-builders), and “args” are the meat of the file, containing the arguments passed to the builder.

Our builder is, of course, [gcloud](https://cloud.google.com/sdk/gcloud/), the primary CLI for GCP, and our arguments are a single-line [functions deploy](https://cloud.google.com/sdk/gcloud/reference/functions/deploy) argument. Manually entered into the gcloud CLI it would look like:


```
gcloud functions deploy $_FUNC_NAME --runtime python37 --entry-point hello_world --source https://source.developers.google.com/projects/$PROJECT_ID/repos/$REPO_NAME/moveable-aliases/$BRANCH_NAME/paths// --trigger-http --allow-unauthenticated
```


	Obviously, the $VARIABLES look a bit out of place in gcloud; those are a terrific tool that allows for far more flexibility in our config files. Our _FUNC_NAME is, of course, the variable we defined, while the others (notably lacking the preceding underscore) are defaults. Questions about any arguments here will likely be answered by referencing the appropriate flag [here](https://cloud.google.com/sdk/gcloud/reference/functions/deploy).


### Building for Multiple Branches

 One of the best uses of Cloud Build is the ability to integrate CD into various branches, allowing for quicker feedback and collaboration. I’ll take a brief moment here to create a “dev” branch that might be used to test our potentially unstable changes before we merge with the master branch and, thereafter, our primary function. 

Let us return to our local git repo and make our dev branch in the terminal.


```
git checkout -b dev
```


	Go ahead and add some text to the return statement before adding, committing, and pushing to your cloud repository.


```
git add .
git commit -m 'updated main.py with potentially unstable text'
git push --set-upstream google dev
```


	

Now that we have our branch, we can go ahead and create a new trigger for it. This should be quite similar to our previous trigger, but with a new name, branch, and _FUNC_NAME variable.



<p id="gdcalert15" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/Copy-of14.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert16">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/Copy-of14.png "image_tooltip")


<p id="gdcalert16" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/Copy-of15.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert17">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/Copy-of15.png "image_tooltip")


	That’s all it takes! _Create_ your function and _run trigger_ or push a change to your dev branch, and then go confirm that your new function has been created, complete with the new changes. This can and should be duplicated into a greater number of branches, however many suits your needs. 


## Conclusion

	Congratulations! You’ve successfully created a functioning CI/CD environment with GCP cloud functions. This is, of course, just an entry point, and I encourage you to continue exploring the Console and Documentation provided by Google, both for any questions and for further application. 

I’ll finish by giving credit to Clemens Siebler and his similar post, [Deploying Azure Functions in Python with Azure DevOps](https://clemenssiebler.com/deploy-azure-functions-python-azure-devops/), which introduced me to the world of CI/CD and serves as inspiration for this guide. If you’re looking to do something very similar in Azure, go check out his post.

</details>
