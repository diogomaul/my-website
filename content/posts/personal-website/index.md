---
title: "How to create your personal portfolio website"
date: 2022-04-04T09:45:23+06:00
#hero: images/posts/personal-website/hero.jpg
description: How to create a personal portfolio website using Hugo
theme: Toha
menu:
  sidebar:
    name: Personal Website 
    identifier: personal-website
    weight: 500
---

A personal website is something that I've been meaning to have for a while now... and it's finally here! 

So for this first post I thought why not talk about my experience setting this up and maybe help someone else that is in the same boat as me (not a web developer), but wants to have a personal, portfolio, resume or blogging website.

I might tell you that this post is going to be full of surprises, although we are creating a basic website, we are taking this opportunity to learn and see in action some cool DevOps concepts like Continuous Integration and Continuous Delivery using Azure and GitHub. This is going to be awesome!

As any "not a web developer" person, I started looking for HTML templates and other things like this. After testing 2 or 3 alternatives, I really liked how this HUGO framework works. It basically provides you with the website strucuture and you just need to create the sections (YAML files) that you want and go on from there adding the content and some customization.

So what's HUGO after all, on their own words, "Hugo is a fast and modern static site generator written in Go, and designed to make website creation fun again." If you want to know more about it, here you go:

https://gohugo.io/about/what-is-hugo/

So let's get started. You'll see that there are always more than oneor two ways to get to the same result, but I'll focus on what I did to get where I'm now, typping this post.

#### 1. Installing Chocolatey 
Yes, a tool you need to install first in order to get the tool you want, funny right? Welcome to IT.

Chocolatey is a package manager that will help you downloading Hugo (and many other things you might need for future projects, so it's a cool tool to have installed anyways) 

The easiest way to install it is using the individual installation step, following these 5 easy steps:

###### First, run Powerhsell (or the new Windows Terminal) as an administrator.
  * Right-click and select Run as Adminsitrator

###### Then, run the following command. (Important Note: This will set your powershell execution policy to ByPass, please check the sources at the end to learn more about it)
```
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

```

###### Finally, wait for the command to complete a test if chocolatey is installed running
```
choco -?
```

#### 2. Installing HUGO

All right, now with Chocolatey out of the way, we can start doing some business here. Depending on which OS you are using, the options will vary a bit, but this is what worked as a charm for me.

To install HUGO, all you need to do is running the following Chocolatey command line:
```
choco install hugo -confirm
```

Beatiful, eh?

All right, now let's create our default website and publish it! Ah yes, we are going to publish it to Azure and you will have this online in just a few minutes from now. Can you believe it?

###### a. Still in the powershell/windows terminal shell, run the Hugo CLI to create a new app.
```
hugo new site static-app
```

###### b. Navigate to the newly created app.
```
cd static-app
```

###### c. Initialize a Git repo.
```
git init
```

###### d. Ensure that your branch is named main.
```
git branch -M main
```

###### e. Next, add a theme to the site by installing a theme as a git submodule and then specifying it in the Hugo config file.

```
git submodule add https://github.com/hugo-toha/toha themes/toha
echo 'theme = "toha"' >> config.yaml
```

###### f. Add the changed file to the git staging area
```
git add -a
```

###### g. Commit the changes
```
git commit -m "initial commit"
```

Now your changes are commited to your local repository and we will push them to the origin on Git Hub. Git is source control technology widely adopted by companies and people around the world and GitHub is the biggest player in this field.

#### Push your application to GitHub

OK, maybe this is not what you were expecting to see, we could definitely publish our website.

First, let's make sure we have a repository to push to. That's important, right?

##### If you already have a GitHub account:
If you have a github account and are already loogen in, you can use https://github.com/new to quickly go the new repo page. 

##### If you don't have a GitHub account:
Otherwise, the same link will guide you through the account creation process, pretty straight forward.

All right, once in the new repository creation page, name it my-website.

Now back to your command line tool, run the following command to add the github repo you just created as your origin. (don't forget to add your user name in the YOUR_USER_NAME part of the below code)
```
git remote add origin https://github.com/<YOUR_USER_NAME>/my-website
```

Finally, let's push your code to GItHub:
```
git push --set-upstream origin main
```

#### Deploy your website to a web app on Microsoft Azure

So here we are, the last step of our journey.

###### Create the application

Navigate to the Azure Portal https://portal.azure.com/ 
* Select Create a Resource
* Search for Static Web Apps
* Select Static Web Apps
* Select Create

##### On the Basics tab, enter the following information:

   | Property | Value |
   | ----- | --- |
   | Subscription | Your Azure subscription name |
   | Resource | any name for your resource group |
   | Name | my-website |
   | Plan type |	Free |
   | Region for Azure Functions API and staging environments |	Select a region closest to you |
   | Source | GitHub |
   | Click | Sign in with GitHub and authenticate with GitHub |

The result should be something like this:

{{< img src="/posts/personal-website/create-static-app.png" >}}

##### Now let's our GitHub repository to the Static WebApp:

   | Property | Value |
   | ----- | --- |
   | Organization | Select your desired GitHub organization |
   | Repository | Select my-website |
   | Branch |	Select main |
   | In the Build Details section | select Hugo from the Build Presets drop-down and keep the default value |

Again, something like this:

{{< img src="/posts/personal-website/git-hub-deploy.png" >}}

###### Review and create
* Select the Review + Create button to verify the details are all correct.
* Select Create to start the creation of the App Service Static Web App and provision a GitHub Actions for deployment.
* Once the deployment completes click, Go to resource.
* On the resource screen, click the URL link to open your deployed application. 

{{< img src="/posts/personal-website/go-to-your-site.png" >}}

You'll notice that the default URL won't be using a custom domain, such as myname.com, but an azurestaticapps.net instead. In my next post, I'll go step by step on how to register a domain and use it in your website. 

Regarding the deployment, you may need to wait a minute or two for the GitHub Action to complete it. Another nice thing is that Azure itself creates the YAML file with the job that takes care of the web-app deployment for you. You can find the file in the .github/workflows folder of your repo.

Also, you can check check the deployment status in the actions tab of your GitHub Repository:

{{< img src="/posts/personal-website/git-hub-actions.png" >}}

That would do it for a first post, following this steps you should be able to set up a basic Hugo Static Web App with the Toha (or any other theme). Once you have it set up, you can follow the theme instructions for all the required customizations.

Sources:
https://chocolatey.org/install#individual /n
https://gohugo.io/getting-started/installing \n
https://docs.microsoft.com/en-us/azure/static-web-apps/publish-hugo
https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.2

