---
layout: post
title: Building a personal blogging site using Jekyll in under 15 minutes
summary: Walk-through for creating this website using a Jekyll theme - Lanyon and hosted on Github pages, using Markdown and Docker for local hosting.
category: note
---

> Walk-through for creating this website using a Jekyll theme - Lanyon and hosted on Github pages, using Markdown and Docker for local hosting.

## Step 1: Clone Lanyon Repo

{% highlight js %}
// Clone the Lanyon Repo
git clone https://github.com/poole/lanyon.git
// Flush git info
rm -rfv lanyon/.git

// Rename the path to whatever you want to call your github repository
mv lanyon mywebsites
{% endhighlight %}

## Step 2: Create Github repository

Head over to [GitHub](https://github.com/new) and create a new repository.

![Create New Github Repo]({{site.baseurl}}/assets/githubRepo.png)

## Step 3: Commit to Github

Let's do an initial commit to our new repo.

{% highlight js %}
git init
git add .
git commit -am 'initial commit'

// Add your repo below
git remote add origin <your repo>
git push -u origin master
{% endhighlight %}

## Step 4: Enable GitHub Pages

From your github repo, goto settings and enable github pages. Within a few minutes you will have the URL to your website!

![Enable Github Pages]({{site.baseurl}}/assets/githubPages.png)

## Step 5: Use Docker to serve content locally

To serve your website locally before pushing your changes to github, you may use [Docker](https://www.docker.com/)

For the very first time you will have to do a build:

{% highlight js %}
docker run --env=DEBUG=true --rm --volume="/Users/purak/Desktop/mywebsite:/srv/jekyll" -it jekyll/jekyll:$JEKYLL_VERSION jekyll build
{% endhighlight %}

Once the build is complete you can run it with draft mode:

{% highlight js %}
docker run --name mydomain.com --env=DEBUG=true --rm --volume="/Users/purak/Desktop/mywebsite:/srv/jekyll" -p 4000:4000 -it jekyll/jekyll:$JEKYLL_VERSION jekyll serve --watch --drafts
{% endhighlight %}

Your website should now be hosted locally at: [http://localhost:4000](http://localhost:4000)
