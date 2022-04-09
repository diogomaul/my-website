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

1. Installing Chocolatey 
  * (yes, a tool you need to install first in order to get the tool you want, funny right? Welcome to IT).

Chocolatey is a package manager that will help you downloading Hugo (and many other things you might need for future projects, so it's a cool tool to have installed anyways) 

I did the individual installation on my laptop, following these 5 easy steps:
https://chocolatey.org/install#individual


2. Installing HUGO

Depending on which OS you are using, the options will vary a bit.

With the tool choosen, I went ahead for the installation:
  https://gohugo.io/getting-started/installing/

In summary, with chocolatey installed, all you need to do to install HUGO is running the following command line:
```
choco install hugo -confirm
```

With Hugo installed, I moved to another doc, from Microsoft this time, that helped me starting the website and publishing it on Azure, using a free static site app.

https://docs.microsoft.com/en-us/azure/static-web-apps/publish-hugo

a. Open a terminal:
Run the Hugo CLI to create a new app.
```
hugo new site static-app
````

Navigate to the newly created app.

```
cd static-app
```

Initialize a Git repo.

````
git init
```

Ensure that your branch is named main.

```
git branch -M main
```
