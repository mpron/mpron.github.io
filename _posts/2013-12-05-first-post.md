---
layout: post
title: Setting Up This Blog
description: "My first post on a fresh new Jekyll blog.  Here's how I handled issues installing Jekyll on Windows and how I dealt with Pygments and encoding issues."
modified: 
tags: [Windows, Jekyll, Ruby]
image:
  feature: castlewater.jpg
  credit: Frédéric Bazille
  creditlink: https://images.nga.gov/en/asset/show_zoom_window_popup.html?asset=55194&location=grid&asset_list=77764,77730,76466,68588,68124,67331,67307,66306,65879,58917,58901,58618,57395,56412,56403,56400,56200,55195,55194,49508,47771,47749,47246,47244,46483,46470,46349,46348,46347,46345,46344,45806,45797,45788,45785,45758,45749,45723,45260,45259,45220,45096,45092,45091,45056,43436,38534,19790,19781&basket_item_id=undefined
comments: true
share: true
---

Now that I've completed [three intensive months](http://bloc.io) of full-stack Ruby on Rails training, I decided that the next project on my docket was to set up my own blog – one that I can use for the long hall.

But it wasn't clearly the next item on my list of project ideas until I stumbled upon this [little beauty called](http://mmistakes.github.io/hpstr-jekyll-theme) "HPSTR", a theme for Jekyll.  Before I found that, I was planning on using the shiny new blog engine ["Ghost"](http://ghost.org), which I _do_ still want to try out on [OpenShift](https://www.openshift.com).

So here's how the setup process went for me as I tried to build this new blog.

# Jekyll Windows Setup and Theme Cloning

_Pause for a **TL;DR** section_ – Here are all the links to articles and docs that I used throughout the process:

* [HPSTR Theme Setup](http://mmistakes.github.io/hpstr-jekyll-theme/theme-setup/)
* [Installing Jekyll on Windows](http://chrismeserole.com/coding/install-ruby-rails-jekyll-on-windows/)
* [SO Question on Jekyll "Liquid Exception" issue with Pygments](http://stackoverflow.com/questions/17332964/jekyll-liquid-exception-cannot-find-bin-sh-on-windows/20365857#20365857)
* [Fixing the "Liquid Exception" 'UTF-8 and IBM437' issue](http://www.madhur.co.in/blog/2011/09/01/runningjekyllwindows.html#comment-1151046802)

My first stop was the [Theme Setup section](http://mmistakes.github.io/hpstr-jekyll-theme/theme-setup/) of the HPSTR theme demo site. Step one: Install Jekyll.  So I jumped over to the Jekyll homepage and I was reminded that Jekyll is not officially supported by Windows.  

No worries. The community has me covered.  The Jekyll users community has had more than a year to bring some mature tools and tutorials into the mix.

Here were the first steps (some of which I had already done for past projects):

 1. [Download and Run the RailsInstaller for Windows](http://railsinstaller.org/)
 2. [Download and Install Git for Windows](http://git-scm.com/downloads)
 3. [Download and Install Python 2.7 for Windows](http://www.python.org/download/releases/2.7.6/) (get the first download unless you have a 64-bit Windows install, then get the third MSI link)
 3. Run `gem install jekyll` in the command line
 4. Run `gem install kramdown` in the command line ([kramdown](https://github.com/gettalong/kramdown) is the [markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) editor that the HPSTR theme uses, but you could use your own with some research and hacking.

If you didn't even have Git installed already, you might want to start with some more basic tutorials on [using Git](http://lifehacker.com/5983680/how-the-heck-do-i-use-github) and the [Command Line](http://cli.learncodethehardway.org/book/).

Now back to Michael Rose's [HPSTR Theme Setup Tutorial](http://mmistakes.github.io/hpstr-jekyll-theme/theme-setup/). 

Michael says to fork his theme's [repo](https://github.com/mmistakes/hpstr-jekyll-theme) _(hit the fork button to do that)_ but I don't think I needed to do that when all was said and done.  Any git pushes will go to the fork instead of the new repo that I wanted to create under my GitHub User Pages URL.  So when I was ready to go live, I used [these instructions](https://help.github.com/articles/changing-a-remote-s-url) to switch the remote origin from the forked repo to my mpron.github.io repo that I had created.

All I really think you need to do is create a folder where you want to keep your blog files, navigate there in the command line, then grab the clone url  on Michael's theme repo page, and paste it in the `git clone [paste url here]` command and run it.

# Pygments Issues

Now that you've got all of the theme's files on your machine, it's time to test it out.  In the same folder that has the HPSTR theme files, run `jekyll serve` and see what the command line tells you.  Chances are you probably ran into some "Liquid Exception" issues that I did.  The first was with with a library for code syntax highlighting called Pygments.  

If you don't plan on ever sharing code snippets in your blog, you can just go to the [`_config.yml`](http://jekyllrb.com/docs/configuration/) file and look for `pygments: true`.  Set it to `false` if you don't need code syntax highlighting.

I did want highlighting, so in order for this to work, you need to uninstall a the current Pygments library (a ruby gem) if it's version is greater than 0.5.0.

Here's what you should run in your command line to fix things:

{% highlight console %}
gem list
[displays a list of all your installed ruby gems 
with their version numbers in parentheses]
gem uninstall pygments.rb --version "=[insert any pygments version number 
that was installed in the ruby gems list above 0.50]"
gem install pygments.rb --version "=0.5.0"
{% endhighlight %}

My gem list showed `pygments.rb (0.5.0, 0.5.4)` so I had to run `gem uninstall pygments.rb --version "=0.5.4"`

_**Note** about using Syntax Highlighting:_
_When you want to highlight a piece of code, make sure you use the proper highlighting syntax, or your site will not run or deploy.  An example code snippet in your blog post's markdown file will look like this:_

![Syntax Highlighting](http://i.imgur.com/rPmWTOi.jpg)

_If you use a word after `highlight` that Pygments doesn't have a lexer (highlighter) for, then your site won't run.  To see all the lexers you can use, [visit this page](http://pygments.org/docs/lexers/) and do ctrl+F searches for the languages you want to highlight.  For this tutorial I used `highlight console`._

Now, the last thing you need to do is go to your C:\ drive and open the RailsInstaller folder that should be there now. Then you have to go into the Ruby 1.9 or Ruby 2.0 folder, depending on which version you decided to get, and then finally open the `setup_environment.bat` file in your code editor. My path to the file looked like this:

`C:\RailsInstaller\Ruby1.9.3\setup_environment.bat`

Look for the "SET PATH=" line which will look something like this:

`SET PATH=%RUBY_DIR%\bin;[several other other paths];%PATH%`

and then insert `C:\Python27` into it at the end but in front of `;%PATH%`.  It should look like this:

`SET PATH=%RUBY_DIR%\bin;[several other other paths];C:\Python27;%PATH%`

Close and restart your command line window, navigate to the jekyll theme folder again, and run `jekyll serve`.  Did you run into the same "Liquid Exception" error, or did it run just fine?  A this point everything ran fine for me during a few `jekyll serve` tests, but for no clear reason, a different "Liquid Exception" error cropped up...

# UTF-8 Encoding Issues

Here's the second weird error I got:

{% highlight console %}
Liquid Exception: incompatible character encodings: UTF-8 and IBM437 in _layouts/page.html
{% endhighlight %}

Even though there was a relatively simple solution for this, it didn't stop me from finding a bunch of different, more complex and confusing ways to deal with this encoding issue.  

Most of the searches I did pointed to methods that used this [chcp 65001](http://joseoncode.com/2011/11/27/solving-utf-problem-with-jekyll-on-windows/) command, but the better method was hiding in plain sight in the [comments of the Jekyll on Windows tutorial](http://www.madhur.co.in/blog/2011/09/01/runningjekyllwindows.html#comment-1151046802) that Jekyllrb.com recommended, which I didn't initially use because it was pretty dated and unnecessarily complicated.  

If you take a look at [my comment](http://www.madhur.co.in/blog/2011/09/01/runningjekyllwindows.html#comment-1151046802) on the tutorial, I mention that another commenter on the post showed me the solution.  Just add the following line to your `_config.yml`, run `jekyll serve` again, and rejoice!

{% highlight console %}
encoding: UTF-8
{% endhighlight %}

That's it.  I _didn't_ need to change my markdown gem to `redcarpet` and I didn't need to mess with the `chcp` command.

# Off and Running with the HPSTR Theme

The first thing you'll want to do, if you're not already familiar with Jekyll's unique but pretty intuitive file structure, is to walk through this helpful [Nettuts tutorial](http://net.tutsplus.com/tutorials/other/building-static-sites-with-jekyll/) so that you understand which files and folders control different aspects of the site.

Once you've done that, you can look back at our HPSTR themed blog files and start making some modifications.

#### Modding Tips ####

Read through Michael Rose's [HPSTR Theme Setup Tutorial](http://mmistakes.github.io/hpstr-jekyll-theme/theme-setup/) and all of his other posts on the theme demo to find out about some of the simple modifications you can make.  Some of his sections, like the one about using [Grunt](http://gruntjs.com/), and any major customizations will require your own independent research.

For me, the main things I wanted to customize were:

* Delete his posts and site data and put in my own (obviously)
* Delete his "About" information and insert my own (obviously)
* Add my own images for the main page and for blog posts
* Add my own background

Michael gives good advice for swapping your information into the `_config.yml` file, so that part should be fairly easy.  **Just remember to leave the `url:` field blank when you are modifying and testing your site locally**.  And you probably don't need to worry about the Disqus and Google Analytics credentials until you confirm what your site's URL will be.

Next you'll want to delete or move the posts that Michael has in there, but I'd recommend you move them to another folder outside your Jekyll project so that you can still reference how he does certain things like videos and code snippets later.  In several cases, reading the markdown code of those posts was a lot more helpful than just reading the post on his demo site.

I'd also recommend you keep one of his posts in your Jekyll project so that you can just delete his markdown text and write your own while maintaining all of the fields in the header content that this theme uses (e.g. `title:`, `description:`, `image:`).

Next, go to the `about.md` file, which isn't in any folder, and modify that to be an about page for you.

Then open up the `index.html` file, which is also not in any folder.  This is going to modify your home page, so make sure you personalize it with your own images and info in the header content.

#### Images ####

In order to use an image on a page, you just have to go find one, modify it to your liking, drop it in the `images` folder in your Jekyll project, and then paste the name of the file in the header content of the page where you want to use it, just like the default images.

Although Michael suggests different dimensions, I think that the images should be at least 1200px long and **the height should be half the width**.  This looked better to me when I was decreasing the size of the window.  If the image is very wide and not very high, then the text will flow out of the borders of the picture at certain window sizes.

Finally, to change the background, just find a subtle square image that's not too big and won't look ugly when it's tiled across your background.  The fun part of this exercise is testing different backgrounds and feature images to see which ones you like the most for your blog's style.

# Deploying Your Blog

Once you've gotten a few modifiations, you'll want to try deploying your site to the web early.  Don't try and do a ton of modifications before seeing how the site will deploy to the web.  A common credo among developers is "deploy early and often."

There are many ways you could deploy this blog, but the easiest by far is to use this blog as your GitHub user page.  That just means that GitHub will host it for free as your one personal page that corresponds to your GitHub account.

Before you start your first deployment, **make sure you create your user page repo on GitHub and add the user page's URL to the `url:` field in your `_config.yml` file**.  I'll show you what I mean

#### Making Your GitHub User Page Repo and Deploying to it ####

This part is super simple, but you have to create this repo on the GitHub site before you deploy your Jekyll project to it.  This is why you don't really want to fork (make a copy) of Michael Rose's repo, because then it will already be linked to deploy your project to that for, not the new GitHub User Page repo that we want it to go to.

Go to your GitHub web account, click the "Repositories" tab, and then click the green "New" button.  Then, in the "Repository Name" field, type "[your GitHub username].github.io".  That's going to be the URL people type to get to your blog.  Mine is mpron.github.io, as you can see in your address bar above.

You can ignore the other fields and hit "Create Repository".  If you forked Michael's repo, like I did, go to your command line, navigate to your Jekyll project, and follow [these instructions](https://help.github.com/articles/changing-a-remote-s-url) to replace the old forked repo with the new [your GitHub username].github.io as the remote origin.

If you didn't fork his repo, then just go to your Jekyll project in the command line and follow the instructions on the GitHub page that appears after you create the repository.  Typing those commands will allow you run through this process every time you want to deploy a modification to your site:

{% highlight console %}
git add . 
git add -u
git commit -m "this is a description of what I changed"
git push
{% endhighlight %}

You don't need to do the `git add -u` if you haven't deleted any files.  This is just a rough estimate for the average deployment.  You may want to do a bunch of different things when deploying or developing, so read the first few chapters of [Pro Git](http://git-scm.com/book) (free online book) if this all seems unfamilliar to you.

**You're basically done now!**

If you connected your project folder to the [your username].github.io using the instructions on the GitHub page, then you should see all the project files when you go to `https://github.com/[your GitHub username]/[your GitHub username].github.io`

To see your live blog, simply go to `[your GitHub username].github.io`.  See how it looks, make some more modificatons or create new posts locally, and then push them to GitHub and check that URL again.

Enjoy your new blog, you badass!

