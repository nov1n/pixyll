---
published: true
layout:     post
title:      WebStorm Live Templates for Meteor
date:       2015-04-26 23:30:39
summary:    Learn how to use Live Templates in Webstorm to speed up meteor development.
categories: tech meteor
---
## What are Live Templates
 
In many frameworks including meteor particular code structures show up again and again. [WebStorm](https://www.jetbrains.com/webstorm/) has a feature called Live Templates which can be seen as customizable autocomplete. We define an abbreviation which expands to our template text when we press the 'expand' key (tab by default).
 
Below we will go over some of the most useful Live Templates I've found. If you'd like to share your own, feel free to do so in the comment section below.
 
## Creating a Live Template
To create a Live Template launch WebStorm and head to File > Settings > Editor > Live Templates. Now press the ![Add]({{ site.url }}/images/new.png) on the top right and select Live Template. For each of the templates, find ![No context available]({{ site.url }}/images/no_applicable_context.png), click define and check JavaScript.
 
## 1. Getting and setting Session variables
<i>Abbreviation:</i> sget<br/>
<i>Description:</i> Get a session variable.<br/>
<i>Template text:</i>
```
Session.get($PARAMETER$)$END$
```

<i>Abbreviation:</i> sset<br/>
<i>Description:</i> Set a session variable.<br/>
<i>Template text:</i>
```
Session.set($PARAMETER$)$END$
```
 
## 2. Define template helpers
<i>Abbreviation:</i> thelp<br/>
<i>Description:</i> Define template helpers.<br/>
<i>Template text:</i>
```
Template.$PARAM$.helpers({
    $END$
});
```
 
## 3. Create template rendered callback
<i>Abbreviation:</i> trend<br/>
<i>Description:</i> Defines the template rendered function.<br/>
<i>Template text:</i>
```
Template.$PARAM$.rendered = function() {
    $END$
};
```

## 4. Creating a meteor collection
Now that we have seen the basic usage of Live Templates, let's create a more complex one. Start with the following:<br/>

<i>Abbreviation:</i> coll<br/>
<i>Description</i>: Creates a new meteor collection.<br/>
<i>Template text:</i>
```
$VARIABLE$ = new Meteor.Collection("$NAME$");
$END$
```

Now click on ![Edit variables]({{ site.url }}/images/editvars.png). In the expression field of NAME, add `decapitalize(VARIABLE)`. This produces the following result.<br/>
![Collection]({{ site.url }}/images/coll.gif)<br/>
As you can see the name of the collection turns into camelCase as we type.

The expression field is very powerful. The complete list of available functions can be found [here](https://www.jetbrains.com/webstorm/help/live-templates-2.html#d373781e466).

In our examples we only scratched the surface of Live Templates. Their flexibility and ease of use makes them a great addition to every programmer's toolbox.
