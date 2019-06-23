---
layout: post
title:      "Rails App with jQuery Comic Review Corner enhanced"
date:       2019-06-23 15:51:25 -0400
permalink:  rails_app_with_jquery_comic_review_corner_enhanced
---


For this project we had to enhance the previous project and add jQuery 
to make our application more dynamic. To make all of this possible we had to make
a few adjustments on the server side. The first one is serving JSON. Here we are introduced 
to Active Model Serializers. First we need to add a gem called active_model_serializers to our
Gemfile and generate serializers with rails generate serializer review. This generates a new class 
where you can specify what to serialize and how from our model.
```
class ReviewSerializer < ActiveModel::Serializer

  attributes :id,:title,:content,:comments
  belongs_to :user
  belongs_to :comic

  def comments
    ActiveModel::SerializableResource.new(object.comments, each_serializer: CommentSerializer)
  end

  attribute :links do
    {
      next: generate_next_link,
      previous: generate_previous_link
    }
  end

  def generate_next_link
    object.next_link(instance_options[:comic_id])
  end

  def generate_previous_link
    object.previous_link(instance_options[:comic_id])
  end
end

```

In the controller we need to add a new line to our respond_to block so that we can send a json response back to the client.
We request and receive JSON with $.ajax, $.get, $.post jQuery functions and handle the responses accordingly.
For that purpose we created two JS classes(review,comments) that handle rendering for us based on the data we receive.

With this project I have only scratched the surface of what jQuery can do, but I am eager to learn more and add 
new functionality to an existing app.
