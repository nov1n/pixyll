---
published: false
---

---
layout:     post
title:      WebStorm Live Templates for Meteor development
date:       2015-04-26 23:30:39
summary:    In this post we see how to use Live Templates in Webstorm to speed up meteor development.
categories: tech meteor
---
## What are Live Templates
 
In many frameworks including meteor particular code structures show up again and again. [WebStorm](https://www.jetbrains.com/webstorm/) has a feature called Live Templates which can be seen as customizable autocomplete. We define an abbreviation which expands to our template text when we press the 'expand' key (tab by default).
 
Below we will go over 5 of the most useful Live Templates I've found. If you'd like to share your own, feel free to do so in the comment section below.
 
## Creating a Live Template
To create a Live Template launch WebStorm and head to File > Settings > Editor > Live Templates. Now press the IMAGE + on the top right and select Live Template.
 
## 1. Getting and setting Session variables
Abbreviation: sget
Description: Get a session variable.
Template text:
Session.get($PARAMETER$)$END$
 
Abbreviation: sset
Description: Set a session variable.
Template text:
Session.set($PARAMETER$)$END$
 
## 2. Define template helpers
Abbreviation: thelp
Description: Define template helpers.
Template text:
Template.$PARAM$.helpers({
    $END$
});
 
## 3. Create template rendered callback
Abbreviation: trend
Description: Defines the template rendered function.
Template text:
Template.$PARAM$.rendered = function() {
    $END$
};

## 4. Creating a meteor collection
Now that we have seen the basic usage of Live Templates, let's create a more complex one. Start with the following:
Abbreviation: coll
Description: Creates a new meteor collection.
Template text:
$VARIABLE$ = new Meteor.Collection("$NAME$");
$END$

Now click on EDIT VARIABLES. In the expression field of NAME, add decapitalize(VARIABLE). This produces the following result. As you can see the name of the collection turns into camelCase as we type
GIF

The expression field is very powerful. The complete list of available functions can be found [here](https://www.jetbrains.com/webstorm/help/live-templates-2.html#d373781e466).

In our examples we only scratched the surface of LiveTemplates. Their flexibility and ease of use makes them a great addition to a programmer's toolbox.

