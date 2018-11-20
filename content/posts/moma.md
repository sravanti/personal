---
author: sravanti
categories:
  - journalism
  - programming
date: 2018-08-03 12:30:11
guid: https://sravantitekumalla.com/?p=166
id: 166
permalink: /looking-for-artists-who-look-like-me/
title: 'Looking for Artists Who Look Like Me'
url: /2018/08/03/looking-for-artists-who-look-like-me/
---

_Note: this blog post is based on a talk I gave at Write/Speak/Code in NYC on August 3, 2018. [Find the slides here!](https://sravantitekumalla.com/momadiversity/) _

<p class="p1">
  In the past, I’ve <a href="https://sravantitekumalla.com/when-github-and-moma-collide/">documented</a> my previous attempts to analyze the MoMA GitHub repository of artists and artworks. Inspired by the initial analysis of the massive collection of art metadata by <a href="https://fivethirtyeight.com/features/a-nerds-guide-to-the-2229-paintings-at-moma/">FiveThirtyEight</a>, I set off to answer a few questions of my own. Initially, I was initially interested in questions like, “How rapidly has the museum collected art over time?” or “How many works of art were gifted to the museum versus bought? Who have been major donors over the years?”
</p>

<p class="p1">
  I gathered some basic insights in my <a href="https://sravantitekumalla.com/when-github-and-moma-collide/">WIP post</a>, but didn’t really delve into it further. The questions above were interesting to answer, but didn&#8217;t reflect what I was really interested in, which were questions about diversity of art and artists over time.  Is the MoMA including more women over time? How about POC artists?
</p>

<p style="padding-left: 30px;">
  <em>A note on the methodology: I used the CSV files in the GitHub repository, as opposed to the JSON files. This allowed me to port the CSV into a SQL database, which made querying much faster than doing analysis using Python.</em>
</p>

<p class="p1">
  Let’s start with two data points the dataset gives us: gender and nationality (we’ll delve more into race later). I started with taking the aggregate gender counts over the 89 years worth of data MoMA provides.
</p>

<p class="p1">
  <img class="alignnone size-medium wp-image-167" src="https://sravantitekumalla.com/wp-content/uploads/2018/08/Screen-Shot-2018-08-01-at-4.29.26-PM-300x284.png" alt="" width="300" height="284" srcset="https://sravantitekumalla.com/wp-content/uploads/2018/08/Screen-Shot-2018-08-01-at-4.29.26-PM-300x284.png 300w, https://sravantitekumalla.com/wp-content/uploads/2018/08/Screen-Shot-2018-08-01-at-4.29.26-PM.png 664w" sizes="(max-width: 300px) 100vw, 300px" />
</p>

<p class="p1">
  This isn&#8217;t particularly surprising: female artists make up about 15% of the total artists represented at MoMA. I am curious about the 3130 artists without a gender label. It could be that those artists identify as non-binary, but in that case I would assume the museum would include their preferred gender pronouns or make a note. More likely is the scenario that the artists are institutions (Bauhaus, for example) or anonymous artists.
</p>

<p class="p1">
  <em>*An action item if you’re interested:  contact MoMA to learn more about non-binary artist representation and push for accurate gender representation in these data sets!</em>
</p>

<p class="p1">
  Beyond the aggregate, I wanted to understand how the ratio of art created by women artists have changed over time. My hunch was that the ratio increases over time; MoMA is more progressive than traditional art museums, and would be more conscious of the diversity of artists they select.
</p>

<p class="p1">
  My hunch was wrong.
</p>

<p class="p1">
  <img class="alignnone wp-image-168 size-large" src="https://sravantitekumalla.com/wp-content/uploads/2018/08/Screen-Shot-2018-08-01-at-4.30.07-PM-1024x621.png" alt="" width="1024" height="621" />
</p>

<p style="padding-left: 30px;">
  <em>This chart was created by using the &#8220;Artworks&#8221; CSV file in the MoMA repository. I grouped together art by year of acquisition and for each piece of art, determined the number of male and female artists that created each piece ( most art is by solo artists, but there are many art pieces that have multiple artists associated with it). I then went from 1929 to 2018, aggregating the count of female artists up until that year and dividing that number by the total # of artists. </em>
</p>

<p class="p1">
  When I first saw this chart, I didn’t think it was right. I ran the numbers a few more times, double checked my logic, and implemented the calculations a few different ways. I was expecting more of a linear trend, and certainly not a downward trend in 2017! What happened? It’s important to consider the context of the data: perhaps the museum acquired a lot of art last year by male artists but also happened to include more female artists than ever—the percentage alone doesn’t tell the whole story. But still, this was disappointing to see, and totally disproved my hypothesis.
</p>

<p class="p1">
  If you’re looking for a silver lining, though, it’s that the MoMA includes more female artists than the Metropolitan Museum of Art (according to the below statistic by the Guerrilla Girls, a feminist art group):
</p>

<img class="alignnone wp-image-169 size-large" src="https://sravantitekumalla.com/wp-content/uploads/2018/08/Screen-Shot-2018-08-01-at-4.30.52-PM-1024x467.png" alt="" width="1024" height="467" srcset="https://sravantitekumalla.com/wp-content/uploads/2018/08/Screen-Shot-2018-08-01-at-4.30.52-PM-1024x467.png 1024w, https://sravantitekumalla.com/wp-content/uploads/2018/08/Screen-Shot-2018-08-01-at-4.30.52-PM-300x137.png 300w, https://sravantitekumalla.com/wp-content/uploads/2018/08/Screen-Shot-2018-08-01-at-4.30.52-PM-768x350.png 768w, https://sravantitekumalla.com/wp-content/uploads/2018/08/Screen-Shot-2018-08-01-at-4.30.52-PM.png 1390w" sizes="(max-width: 1024px) 100vw, 1024px" />

<p class="p1">
  The second part of my hypothesis was that MoMA includes more POC over time, for the same reasons of progressivism and that MoMA tends to be more open to different identities of artists compared to older art institutions. As a starting point, remember that we have nationality, not race, in our dataset. As I mapped out gender over time, I decided to map the top 15 nationalities over time—mapping out all of the countries would be too much for a line graph. Is this a job for a choropleth over time? Yes! Did I have time to mess around with d3 to get a choropleth graph over time? No. 🙁 In any case, here’s the graph:
</p>

<p class="p1">
  <img class="alignnone wp-image-170 size-large" src="https://sravantitekumalla.com/wp-content/uploads/2018/08/Screen-Shot-2018-08-01-at-4.31.19-PM-1024x701.png" alt="" width="1024" height="701" srcset="https://sravantitekumalla.com/wp-content/uploads/2018/08/Screen-Shot-2018-08-01-at-4.31.19-PM-1024x701.png 1024w, https://sravantitekumalla.com/wp-content/uploads/2018/08/Screen-Shot-2018-08-01-at-4.31.19-PM-300x205.png 300w, https://sravantitekumalla.com/wp-content/uploads/2018/08/Screen-Shot-2018-08-01-at-4.31.19-PM-768x526.png 768w, https://sravantitekumalla.com/wp-content/uploads/2018/08/Screen-Shot-2018-08-01-at-4.31.19-PM.png 1396w" sizes="(max-width: 1024px) 100vw, 1024px" />
</p>

<p style="padding-left: 30px;">
  <em>This chart was created by using the &#8220;Artworks&#8221; CSV file in the MoMA repository. I grouped together art by year of acquisition and for each piece of art, used the nationality provided for the artist associated with the piece of art. Note that for this chart, I only used solo artists, and did not consider art by multiple artists from multiple nationalities. </em>
</p>

<p class="p1">
  The steep purple line is the USA, and the blue line soaring above the rest is France. This intuitively makes sense: seeing as MoMA is an American museum, it makes sense that they’d want to display art by its citizens. I would expect an analogous result when looking at the Tate and its representation of British artists, for example.
</p>

<p class="p1">
  <em>*Action item if you’re interested: prove this hypothesis right or wrong! The Tate has an open source dataset similar to MoMA.</em>
</p>

<p class="p1">
  As we know, though, Americans != white people. How can we then go on to quantify race? This is a tricky problem, and not one that has a bulletproof solution. It’s important to note here that I’m not trying to box anyone into a race or guess what race someone is. It’s more that I’m trying to understand race at the aggregate level. Luckily, there’s an API that can help take a name and spit out the two most likely ethnicities of a person: the diaspora API from <a href="https://www.namsor.com/">NamSor</a> with a probability attached to each ethnicity.
</p>

<p class="p1">
  A short aside: It’s worth noting at this point that I have a secret agenda here. I’d love to know if there are any artists that share my identity: women artists that are Indian-American. Why care about this? Why look for this? It’s because I think there’s a high likelihood that an artist who shares my identity will create art around themes I can relate to and identify with. I’m sure I’d be able to relate to a hypothetical female Indian-American’s art more than, say, a European-American artist.
</p>

<p class="p1">
  Given the name limits imposed by NamSor, I had to make some tough decisions when looking at ethnicity diversity. Given my secret agenda, I decided to just run female American artists through the API, and this is what I found:
</p>

<p class="p1">
  <img class="alignnone wp-image-172 size-large" src="https://sravantitekumalla.com/wp-content/uploads/2018/08/Screen-Shot-2018-08-01-at-5.42.44-PM-544x1024.png" alt="" width="544" height="1024" srcset="https://sravantitekumalla.com/wp-content/uploads/2018/08/Screen-Shot-2018-08-01-at-5.42.44-PM-544x1024.png 544w, https://sravantitekumalla.com/wp-content/uploads/2018/08/Screen-Shot-2018-08-01-at-5.42.44-PM-159x300.png 159w, https://sravantitekumalla.com/wp-content/uploads/2018/08/Screen-Shot-2018-08-01-at-5.42.44-PM-768x1446.png 768w, https://sravantitekumalla.com/wp-content/uploads/2018/08/Screen-Shot-2018-08-01-at-5.42.44-PM.png 806w" sizes="(max-width: 544px) 100vw, 544px" />
</p>

<p class="p1">
  Again, I didn&#8217;t find these results too surprising. The representation includes mostly European identities, followed by Black and Latina artists. I kept looking down the list: there have to be a few Indians here….right? Noting the 10 potential candidates, I decided to google them all. Unfortunately, for 8 of them, I couldn’t really tell what race they were—the only confirmation I would take is if someone self-identified with a racial identity.
</p>

<p class="p1">
  I did get lucky with two artists though! In particular, I was excited to come across <a href="https://www.moma.org/artists/37879">Chitra Ganesh’</a>s work. She focuses on themes of feminism and Bollywood, and I loved discovering her art.
</p>

<p class="p1">
  I have to admit. I wasn’t expecting to discover (and love!) someone’s art along the way. That was a special surprise for me that I wouldn’t have gotten just by going to MoMA. Chitra had a solo show in 2009, and her art hasn’t been shown since. Given the scarcity of artists who share my identity, this became a cool way to find art that was relatable for me.
</p>

<p class="p1">
  I want you to have that experience too! If you’re looking for female American artists whose work has been shown at MoMA and who share your identity, query the database on my GitHub page. And please tell me what you find! I’d love to hear about the artists and art you find.
</p>
