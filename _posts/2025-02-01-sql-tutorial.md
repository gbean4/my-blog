---
layout: post
title:  "Unlock the Power of Data: An Easy Introduction to SQL"
date:   2025-02-04
description: This post is designed to help define basic SQL functions and guide you through your first SQL query as you enter the world of data science. You got this!!! 

---

<p class="intro"><span class="dropcap">T</span>here I was, Fall 2022, sitting in a large lecture hall in the basement of the Utah State business college. Unsure of my life’s path and my career opportunities, I was a hesitant bioengineering major in a random data science class, just trying to make it work—when suddenly my world was changed. Changed by what, you may ask? The beauty of SQL. </p>



### Introduction:
To put it simply, SQL (or Structured Query Language) is a programming language used for storing and processing information in a relational database. It’s exceptionally helpful in pulling and processing large amounts of data, even pieces of related data, for your use and interpretation. Lucky for us newbies, it's also easy to learn and immediately use to answer all of our deepest data science questions. 

In this post, we’ll start by defining some key elements of SQL and a SQL query (or question about a set of data). We’ll also get you a simple dataset to play with on your own while defining some helpful functions in your data manipulation journey. Let the games begin!

### Set Up:


<blockquote>Aenean lacinia bibendum nulla sed consectetur. Morbi leo risus, porta ac consectetur ac, vestibulum at eros. Cras mattis consectetur purus sit amet fermentum. Nulla vitae elit libero, a pharetra augue. Curabitur blandit tempus porttitor. Donec sed odio dui. Cras mattis consectetur purus sit amet fermentum.</blockquote>

Nullam quis risus eget urna mollis ornare vel eu leo. Cras mattis consectetur purus sit amet fermentum. Duis mollis, est non commodo luctus, nisi erat porttitor ligula, eget lacinia odio sem nec elit. Vivamus sagittis lacus vel augue laoreet rutrum faucibus dolor auctor.

## Unordered List
* List Item
* Longer List Item
  * Nested List Item
  * Nested Item
* List Item

## Ordered List
1. List Item
2. Longer List Item
    1. Nested OL Item
    2. Another Nested Item
3. List Item

## Definition List
<dl>
  <dt>Coffee</dt>
  <dd>Black hot drink</dd>
  <dt>Milk</dt>
  <dd>White cold drink</dd>
</dl>

Donec id elit non mi porta gravida at eget metus. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Maecenas faucibus mollis interdum. Donec sed odio dui. Cras justo odio, dapibus ac facilisis in, egestas eget quam.

## Table

| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |
| Header      | Title       |
| Paragraph   | Text        |

## Code Snippet

{%- highlight python -%}
def print_hi(name):
  print("Hi" + name)
print_hi('Tom')
#=> prints 'Hi, Tom'.
{%- endhighlight -%}


## Figure with Caption

<figure>
	<img src="{{site.url}}/{{site.baseurl}}/assets/img/touring.jpg" alt=""> 
	<figcaption>Figure 1. - This is an example figcaption</figcaption>
</figure>


{%- highlight html -%}
<figure>
	{% raw %}<img src="{{site.url}}/{{site.baseurl}}/assets/img/touring.jpg" alt="">{% endraw %}
	<figcaption>Figure 1. - This is an example figcaption</figcaption>
</figure>
{%- endhighlight -%}

