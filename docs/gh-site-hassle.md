---
layout: default
title: "The Hassle Of Creating This Site"
permalink: /gh-site-hassle
tags: "article"
---

# The Hassle Of Creating This Site
## Plan
Create a GitHub pages site, and add articles about the tech stuff that I am involved with.

### Progress Thu 20 Nov 2025 21:11
#### Summary of work done today
1. Created a new repository called [glum-giggle](https://github.com/aeconoclast/glum-giggle) as suggested by the [Quickstart guide](https://docs.github.com/en/pages/quickstart).
    - ***A new repository is required to publish a GitHub Pages site. Unfortunately, when one attempts to create a new repo, GitHub asks to give a new name. So I gave the name as glum-giggle. This was the first problem with this exercise.***
2. The minimal theme used in the Quickstart Guide linked back to repo glum-giggle which I didn't want.
3. I changed to the Cayman theme which still showed the link to glum-giggle.
4. The only way to get rid of the link seems to customize the Jekyll theme. To do that, I
    - Installed ruby.
    - Created a local copy of the repo.
5. By that time, GitHub started showing this warning: *"GitHub users are now required to enable two-factor authentication as an additional security measure. Your activity on GitHub includes you in this requirement. You will need to enable two-factor authentication on your account before January 04, 2026, or be restricted from account actions."*

#### Next Steps

1. Improve the added content.
2. Finish Jekyll customization, and get the GitHub pages site up and running, this weekend. To do this, follow the long series of instructions here: https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll
3. Set up 2FA by installing the GitHub app.

Tue 9 Dec 2025 22:44
---
Planned on 3 hours to get this done. Took 4 hours and it is still incomplete. Summary of what I had to go through.

As planned, I followed instructions [here](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll)
It was step 12 that took the longest time. It failed - ```bundle install``` - due to different reasons
- Permissions to a file in /var
- A package called *bigdecimal* not being available.
- The version of ruby not working for that version of Jekyll

The only to resovle these issues was by installing rvm which installs Ruby. So I installed ruby 3.4.7 to get GitHub Pages to work.
As an aside, I found that Ruby releases are all over the place - there seems to be no obvious rule of versioning: https://www.ruby-lang.org/en/downloads/releases/

Once that was done, I found the site didn't open the page. I then followed instructions [here](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/adding-content-to-your-github-pages-site-using-jekyll#adding-a-new-page-to-your-site). Working with the yaml file, adding the right markdown for the [Frontmatter](https://jekyllrb.com/docs/front-matter/) let me get the site up and running here: https://aeconoclast.github.io/glum-giggle/free-mouse-clicks

There are still issues with it:
1. The home page (https://aeconoclast.github.io/) does not open.
2. The glum-giggle (https://aeconoclast.github.io/glum-giggle) link does not work.
2. The theme looks non-existent.

Somehow, the Jekyll site works. The above issues must be resolved before publicizing it. The build shows this issue: *Layout 'page' requested in free-mouse-clicks.md does not exist.*

Tue 23 Dec 2025 01:06
---
To get the home page (https://aeconoclast.github.io/glum-giggle) to work, I changed the publishing source from the /docs directory to the /root directory. That allows the home page to function but the jekyll rendering and theme don't work. I added an index.html file to the root directory so the page is not empty.

#### Next Steps

1. I have to find a way to make the home page work.
2. After the home page renders properly, link the free mouse clicks page from the home page.

Wed 24 Dec 2025 01:17
---
I couldn't find a way to make the site work as intended. Publishing from /docs does not allow the home page (index.html) to render as a Jekyll site. I changed index.html to index.md and added index.md in _config.yml to the *include* tag. Didn't work.

In the end, I gave up with trying to make the site work smoothly with Jekyll. The problem was that Jekyll would not render the index.html file or the home page would result in a 404 error. Then there were the configuration issues where I changed the *baseurl* tag from /docs to / and then change the publishing source from /docs to /root. It became a crapshoot for hours.

#### Next Steps

1. Home page stays in custom index.html with Jekyll interference.
2. Home page links to all the other pages in the Pages site.

The home page works when the publishing source is /root, but Jekyll rendering completely breaks down. No theme, so no markdown-based content.
To stay with Jekyll, the only other solution I can think of is to delete the site and create it from scratch again.

Wed 24 Dec 2025 14:47
---
### The Origin of all Problems
When I named the repository, I didn't know that its name meant so much for GitHub Pages. I named it *glum-giggle* just for fun, since it was only going to host the text of my GitHub blog. That created all these problems.

GitHub wants me to name the repository as *aeconoclast.github.io*, so it can host the Pages site at https://aeconoclast.github.io. If have to host the site at glum-giggle.com, then I have to create a DNS record, and do quite a few other things, effectively opening a new can of worms.

Right now, publishing from /docs opens the [free-mouse-clicks](https://aeconoclast.github.io/glum-giggle/free-mouse-clicks) page, but that page has a link to https://aeconoclast.github.io/glum-giggle (the *home page*) that does not work. I'll spend a bit more time to figure out how to make that home page link work. Changing _config.yml, or the Gemfile or index.html does not make it work. Also, I couldn't figure out how to remove that home page link. But it is better to have it there, and make it work.

If I publish from /root, both pages work, but I'd have to write all the html manually. Publishing from /docs allows me to write only markdown which the Jekyll Gem processes to create an html file for the site.

#### Next Step

Create a new repo with name aeconoclast.github.io.

Thu 25 Dec 2025 00:59
---
So I created a new repository called aeconoclast.github.io, using the Quickstart guide. The page at https://aeconoclast.github.io works, uses the tactile Jekyll theme. This means I now have 2 repositories from where I am publishing to GitHub Pages: aeconoclast.github.io and glum-giggle.
Unfortunately, the pages from glum-giggle became plain html after a few changes to _config.yml to connect them to aeconoclast.github.io. There is probably a theme mixup that is causing this.

The question now is what to do about this scenario.Configuring a custom domain seems to be too much of a hassle right now. Especially, since I still have to get the theme to work. Or write my own custom HTML and CSS.
Thinking over this, I could use these pages as below:
1. https://aeconoclast.github.io is the about page, the contact page. It has something about me and it links to glum-giggle.
2. https://aeconoclast.github.io/glum-giggle is the GitHub blog page, the page that links to the actual blog content.
3. https://aeconoclast.github.io/glum-giggle/free-mouse-clicks is the first blog page.

Sat 27 Dec 2025 07:02
---
Decided to try to use my own custom HTML and CSS. Asked an AI bot to give me a sample, and used it.
Adding an AI-generated index.html file with CSS in styles.css, and then a link to https://aeconoclast.github.io/free-mouse-clicks.html works so well!

Unfortunately, this might be actually too much work for a blog. All html and css would have to be written and maintained by me. I'd spend more time working with the system than actually adding the content. So back to GitHub Pages, and its themes it is.

#### Problems with GitHub Pages

1. There is no reason to have the gh-pages branch. Nobody wants to publish from a separate branch.
2. The [testing](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll) has its own problems. 
3. Link to the GitHub CLI - the git commands do not work directly from the CLI.
4. When using the default "Minima" theme, the title of the blog becomes a circular link, pointing to the home page.

Mon 29 Dec 2025 13:24
---
The Merlot theme looks better than the Minima theme. I think, I am attracted by its banner.

The default "Minima" theme is set in the Gemfile. Like this:

```ruby
This is the default theme for new Jekyll sites. You may change this to anything you like.
gem "minima", "~> 2.0"
```

Changing that to merlot didn't affect the page. Changing the publishing source of the site from /docs to /root removes all Jekyll-processing, and renders plain text. When the source is /docs, the minima theme takes effect even though I removed its mention from everywhere in the repo. Jekyll processed the md files, and displayed them as html text on the links.

Mon 29 Dec 2025 23:29
---
There seems to be no way to have the index.html file in the root folder, and use any Jekyll theme. It can be in the /docs folder, and then it will use the Minima theme. The only way to have the index.html file and use a theme is to put it in the docs folder.

#### Use GitHub Actions 
***Till now, I had been publishing the site using the "Classic Branches" workflow. It is not recommended. GitHub's QuickStart Guide sets up the Pages site only to fail. It uses the Branches workflow, does not warn that the repo needs to be the same as the site name, uses a default theme where the most prominent link points to the same page. It is a full-fledged project just to change the theme, create a new page, add content.***

After looking into documentations, other options, and custom html, I changed from the *Classic Branches* workflow to the GitHub Actions workflow. GitHub Actions Workflow file added. One problem - the UI from the Settings -> Pages section opens into the main branch, and there was no way to commit the new config file to a different branch. Had to add the file manually to a new branch.

The GitHub Actions Workflow build gave this message: 
> The github-pages gem can't satisfy your Gemfile's dependencies. If you want to use a different Jekyll version or need additional dependencies, consider building Jekyll site with GitHub Actions: https://jekyllrb.com/docs/continuous-integration/github-actions/

So added this line in Gemfile: `` gem "jekyll", "~> 4.2"``

Tue 30 Dec 2025 01:52
---
That was a wrong turn. Found that this page recommended a different workflow - https://jekyllrb.com/docs/continuous-integration/github-actions/. Removed the added line from the Gemfile, then followed that page to "Click Configure under the Jekyll workflow".

Tue 30 Dec 2025 01:57
---
Now I broke GitHub. The GitHub Actions [build](https://github.com/aeconoclast/aeconoclast.github.io/actions/runs/20586136002) failed with this message:

> **Failed to save: <h2>Our services aren't available right now</h2><p>We're working to restore all services as soon as possible. Please check back soon.</p>0zCJTaQAAAAAtMqAK6fApSKvnxU0VWvAJQ0hHRURHRTE3MTYARWRnZQ==**

Will try later.

Tue 30 Dec 2025 22:52
---

It works now! Those build failure messages were a decoy. The real issue was in the build's log message:

> Liquid Exception: No repo name found. Specify using PAGES_REPO_NWO environment variables, 'repository' in your configuration, or set up an 'origin' git remote pointing to your github.com repository. in /_layouts/default.html
> 
> ERROR: YOUR SITE COULD NOT BE BUILT:
> 
> No repo name found. Specify using PAGES_REPO_NWO environment variables, 'repository' in your configuration, or set up an 'origin' git remote pointing to your github.com repository.````
> Error: Process completed with exit code 1.


To resolve that issue, I corrected the entries in _config.yml to this:

> repository: aeconoclast/aeconoclast.github.io
> 
> repository_url: https://github.com/aeconoclast/aeconoclast.github.io

After completing that, the build ran successfully . This created one page as desired for the first time - the free-mouse-clicks page displayed in the Merlot theme correctly. The home page https://aeconoclast.github.io still used vanilla html. For that, I copied the page source of the free-mouse-clicks page, edited it appropriately, and pasted it to index.html in the root directory. Viola, that worked!

The index.html page becomes the home and https://aeconoclast.github.io works at last. The only caveat: If I am making changes to the CSS, I have to change index.html separately. That's small price to pay for using the theme. The bigger price was all the time spent trying to actually getting the site to work. Now we know that the publishing using the "classic" Branches does not work.

#### Next Step

Add links to the blue part of the banner. These are part of *section id=downloads* in the CSS file.

Tue 6 Jan 2026 19:42
---
The blue part of the banner uses CSS classes to show the URLs for ZIP and TGZ file downloads. I was not able to replace those with my own classes successfully in a short time. The replacement broke the page's display.
So I used the same classes, but changed the URLs as I needed.

Tue 6 Jan 2026 23:54
---
I added an empty page to the site, and configured it as "empty_page". This is called in default.html, and linked at the top as "Next" now. When more pages are added to the blog, this "Next" link needs to be link to those.

#### Next Step

Write logic in default.html to use empty page link only if there are no more pages to the blog. This will make the blog act like a website with each page navigated to using the Next link.
Write one more page to check if this logic works.

### Last Words?

This could go on and on till I find a way to stop doing this or outsource it. Stopping here since this site is up and running.

### References

This [blog]( https://vickiboykis.com/2015/05/30/man-do-static-sites-suck./) talks about how the Jekyll-based Github pages site is neither easy nor straightforward to create.
Another [blog](https://www.jessesquires.com/blog/2021/11/01/how-to-start-a-blog/) instructs on how to create a blog. This [page](https://jessesquires.github.io/)) shows how the site created using GitHub's Quickstart Guide looks like.
