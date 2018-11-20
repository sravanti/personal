---
author: sravanti
categories:
  - programming
date: 2016-04-20 04:57:30
guid: http://sravantitekumalla.com/?p=42
id: 42
permalink: /what-does-hillary-clintons-inbox-look-like/
title: What does Hillary Clinton’s inbox look like?
url: /2016/04/20/what-does-hillary-clintons-inbox-look-like/
---

I, too, am tired of hearing about Hillary’s use of a private email server. On the other hand, it led to a pretty neat data set to unpack: a dump of emails she’s sent and received.

<span style="font-weight: 400;">I played around with this data set a bit and was particularly interested in how different groups of people interacted with Hillary. Did men use shorter sentences than women, for example? Did her staffers send one-liners versus ambassadors who sent lengthy emails? Did she have interesting relationships with people we might not be familiar with?</span>

<span style="font-weight: 400;">These are obviously a host of questions to answer, but I’m starting to chip away at some of this, in part for a project I’m doing for my natural language processing class. Lesson learned along the way: visualizing text is </span>_<span style="font-weight: 400;">hard.</span>_<span style="font-weight: 400;"> I found that the norm for text visualizations out there, such as word clouds or circle packing, was reductionist for some of the data I have, like topic models or k-means clustering. </span>

<span style="font-weight: 400;">For a simple representation to start, I generated </span>[<span style="font-weight: 400;">a scatter plot visualization</span>](http://sravantitekumalla.com/futureofnews/dataviz/scatter.html) <span style="font-weight: 400;">using <a href="https://mpld3.github.io">mpld3</a> (created by my NLP professor for another assignment) which creates interactive matplotlib graphs for the browser. It’s clunky to navigate (you need to switch to a zoom-in mode, drag a rectangular portion of the graph to zoom in on, then switch again to the cursor mode to scroll over words), but it’s interesting to see which words appear together for a first step.</span>

&nbsp;<figure id="attachment_43" style="width: 980px" class="wp-caption alignnone">

<img class="wp-image-43 size-full" src="http://sravantitekumalla.com/wp-content/uploads/2016/04/Screen-Shot-2016-04-20-at-12.42.52-AM.png" alt="cluster" width="980" height="756" srcset="http://sravantitekumalla.com/wp-content/uploads/2016/04/Screen-Shot-2016-04-20-at-12.42.52-AM.png 980w, http://sravantitekumalla.com/wp-content/uploads/2016/04/Screen-Shot-2016-04-20-at-12.42.52-AM-300x231.png 300w, http://sravantitekumalla.com/wp-content/uploads/2016/04/Screen-Shot-2016-04-20-at-12.42.52-AM-768x592.png 768w, http://sravantitekumalla.com/wp-content/uploads/2016/04/Screen-Shot-2016-04-20-at-12.42.52-AM-800x617.png 800w" sizes="(max-width: 980px) 100vw, 980px" /><figcaption class="wp-caption-text">Isn&#8217;t it interesting that &#8220;bipartisan&#8221; appears well outside the main cluster of words?</figcaption></figure> 

&nbsp;

<span style="font-weight: 400;">I&#8217;m using a n-gram analysis to figure out differences in word usage between genders (spoiler: there isn&#8217;t a significant difference). </span>

<span style="font-weight: 400;">The <a href="https://en.wikipedia.org/wiki/K-means_clustering">k-means clustering</a> between genders was slightly more interesting:</span>

(threshold: 10 occurrences per word, clusters = 25, window size=3). Side note: I need to increase the number of clusters, perhaps the threshold as well.

[Female k-clusters](http://sravantitekumalla.com/47-2/)

[Male k-clusters](http://sravantitekumalla.com/male-k-means-clustering/)

I&#8217;m still slightly stumped on how to represent this well. In the meantime, I&#8217;ll be working on creating an interactive to show some of the [LDA](https://en.wikipedia.org/wiki/Latent_Dirichlet_allocation) topic modeling analysis I did as well as finding a clean way to display vocabulary differences between different categories of people.

This is obviously a work in progress — if you&#8217;d like to follow along,  I&#8217;m actively working on this for the next month on [GitHub](https://github.com/wellesleynlp/sravanti-finalproject) (forgive the messy Python scripts).

&nbsp;