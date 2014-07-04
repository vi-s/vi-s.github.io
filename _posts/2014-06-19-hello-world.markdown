---
layout: post
title:  "Hello World!"
date:   2014-06-19 14:00:21
categories: summer internship ibm pittsburgh
---

This is my first post on my personal site. This site was generated using a static site generator known as Jekyll. I like Jekyll since it takes so much boilerplate code out of the mix. The Liquid templating engine is new to me, but not terribly difficult to get used to. There are also a wide range of themes and plugins that can be leveraged in a Jekyll project.

So far, this summer has been pretty relaxing. After I got off from school, I had roughly a month before my internship started. Since I had essentially no commitments during this time, I had the most chill month one could imagine. I spent some of my free time working on my website [gtcoursewatch.us][gtcoursewatch] adding new features and revamping the front-end. Me and a couple friends also went to a lakehouse about 30 minutes south of Atlanta and spent a couple days. It was so much fun!

I left Atlanta around June 1st for Pittsburgh, where I am right now. I'm here for an summer internship with IBM's big data lab, which is a component of their Watson initiative. Our lab specializes in search and maintains a product called "Watson Explorer." I specifically work on the DevOps team, which is basically the layer of software developers that interface between the system administrators and the other developers on the floor. My teammates are incredibly good with the command line. They spend the majority of their day in a full-screen terminal window with several tabs open. They don't even leave the terminal to write code since they use Vim, lol! I wasn't familiar with this level of engagement with the terminal, but I can see why they prefer it: It's all about efficiency.

I started out learning [Chef][chef] to contribute to IBMs Chef environment, and have recently been working on a Chef Reporting Rails application which essentially provides a dashboard for everyone on the floor to see what hardware nodes are currently non-responsive. The application detects non-responsive nodes by polling the Chef server every minute, and also sends out e-mails to the appropriate people upon detection.

I've essentially been using Ruby for just about everything since I started here at IBM, and am quickly growing to really appreciate the power that this language packs. The syntax is incredibly concise while still offering a large amount of flexibility. It's very object oriented, and even has some functional elements. For example, just like in JavaScript, functions are first-class citizens (at least through the use of a Proc object). All you need to do is define a lambda, or pass a block into a proc. Here's an example:

{% highlight ruby %}
#Creating a Lambda
l = -> (param) {puts param + " World!"}

#Creating a standard Proc
p = Proc.new {|param| puts param + " World!"}

l.call("Hello")
p.call("Hello")
{% endhighlight %}

Both print out ```Hello World!```. You can also pass in code blocks to functions to be executed with a ```yield``` statement like so:

{% highlight ruby %}
#Code block example
def hello_world()
    puts yield + " World!"
end

hello_world do
    "Hello"
end
{% endhighlight %}

This is essentially the Ruby analog of a JavaScript callback. The combination of functional and object-oriented really makes me like this language. I certainly see myself using it more in the future. 

Well, that's all for my first post, I hope everyone's summer is going well!


[gtcoursewatch]: http://gtcoursewatch.us
[chef]: http://www.getchef.com/