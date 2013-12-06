---
layout: post
title: Setting Up This Blog
description: "My first post on my fresh new Jekyll blog.  Here's how dealt with issues installing Jekyll on Windows and dealing with Pygments and encoding issues."
modified:
tags: [Windows, Jekyll, Ruby]
image:
  feature: castlewater.jpg
  credit: 
  creditlink: 
comments: true
share: true
---

Now that I've completed [three intensive months](http://bloc.io) of full-stack Ruby on Rails training, I decided that the next project on my docket was to set up my own blog – one that I can use for the long hall.

But it wasn't clearly the next item on my list of project ideas until I stumbled upon this [little beauty called](http://mmistakes.github.io/hpstr-jekyll-theme) "HPSTR", a theme for Jekyll.  Before I found that, I was planning on using the shiny new blog engine ["Ghost"](http://ghost.org), which I _do_ still want to try out on [OpenShift](https://www.openshift.com).

So here's how the setup process went for me as I tried to build this new blog.

#Jekyll Windows Setup and Theme Cloning
______________

This is me.  How do I look in my spiffy shirt and tie.  I think the tie clip adds a nice touch.  Don't worry.  There's nothing important about that all-white clock in the background.  It's just background.  Anyway, enough about me.

![Mitch Pronschinske]({{ site.url }}/avatar.jpg)
{: .pull-left}

*This is emphasized*. Donec faucibus. Nunc iaculis suscipit dui. 53 = 125. Water is H<sub>2</sub>O. Nam sit amet sem. Aliquam libero nisi, imperdiet at, tincidunt nec, gravida vehicula, nisl. The New York Times <cite>(That’s a citation)</cite>. <u>Underline</u>. Maecenas ornare tortor. Donec sed tellus eget sapien fringilla nonummy. Mauris a ante. Suspendisse quam sem, consequat at, commodo vitae, feugiat in, nunc. Morbi imperdiet augue quis tellus.

HTML and <abbr title="cascading stylesheets">CSS<abbr> are our tools. Mauris a ante. Suspendisse quam sem, consequat at, commodo vitae, feugiat in, nunc. Morbi imperdiet augue quis tellus. Praesent mattis, massa quis luctus fermentum, turpis mi volutpat justo, eu volutpat enim diam eget metus.

### Blockquotes

> Lorem ipsum dolor sit amet, test link adipiscing elit. Nullam dignissim convallis est. Quisque aliquam.

## List Types

### Ordered Lists

1. Item one
   1. sub item one
   2. sub item two
   3. sub item three
2. Item two

### Unordered Lists

* Item one
* Item two
* Item three

## Tables

| Header1 | Header2 | Header3 |
|:--------|:-------:|--------:|
| cell1   | cell2   | cell3   |
| cell4   | cell5   | cell6   |
|----
| cell1   | cell2   | cell3   |
| cell4   | cell5   | cell6   |
|=====
| Foot1   | Foot2   | Foot3
{: rules="groups"}

## Code Snippets

Syntax highlighting via Pygments

{% highlight css %}
#container {
  float: left;
  margin: 0 -240px 0 0;
  width: 100%;
}
{% endhighlight %}

Non Pygments code example

    <div id="awesome">
        <p>This is great isn't it?</p>
    </div>

## Buttons

Make any link standout more when applying the `.btn` class.

{% highlight html %}
<a href="#" class="btn btn-success">Success Button</a>
{% endhighlight %}

<div markdown="0"><a href="#" class="btn">Primary Button</a></div>
<div markdown="0"><a href="#" class="btn btn-success">Success Button</a></div>
<div markdown="0"><a href="#" class="btn btn-warning">Warning Button</a></div>
<div markdown="0"><a href="#" class="btn btn-danger">Danger Button</a></div>
<div markdown="0"><a href="#" class="btn btn-info">Info Button</a></div>
