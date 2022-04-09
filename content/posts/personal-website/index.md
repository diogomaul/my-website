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

As any "not a web developer" person, I started looking for HTML templates and other things like this. After testing 2 or 3 alternatives, I really liked how this HUGO framework works. It basically provides you with the website strucuture and you just need to create the sections (YAML files) that you want and go on from there adding the content and some customization.

So what's HUGO after all, on their own words, "Hugo is a fast and modern static site generator written in Go, and designed to make website creation fun again." If you want to know more about it, here you go:

https://gohugo.io/about/what-is-hugo/

So let's get started. You'll see that there are always more than oneor two ways to get to the same result, but I'll focus on what I did to get where I'm now, typping this post.

### 1. Installing Chocolatey 
Yes, a tool you need to install first in order to get the tool you want, funny right? Welcome to IT.

Chocolatey is a package manager that will help you downloading Hugo (and many other things you might need for future projects, so it's a cool tool to have installed anyways) 

The easiest way to install it is using the individual installation step, following these 5 easy steps:

##### a. First, run Powerhsell (or the new Windows Terminal) as an administrator.
  * Right-click and select Run as Adminsitrator

##### b. Then, run the following command. (Important Note: This will set your powershell execution policy to ByPass, you can read more here: https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.2)

```
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

```

##### c. Finally, wait for the command to complete a test if chocolatey is installed running

```
choco -?
```

### 2. Installing HUGO

All right, now with Chocolatey out of the way, we can start doing some business here. Depending on which OS you are using, the options will vary a bit, but this is what worked as a charm for me.

To install HUGO, all you need to do is running the following Chocolatey command line:

```
choco install hugo -confirm
```

Beatiful, eh?

All right, now let's create our default website and publish it! Ah yes, we are going to publish it to Azure and you will have this online in just a few minutes from now. This is going to be awesome!

##### a. Still in the powershell/windows terminal shell, run the Hugo CLI to create a new app.
```
hugo new site static-app
```

##### b. Navigate to the newly created app.
```
cd static-app
```

##### c. Initialize a Git repo.
```
git init
```

##### d. Ensure that your branch is named main.
```
git branch -M main
```

Sources:
https://chocolatey.org/install#individual
https://gohugo.io/getting-started/installing/
https://docs.microsoft.com/en-us/azure/static-web-apps/publish-hugo

