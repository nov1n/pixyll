---
published: true
layout: post
date: {}
summary: Simplify debugging in meteor with JetSetter and Mongol.
categories: tech
---


Tell me if this sounds familiar. As you hack away on your killer meteor app, something unexpected happens. Determined to figure out what caused it, you open the devtools in your favorite browser. You start with `Session.get('someVariable')` which returns the expected value. After clicking six buttons and filling out a text field, you check again. Nothing out of the ordinary. Maybe it is that `spaceships` collection you created minutes earlier. A quick `Spaceships.find().fetch()` shows an array of all the documents. Expanding all of them, the last one appears to have an undefined field. This is what caused the unexpected behavior. You add some validation before documents are saved and the app works as it should.

## The problem

This is the debugging flow a lot of us meteor developers tend to use. And it is far from optimal. Tediously repeating the same statements in the console to keep track of Session variable state. [Watch Expressions](http://albertlee.azurewebsites.net/using-watch-tools-in-chrome-dev-tools-to-improve-your-debugging/) may make your life a tiny bit easier, but not much. As your app grows the amount of Session variables and collections grows along with it. 

## The solution

Luckily Max Savin created a set of tools called [Meteor Toys](http://meteor.toys/). It aims to solve common problems meteor developers face. The whole suite consists of 10 'widgets', as he calls them. In this post I'd like to discuss the two free widgets in the suite, which in my opinion also happen to be the most useful ones. 

## Mongol

The first one is [Mongol](https://github.com/msavin/Mongol). This is a visual editing tool for mongodb collections in meteor. This may sound a bit fuzzy which is why we're going to look at what it does together. For those of you who like to follow along, add the package to your meteor project with the following command.

`meteor add msavin:mongol`

Now as your app restarts hit `Ctrl + M` and a grey list should appear at the bottom left of your screen. In this list you find all the collections your meteor app consists of.

![Mongol]({{ site.url }}/images/mongol.gif)

Mongol allows you to visualize, edit, remove and duplicate documents in a breeze. This is much faster and easier than fiddling around in the console.

## JetSetter

The second widget is JetSetter. This one allows us to see all the Session variables and their contents. It also makes it very easy to edit or delete them.  To install it run:

`meteor add msavin:jetsetter`

Now after hitting `Ctrl + M` another list will appear on the bottom right of the screen. This is JetSetter. It looks and works a lot like Mongol.

![JetSetter]({{ site.url }}/images/jetsetter.gif)

I am not going to explain every single feature. Instead I encourage everyone to play around with the tools. On the [Meteor Toys](http://meteor.toys/) website you can find the other eight tools. The complete bundle costs $99.
