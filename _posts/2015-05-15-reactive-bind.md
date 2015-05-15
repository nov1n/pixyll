---
published:  false
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

As for the conversion, the formula is:  Celsius = (Fahrenheit - 32) / 1.8. Armed with this information 

This idiom is very common in Meteor hence I tried to capture it in a smart package called reactive-bind
