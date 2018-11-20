---
author: sravanti
categories:
  - journalism
date: 2016-02-23 06:01:00
guid: http://sravantitekumalla.com/?p=27
id: 27
permalink: /when-github-and-moma-collide/
title: '[WIP] When Github and MoMA collide'
url: /2016/02/23/when-github-and-moma-collide/
---

When I saw that MoMA had released their collection data on [GitHub](https://github.com/MuseumofModernArt/collection), I knew I had to do _something _ with it.  I&#8217;m taking art history right now and I find myself asking several questions about when and how art is acquired, so this is a great tool to help answer some of those questions.

I read [fivethirtyeight&#8217;s MoMA analysis](http://fivethirtyeight.com/features/a-nerds-guide-to-the-2229-paintings-at-moma/), but I think we can do more with this dataset — more than the physical composition about the works of art, we can make sense of the context surrounding art as well. Who&#8217;s creating it and where do they come from? Does MoMA acquire a diverse range of art, by artists of color and from all around the world? Has the diversity changed over time?

For now, I&#8217;ve just been playing around with it in (all of ) my free time, but once I figure out what it is I want to do, I&#8217;m planning on creating some visualizations using D3.

For now, here&#8217;s what I&#8217;ve found (I&#8217;ll update this as I find more):

**Top cities from which art is acquired:**

This is tricky, and right now, my string matching is pretty naive. MoMA doesn&#8217;t have a field for where the art is from for each work of art, but rather jumbles it in the title field. It&#8217;s tricky to match the work of art to a location, but by attempting to find substrings of major cities, here&#8217;s what I found:

<li class="p1" style="text-align: left;">
  <span class="s1">New York (obviously)</span>
</li>
<li class="p1" style="text-align: left;">
  Berlin
</li>
<li class="p1" style="text-align: left;">
  Chicago
</li>
<li class="p1" style="text-align: left;">
  Paris
</li>
<li class="p1" style="text-align: left;">
  London
</li>
<li class="p1" style="text-align: left;">
  Mexico City
</li>
<li class="p1" style="text-align: left;">
  Buenos Aires
</li>
<li class="p1" style="text-align: left;">
  San Francisco
</li>
<li class="p1" style="text-align: left;">
  Manhattan (this belongs in the NYC count — will fix for next iteration)
</li>
<li class="p1" style="text-align: left;">
  LA
</li>

What does this tell us? Mostly that art is acquired from major cities in the US and Europe with a couple exceptions for Mexico City and Buenos Aires. I&#8217;m curious — how diverse is MoMA&#8217;s collection, not only in terms of its artists but where the art comes from?

&nbsp;

**How much of MoMA&#8217;s art is by artists that are currently living? **

Luckily, this is easier to figure out — if an artist is currently living, the Artist Bio field contains &#8220;born YYYY&#8221; instead of (YYYY-YYYY). I&#8217;m curious to see how &#8220;modern&#8221; MoMA&#8217;s collection is. Obviously, MoMA&#8217;s been around for a while, so I expect that this number will be fairly low, right? One, Most of the art MoMA has in its collections are from artists that were alive in the 20th century and two, most of the temporary exhibits host the &#8220;contemporary&#8221; art. Nonetheless, here&#8217;s what I found:

  * MoMA has 6910 works of art by artists that are still living (roughly 5% of its collection)
  * The most represented artist is an artist from Berlin, Eberhard Havekost

&nbsp;

&nbsp;
