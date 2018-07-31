---
layout: post
title:      "JobTrackr - Rails Portfolio Project"
date:       2018-07-31 15:05:26 +0000
permalink:  jobtrackr_-_rails_portfolio_project
---


This project came with its many hurdles but I am proud to say I am happy with the outcome and what I've created. 


For this third portfolio project I spent a few days brainstorming application ideas. I wanted something I could actually use and something that was realistic - and something potentially others would also find helpful. The outcome - JobTrackr. As someone who will be on the job hunt fairly soon I know how important it is to keep track of application information when you're applying for jobs. My web application does just that. When you are brought to the home page a user can sign up via Facebook (woohoO), signup with an email, or login if they are a returning user. JobTrackr has a form where you can input all the necessary information for organizing a job application. Below is the current form : 

```
<%= form_for @application do |f| %>
    <%= f.label :company, "Company" %>
    <%= f.text_field :company %><br>

    <%= f.collection_select :job_title, JobTitle.all, :id, :title %>

    <%= f.fields_for :job_title do |f| %>
        <%= f.label :title %>
        <%= f.text_field :title %><br> 
        <% end %>

    <%= f.label :job_location, "Location" %>
    <%= f.text_field :job_location %><br>

    <%= f.label :job_salary, "Salary" %>
    <%= f.text_field :job_salary %><br>

    <%= f.label :job_url, "Job Posting URL" %>
    <%= f.text_field :job_url %><br>

    <%= f.label :description, "Description" %>
    <%= f.text_field :description%><br>

    <%= f.label :date_applied, "Date Applied" %>
    <%= f.text_field :date_applied %><br>

    <%= f.submit %><br>
    <% end %>
```

I have a drop down menu of job titles which a user can select from. In addition - when a user is adding several applications, the user can view all their job titles with their respective company and a user is able to see which job titles are the most popular in their applications. 

```
<h3>Here are your most popular job titles:</h3>

<ul>
<% @job_titles.most_popular.each do |job_title, count| %>
    <li><%= job_title %> - <%= count %></li>
    <% end %>
</ul>
```

This is a great way to gather information about the types of jobs you are applying for and can help with searching for the right job for a user. Overall I really enjoyed creating this application and I am excited to keep adding to in the future when my knowledge expands! 
