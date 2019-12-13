---
layout: post
title:      "Sinatra Portfolio Project - Ads"
date:       2019-12-13 19:04:13 +0000
permalink:  sinatra_portfolio_project_-_ads
---


For my Sinatra Portfolio Project I decided to create an Ads Place application.
Users can register and create new ads for things they would like to sell.
Anonymous users can browse the catalogue of ads and send messages to the seller
if they are interested in buying the product.

For signup/login/logout I used a gem called bcrypt for the purpose of hashing passwords and created two 
controllers (Registration,Session) that handle those processes.

After registration or login users are able to create new ads, edit or delete their current ads, or read messages 
that potential buyers have send them regarding the product they are selling. They can also delete those messages
and upload an image of the product. For the purpose of uploading images a gem CarrierWave was used. There is some 
initial preparation needed for the gem to work. We need to add a new column to the model that the image belongs to
and create a class that represents an CarrierWave uploader where we specify how to store an image, where to store
it; a list of acceptable file formats and so on.

Some other gems that I used in this application are Sinatra-Partial and Sinatra-Flash.
Sinatra-Partial is allowing you to use partials in your sinatra apps; see below an example:

```
<%= erb :'partials/_list', :layout => false, :locals => { :collection => current_user.ads } %>
```
 
Here we pass a collection which will be rendered in the form of ads of the current user. Of course we can also 
pass all kinds of parameters to the partial, as seen in an example below:

```
<%= erb :'ads/_form.html', :layout => false,
    :locals => { :ad => @ad, :conditions => @conditions, :categories => @categories, :action => @action,
    :button_text => "Create Ad"} %>
```

	
Sinatra-Flash allows you to add pop up messages to alert the user that something important happened.
We need to display the flash messages in our layout.erb file and enable sessions. When something 
happens in the controller action we send a message to the user by adding it to the hash.

```
  get '/sessions/logout' do
    session.clear
    flash[:notice] = "Bye!"
    redirect '/'
  end
```


For 404 errors I included a not_found method in an application controller with a custom error page that gets
displayed. I also used a before method to load resources based on the request method and path.

User input validations were handled with ActiveRecord and displayed to the user, see below:

```
<% if !!model && model.errors.any? %>
<div class="validation_errors">
  <ul>
    <% model.errors.each do |attribute,message|%>
    <li><%=attribute.capitalize %> <%=message %></li>
    <% end %>
  </ul>
</div>
<% end %>
```


I have learned a lot while working on this project. And I intend to deepen my understanding 
of ActiveRecord and Sinatra in the future so I can add new functionalities to the application.   







