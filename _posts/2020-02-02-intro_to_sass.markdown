---
layout: post
title:      "Intro to Sass"
date:       2020-02-02 17:04:51 +0000
permalink:  intro_to_sass
---


As I was working on my Sinatra project I decided to give Sass a try.
What is Sass you say? Basically Sass (makes CSS fun again:)) is an extension of CSS, adding
nested rules, variables, mixins, selector inheritance. Sass is a preprocessor scripting language that is 
interpreted or compiled into CSS. Other preprocessors you might know are Less and Stylus. 

In Sass you don't have to repeat the same selectors over and over again and that is accomplished by nesting.

SASS

```
.navigation 
{
	display: flex;
	align-items: center;
	a
	{
		color:#fff;
		text-decoration: none;
		text-transform: capitalize;
	}
	ul
	{
		list-style-type: none;
		padding-right: 1rem;
	}
	li 
	{
		background-color: $grey-color;
		display: inline;
		padding: 1rem;
	}
}
```


CSS 

```
.navigation 
{
	display: flex;
	align-items: center;
}	
.navigation a
{
	color:#fff;
	text-decoration: none;
	text-transform: capitalize;
}
.navigation ul
{
	list-style-type: none;
	padding-right: 1rem;
}
.navigation li 
{
	background-color: $grey-color;
	display: inline;
	padding: 1rem;
}
```


Both CSS and Sass include variables that we can use in the code.

CSS

```
:root{
	--grey-color:#1F2833;
}
```

usage: 
`background-color: var(--grey-color);`
  
SASS 

`$grey-color:#1F2833;`

usage: 
`background-color: $grey-color;`

There are major differences between the two. Sass variables are all compiled away by Sass while CSS 
variables are included in the CSS output. CSS variables can have different values for different 
elements, but Sass variables only have one value at a time. Sass variables are imperative, which means 
if you use a variable and then change its value, the earlier use will stay the same. CSS varibles 
are declarative, which means if you change the value, it'll affect both earlier uses and later uses.

Another cool feature of Sass are the functions in which we can manipulate colors.
We can lighten or darken colors by percentages.

```
darken($grey-color,10%);
lighten($grey-color,10%);
```

Saturate, desaturate, adjust-hue and so on.

These are just some examples of what Sass offers, and I have only diped my toes into it so 
there is much more to explore, which I intend to in my next project.

  
