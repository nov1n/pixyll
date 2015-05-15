---
published:  true
layout:     post
title:      Two-way data binding in Meteor
date:       2015-05-15 14:04:11
summary:    Use the reactive-bind smart package to get two way data binding in Meteor.
categories: tech
---

## What is two-way data binding

Imagine we want to create a very simple Meteor app that converts Fahrenheit to Celsius. The user fills in a text field with the temperature in Fahrenheit, 
we display the result in Celsius right next to it. Easy enough right?
Let's see how we might do this. Start with a textfield and add an event-listener to the template. Whenever the input changes 
we take the value of the text field and store it in a Session variable named 'fahrenheit'.

As for the conversion, the formula is:  

`Celsius = (Fahrenheit - 32) / 1.8` 

Armed with this information we create a span and set its text equal to the value of the 'fahrenheit' Session variable we previously created.

This should give us something like this:

index.html
{% highlight html %}
<body>
  \{\{ >converter \}\}
</body>

<template name='converter'>
  <input id='fahrenheit' type='text'> <span id='celsius'>\{\{ getCelsius \}\}</span>
</template>
{% endhighlight %}

index.js
{% highlight javascript %}
Template.converter.events = {
  'keyup #fahrenheit': function (e) {
    var $target = $(e.target);
    var fahrenheit = $target.val();
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

This pattern is very common in Meteor and can be applied to all the different input elements. For this reason I tried to capture it in a smart package called reactive-bind. The package aims to
simplify binding input elements to Session variables forming a reactive two-way data binding. This means that other than the Session variable displaying the value of the input element, the input element will reflect changes made to the Session variable.

Several other packages are out there, aiming to solve the same problem. However they either required tedious setup, only offer one-way binding or are no longer maintained.

To use reactive bind we simply type
`meteor add nov1n:reactive-bind`
to add it to our project.

Now all we need to do is add a data attribute called 'data-binding' to our input element to bind it to a Session variable with the same name. To stick with our example we would now write:

index.html
{% highlight html %}
<body>
  {{ >converter }}
</body>

<template name='converter'>
  <input data-binding='fahrenheit' type='text'> <span id='celsius'>{{ getCelsius }}</span>
</template>
{% endhighlight %}

index.js
{% highlight javascript %}
Template.converter.helpers({
  getCelsius: function() {
    return Session.get('celsius');
  }
});
{% endhighlight %}

The code above achieves the exact same result as before, only now in a much cleaner, more expressive way. Note we did not have to write the event handlers at all. Only one input element was used in our example, but many applications may require more than that, each with different event handlers. reactive-bind will take care of the binding for you, hopefully speeding up development.

The package is still in its early stages so feel free to contribute, open issues or say thank you on [Github](https://github.com/nov1n/reactive-bind/) or [Atmosphere](https://atmospherejs.com/nov1n/reactive-bind).


