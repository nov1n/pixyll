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
 
Below we will go over 5 of the most useful Live Templates I've found. If you'd like to share your own, feel free to do so in the comment section below.
 
## Creating a Live Template
To create a Live Template launch WebStorm and head to File > Settings > Editor > Live Templates. Now press the ![Add]({{ site.url }}/images/new.png) on the top right and select Live Template. For each of the templates, click define ![No context available]({{ site.url }}/images/no_applicable_context.png) and check JavaScript.
 
## 1. Getting and setting Session variables
<b>Abbreviation: sget<br/>
<b>Description: Get a session variable.<br/>
<b>Template text:<br/>
```
Session.get($PARAMETER$)$END$
```

<b>Abbreviation:<b/> sset<br/>
<b>Description:<b/> Set a session variable.<br/>
<b>Template text:<b/>
```
Session.set($PARAMETER$)$END$
```
 
## 2. Define template helpers
<b>Abbreviation:<b/> thelp<br/>
<b>Description:<b/> Define template helpers.<br/>
<b>Template text:<b/>
```
Template.$PARAM$.helpers({
    $END$
});
```
 
## 3. Create template rendered callback
<b>Abbreviation:<b/> trend<br/>
<b>Description:<b/> Defines the template rendered function.<br/>
<b>Template text:<b/>
```
Template.$PARAM$.rendered = function() {
    $END$
};
```

## 4. Creating a meteor collection
Now that we have seen the basic usage of Live Templates, let's create a more complex one. Start with the following:<br/>

<b>Abbreviation:<b/> coll<br/>
<b>Description<b/>: Creates a new meteor collection.<br/>
<b>Template text:<b/>
```
$VARIABLE$ = new Meteor.Collection("$NAME$");
$END$
```

Now click on ![Edit variables]({{ site.url }}/images/editvars.png). In the expression field of NAME, add `decapitalize(VARIABLE)`. This produces the following result.<br/>
![Collection]({{ site.url }}/images/coll.gif)<br/>
As you can see the name of the collection turns into camelCase as we type.

The expression field is very powerful. The complete list of available functions can be found [here](https://www.jetbrains.com/webstorm/help/live-templates-2.html#d373781e466).

In our examples we only scratched the surface of Live Templates. Their flexibility and ease of use makes them a great addition to every programmer's toolbox.
