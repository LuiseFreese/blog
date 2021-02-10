# How to get started with HTTP requests in Power Automate

If you ever wondered what is an HTTP request and why you would want to know how this works - this post is made for you. 

## What is a HTTP request and why would I need it?

HTTP requests are a super powerful thing - not only in Power Automate so we will first need to understand what this is in order to determine why we would like to know how to use them. But wait - HTTP? 

### What is HTTP? 

Let's first get us all an the same page. HTTP is the acronym for **Hypertext Transfer Protocol**. Its purpose is to structure requests and responses over the internet (yeah, you heard of that one 😇) - Data needs to be transferred from Point A to Point B over the network. 

The transfer of resources (like html files, images, videos etc) happens with TCP - which again is anacronym, for **Transmission Control Protocol**. When you read this blog post, TCP manages the channels between your browser (hope you are using Microsoft Edge) and the server. TCP is used a lot for scenarios in which one computer sends something to another. Now what has TCP to do with HTTP? Think of HTTP as the command language for both computers so they are able to communicate. 

When you type a URL like **https://www.m365princess.com** into the address bar of your browser, your computer establishes first a TCP connection and then makes a request. We will call your computer now **client**. The request is a **HTTP GET** request, as we nicely ask to retrieve the website that the browser shall display. And as we send a nicely request, the server (site that you requested) will send a response and close the TCP connection. Of course, there are more methods than just the **GET** method, you will learn later more about methods **POST, PUT, DELETE**. 

## How do create a HTTP request in Power Automate

## Resources that might help you
