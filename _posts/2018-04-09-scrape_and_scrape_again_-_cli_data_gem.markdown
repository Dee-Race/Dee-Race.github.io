---
layout: post
title:      "Scrape and Scrape Again - CLI Data Gem "
date:       2018-04-09 22:46:37 +0000
permalink:  scrape_and_scrape_again_-_cli_data_gem
---


If you couldn't tell by the title of this post, scraping was a big deal for my project. But before I get into that, I'll start off by describing my project process. 

To prepare for the upcoming project I attended CLI Study Groups while I was finishing up the Object Orientation lessons. While listening in on my first project study group, it became apparent that I clueless about project requirements, project length, and where to even start. And then I attended another study group, and another one, and another one. Slowly things started to become familiar and before I was ready to start the project I had come up with my concept! Traveling is a huge part of my life and something I love to do. So with that in mind I decided to create a CLI Gem describing the worlds best road trips. This concept was also inspired by an upcoming trip, which was listed as one of the best in the world. I decided that if my project concept got me excited then I would be able to continue and push through the rough parts I didn't even see coming. 

Once I had completed all the Object Oriented Ruby lessons I finally arrived at the CLI Data Gem Project. The steps and requirements are displayed in numbered form and one of the first recommendations is to watch a CLI Walkthrough video made by Avi.  I found the video extremely beneficial in creating a project flow and how to lay out the project thought process.  During my brainstorm portion of the project, I created a list of 5 websites I could potentially scrape for my project - all the websites had some pretty EPIC road trips. 

Off I went - I had outlined the CLI portion of the project and was similtaneously getting started on the scraper.  I soon realized I didn't know enough about scraping and found myself stuck. I started taking notes of which websites were returning what value and how I was iterating through the objects. I kept coming up short and felt like I was taking one step forward and two steps back. After talking with technical coaches I realized - "it's not me, it's you".  And the you I am referring to is the website. Not that all websites should be made for scraping, but I learned that the ones I had chosen were poorly organized! With each day, I swapped the website I was scraping and altered my methods. I started getting REALLY close to a solution where all the road trips were being displayed in the CLI but the descriptions were not. With a different website I tried using the highlights of the road trips but while inspecting the site I realized I was heading into the abyss of divs with no rational way out. 

I thought I had settled on the third website I scraped as "the one" but this proved to be so wrong. The entire process went full circle and I actually started seeing some amazing results with the first website I scraped (YAY!).  My initial error in scraping this site was in my lack of knowledge in gsub. Without gsub, the return value of the individual road trips were filled with extra space and unnessary characters. In addition, I found that I needed to use gsub for the descriptions to output my desired result. 

Below is a code snippet of a portion of my scraper for website number 3 - definitely NOT the one 

```
 trip_name = road_trip.css("h2").text.gsub("\u2013", "").gsub("\u00A0", "").split("#") 
 trip_highlights = road_trip.css("blockquote p em").text.gsub("\u2013", "").gsub("\u00A0", "")
```

I could go on and tell you about how this website was a mess and how my objects were never going line up, but I'll refrain and get to the good stuff. 

Below is what I found to be exactly what I was looking for - The One (gsub and all) 

```
trip.road = road_trip.css("h2").text.strip.gsub("\n", "").gsub("Book a Hotel", "")
trip.description = road_trip.css("p").text.gsub("\u2019", " ").gsub("\u00A0", " ")
```

I added the .gsub("Book a Hotel", "") after everything seemed to be working because one of the trips displayed this text during the CLI portion of the project. 

So here I am, finished with the first of several final projects and I couldn't be happier! For students just starting this project or are still in the thick of it - keep going, keep scraping, and find yourself a decent website! And if you're thinking of planning your next road trip, take a peak at my gem to get some inspiration. 


