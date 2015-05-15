---
published:  true
layout:     post
title:      Two-way data binding in Meteor
date:       2015-05-15 14:04:11
summary:    Use the reactive-bind smart package to get two way data binding in Meteor.
categories: tech
---

Two-way data binding is a term becoming increasingly popular. It basically means the following two things. When data in the model changes, the view will update accordingly. In a similar fashion, changes to the view should propagate back to the model.

A possible application of two-way data binding can best be illustrated with an example. In this case we will use Session as the 'model' and an html input element as the 'view'.

## A simple example

Imagine we want to create a very simple Meteor app that converts Fahrenheit to Celsius. The user fills in a text field with the temperature in Fahrenheit, 
we display the converted temperature in Celsius next to it.
Let's see how we might do this. We start with a text field and add an event-listener to the template. Whenever the input changes 
we take the value of the text field and store it in a Session variable named 'fahrenheit'.

As for the conversion, the formula is:  

`Celsius = (Fahrenheit - 32) / 1.8` 

Armed with this information we create a span and set its text equal to the value of the 'fahrenheit' Session variable we previously created.

This should give us something like this:
<iframe height='21px' width='400' src='http://converter.meteor.com'></iframe>

index.html
{% highlight html %}
{% raw %}
<body>
  {{ >converter }}
</body>

<template name='converter'>
  <input id='fahrenheit' type='text'>
  <span id='celsius'>{{ getCelsius }}</span>
</template>
{% endraw %}
{% endhighlight %}

index.js
{% highlight javascript %}
Template.converter.events = {
  'keyup #fahrenheit': function (e) {
    var fahrenheit = e.target.value;
    var celsius = (fahrenheit - 32) / 1.8;
    
    Session.set('celsius', celsius);
  }
};

Template.converter.helpers({
  getCelsius: function() {
    return Session.get('celsius');
  }
});
{% endhighlight %}

## Reactive-bind

This pattern is very common in Meteor and can be applied to all the different input elements. For this reason I created a smart package called [reactive-bind](https://atmospherejs.com/nov1n/reactive-bind). As the name suggests it simplifies binding input elements to Session variables forming a reactive two-way data binding. This means that the Session variable will display the value of the input element and the input element will reflect changes made to the Session variable.

Several other packages are out there, doing similar things. However they either required tedious setup, only offer one-way binding or are no longer maintained.

## Rewriting the example
To use reactive-bind we type

`meteor add nov1n:reactive-bind`

in our project folder, to add it to our project.

Now all we need to do is add a data attribute called 'data-binding' with the name of the variable to our input element. This will bind it to a Session variable with the same name. To stick with our example we would now write:

index.html
{% highlight html %}
{% raw %}
<body>
  {{ >converter }}
</body>

<template name='converter'>
  <input data-binding='fahrenheit' type='text'>
  <span>{{ getCelsius }}</span>
</template>
{% endraw %}
{% endhighlight %}

index.js
{% highlight javascript %}
Template.converter.helpers({
  getCelsius: function() {
    var fahrenheit = Session.get('celsius');
    var celsius = (fahrenheit - 32) / 1.8;
    return celsius;
  }
});
{% endhighlight %}

The code above produces the exact same result as before in a much cleaner, more expressive way. Note that we did not have to write the event handlers at all. 

Only one input element was used in our example, but many applications may require more than that, each with different event handlers. reactive-bind will take care of the binding, so you can focus on writing your app.

For more examples involving multiple input elements click [here](http://reactive-bind-demo.meteor.com/).
The package is still in its early stages so feel free to contribute, open issues or say thank you on [Github](https://github.com/nov1n/reactive-bind/) or [Atmosphere](https://atmospherejs.com/nov1n/reactive-bind).


