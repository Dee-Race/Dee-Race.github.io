---
layout: post
title:      "Adding jQuery to Rails - The ActiveModelSerializer That Broke Everything..."
date:       2018-09-07 19:50:13 +0000
permalink:  adding_jquery_to_rails_-_the_activemodelserializer_that_broke_everything
---


For my project I was excited to add jQuery features to my Rails app but has no idea the hurdles I would encounter with the Active Model Serializers. The AMS are honestly pretty straight forward, but there was a small glitch in my Comments Serializer that eventually was breaking all the new functionality. To start - you need to add a new gem to your gemfolder called ```active_model_serializer``` - then you can start adding the serializers that correspond to the models in your application. In the console, to add a new serializer you type ```rails g serializer Model```. The first serializer I added was Application. I started adding new features and preventing the default action of page reloads and soon I was clicking links and information was popping up without a reload. 

Fastforward to the struggles ... I ended up adding a second serializer and just like before I dropped to the console and typed ```rails g serializer Comment``` and thats when I started getting strange errors, and a NoMethodError that literally made no sense. To debug whatever was happening I tried making small changes but nothing worked. I commented out my JavaScript function and made sure that my Comment Form was working correctly. I put an alert and console.log(this) to make sure it was preventing the reload and that the form data was returning correctly. 

I had a feeling something was off with my serializers but I couldn't figure out what it was, because they're pretty straight forward. 

```
class ApplicationSerializer < ActiveModel::Serializer
  attributes :id, :company, :job_location, :description, :job_salary, :date_applied, :job_url

  belongs_to :job_title
  belongs_to :user
  has_many :comments
end
```

```
class CommentSerializer < ApplicationSerializer 
  attributes :id, :content, :application_id

  belongs_to :application
end

```

This is before I found the fix... everything seems to look good.....riiight.....

I then noticed that my CommentSerializer was inheriting from ApplicationSerializer - no idea how that happened BUT, I instantly changed it to inherited from ActiveModel::Serializer and everything was right in the world and in my application. 

```
class CommentSerializer < ActiveModel::Serializer 
  attributes :id, :content, :application_id

  belongs_to :application
end
```

Moral of the story - sometimes error messages aren't telling you everything, so make small changes and read through every line of code. 
