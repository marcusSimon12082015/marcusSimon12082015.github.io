---
layout: post
title:      "'Comic Review Corner - Rails Portfolio Project'"
date:       2019-05-04 19:53:45 +0000
permalink:  comic_review_corner_-_rails_portfolio_project
---


For my Rails Portfolio Project I decided to create a Comic Review Corner.
We have two roles defined for User which is standard and administrator.
Administrator can create new comics which include artists that created 
the comic, notebale characters that appear in the comic and the comic book cover.

When the standard user signes up he gets 100 credits which he can use to buy a number of comics.
When the comic is added to the users collection he is able to write a review about the comic 
and share his thougths on the story and the characters.

For signup/login/logout devise was used with adding a sign_up form to the home page.
In this case Github is used as a third party signup/login provider.
For that to work we had to add a few helper methods to our ApplicationController, like 
resource_name, resource_class,resource, devise_mappping, and override a few methods in 
the RegistrationsController(create) and SessionsController(after_sign_in_path_for).

So after the user is signed up he is redirected to comics index page where he can pick 
his favorite comics if he has enough credits of course. When he adds one he can write a review 
for it in a form of a nested resource -> comics/6/reviews/new, and from the comic page we can access
all of the reviews -> comics/2/reviews. 

There were a few notebale gems used in the application, like 
Carrierwave for image uploading and nested_form_fields for dynamic adding of form fields.

For my class method I created a best_seller method that displays most owned comics. 

I learned a lot while working on this project. And I intend to add more to it in the future 
in the form of better search options for the user. Also improve the look and feel of the whole 
application with css styling.
