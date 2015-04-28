---
published: false
---

---
layout:     post
title:      WebStorm Live Templates for Meteor development
date:       2015-04-26 23:30:39
summary:    Learn how to use Live Templates in Webstorm to speed up meteor development.
categories: tech meteor
---
## What are Live Templates
 
In many frameworks including meteor particular code structures show up again and again. [WebStorm](https://www.jetbrains.com/webstorm/) has a feature called Live Templates which can be seen as customizable autocomplete. We define an abbreviation which expands to our template text when we press the 'expand' key (tab by default).
 
Below we will go over 5 of the most useful Live Templates I've found. If you'd like to share your own, feel free to do so in the comment section below.
 
## Creating a Live Template
To create a Live Template launch WebStorm and head to File > Settings > Editor > Live Templates. Now press the ![Add](images/add.png) on the top right and select Live Template. For each of the templates, click define ![No context available](images/no_applicable_context.png) and check JavaScript.
 
## 1. Getting and setting Session variables
Abbreviation: sget
Description: Get a session variable.
Template text:
{% highlight ruby %}
Session.get($PARAMETER$)$END$
{% endhighlight %}

Abbreviation: sset
Description: Set a session variable.
Template text:
{% highlight ruby %}
Session.set($PARAMETER$)$END$
{% endhighlight %}
 
## 2. Define template helpers
Abbreviation: thelp
Description: Define template helpers.
Template text:
{% highlight ruby %}
Template.$PARAM$.helpers({
    $END$
});
{% endhighlight %}
 
## 3. Create template rendered callback
Abbreviation: trend
Description: Defines the template rendered function.
Template text:
{% highlight ruby %}
Template.$PARAM$.rendered = function() {
    $END$
};
{% endhighlight %}

## 4. Creating a meteor collection
Now that we have seen the basic usage of Live Templates, let's create a more complex one. Start with the following:
Abbreviation: coll
Description: Creates a new meteor collection.
Template text:
{% highlight ruby %}
$VARIABLE$ = new Meteor.Collection("$NAME$");
$END$
{% endhighlight %}

Now click on ![Edit variables](images/editvars.png). In the expression field of NAME, add decapitalize(VARIABLE). This produces the following result.
![Collection](images/coll.gif)
As you can see the name of the collection turns into camelCase as we type
GIF

The expression field is very powerful. The complete list of available functions can be found [here](https://www.jetbrains.com/webstorm/help/live-templates-2.html#d373781e466).

In our examples we only scratched the surface of Live Templates. Their flexibility and ease of use makes them a great addition to every programmer's toolbox.