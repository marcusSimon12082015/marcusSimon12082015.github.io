---
layout: post
title:      "My first time with FlexBox"
date:       2019-12-14 14:40:40 +0000
permalink:  my_first_time_with_flexbox
---


When I started working on my Sinatra Portfoli Project I decided to try out this thing called FlexBox.
So FlexBox is a "new" :) module in CSS3 that provides a more efficient way to lay out, align and distribute space among items in a container.

We have a Flex container and Flex items. A Flex item can also be a flex container. We define a Flex container by:

```
.container 
{
	display: flex;
}
```
We can set direction with:
```
.container 
{
	flex-direction: row | row-reverse | column | column-reverse;
}
```
and so on. There are also flex-wrap, justify-content, align-items, align-content.

For items we can set order, how much they can grow with flex-grow, shrink and align self.

```
.item 
{
	order: 0;
	flex-grow: 0;
	flex-shrink: 0;
	flex-basis: 0;
	align-self: auto;
}
```

So in my project I used FlexBox for basic examples as centering my forms, styling header and positioning elements within it and creating 3x3 grids:

```
.main_content 
{
	display: flex;
	flex-wrap:wrap;	
}

.ad_content 
{
	flex: 0 0 32%;
}
```

In the future I plan to look at CSS Grid and maybe combine both of them in a project.

