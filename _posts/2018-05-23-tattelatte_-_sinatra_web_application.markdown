---
layout: post
title:      "TatteLatte - Sinatra Web Application"
date:       2018-05-23 23:56:23 +0000
permalink:  tattelatte_-_sinatra_web_application
---


I am nearing the end of what became a challenging and rewarding second project.  When I started the project I was most excited about revisiting HTML and CSS and how it incorporates with Ruby and Sinatra.  Although I was able to customize some of the features of my new web application, I look forward to moving on in the curriculum and continuing to revise my project and I learn more. 

When I started customized the HTML and CSS I honestly didn't know where to begin. It's been several months since I worked on those labs and lessons and I was starting to think I had forgotten everything! After some initial googling I found a very throughout article about CSS and after reading through the content I picked up right where I left off. The article also sited a website where there are free subtle background images available to download.  After that I kept everything simple and went with a modern font-family to go with the vibe of my web application. 

When it came to the concept of my project I had a few different ideas - some didn't really apply to the guidelines and some of them I couldn't make work within the scope of the project. So after some brainstorming I came up with TatteLatte. Named after my favorite coffeeshop in Boston it has my absolute favorite latte (iced hazelnut latte with almond milk). In my web application a user can sign up for an account - and then be redirect to a page where the user can create their favorite coffee beverages. The beverage form has a name, flavor, size, and description. 

Initially I built out my models with having two separate latte.rb and flavor.rb files. This became problematic and unnecessary and I removed the flavor.rb file. I went on to delete some of the files in the datebase and added some features then re-migrated the files for my new updated version. 

Here's the new create_latte file: 

```
class CreateLattes < ActiveRecord::Migration
  def change
    create_table :lattes do |t|
      t.string :name
      t.string :flavor
      t.string :size
      t.string :description
      t.integer :user_id
    end
  end
end
```

After I made this update everything else fell into place and my web application started to make sense. Although this is a simple web application I am proud of what I built and look forward to adding different features and making changes as I progress. 
