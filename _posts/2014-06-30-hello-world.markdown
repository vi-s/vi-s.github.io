---
layout: post
title:  "Hello World!"
date:   2014-06-30 14:00:21
categories: summer internship ibm pittsburgh
---

This is my first post on my personal site, which was generated using a static site generator known as Jekyll. I like Jekyll since it takes so much boilerplate code out of the mix. The Liquid templating engine is new to me, but not terribly difficult to get used to. There are also a wide range of themes and plugins that can be leveraged with Jekyll.

So far, this summer has been pretty relaxing. After I got off from school, I had roughly a month before my internship started. Since I had essentially no commitments during this time, I had the most chill month one could imagine. I spent some of my free time working on my website [gtcoursewatch.us][gtcoursewatch] adding new features and revamping the front-end. Me and a couple friends also went to a lakehouse about 30 minutes south of Atlanta and spent a couple days. It was so much fun!

I left Atlanta around June 1st for Pittsburgh, where I am right now for a summer internship with IBM. The lab I work in specializes in search and is a component of IBM's Watson initiative. I specifically work on the DevOps team, which is basically the layer of software developers that interface between the system administrators and the other developers on the floor. My teammates are incredibly good with the command line. They spend the majority of their day in a full-screen terminal window with several tabs open. They don't even leave the terminal to write code since they use Vim, lol! I wasn't familiar with this level of engagement with the terminal, but I can see why they prefer it: It's all about efficiency.

I started out learning [Chef][chef] to contribute to IBMs Chef environment, and have recently been working on a Chef Reporting Rails application which essentially provides a dashboard for everyone on the floor to see what hardware nodes are currently non-responsive. The application detects non-responsive nodes by polling the Chef server every minute, and also sends out e-mails to the appropriate people upon detection.

I've been using Ruby for just about everything since I started here at IBM, and am quickly growing to really appreciate the power that this language packs. The syntax is incredibly concise while still offering a large amount of flexibility. It's very object oriented, and even has some functional elements. For example, just like in JavaScript, functions are first-class citizens (at least through the use of a Proc object). All you need to do is define a lambda, pass a block into a proc, or even reference an existing method. Here's an example:

{% highlight ruby %}
#Creating a Lambda
l = -> (param) {puts param + " World!"}

#Creating a standard Proc
p = Proc.new {|param| puts param + " World!"}

l.call("Hello")
p.call("Hello")

#or even reference an existing method
def hello_world(param)
  puts param + " World!"
end

method_ref = method(:hello_world)
method_ref.call("Hello")
{% endhighlight %}

All print out ```Hello World!```. You can also pass in implicit code blocks to functions to be executed with a ```yield``` statement like so:

{% highlight ruby %}
#Implicit code block example
def implicit_hello_world()
  puts yield + " World!"
end

implicit_hello_world do
  "Hello"
end
{% endhighlight %}

If no block is provided, the method will raise an exception upon encountering the ```yield``` statement. 

You can also explicitly pass in a code block by passing a parameter prepended with an ```&``` symbol. Any parameter prepended with ```&``` instructs the interpreter to  call the ```to_proc``` method on itself to convert it to a ```Proc``` object. So that's how we can have access to our code block in the form of a ```Proc``` object within our method.

{% highlight ruby %}
#Explicit code block example
def explicit_hello_world(&my_block)
  my_block.call + " World!"
end

explicit_hello_world do
  "Hello"
end
{% endhighlight %}

Code blocks are essentially the Ruby analog of a JavaScript callback.

```&:symbol``` is a commonly used pattern utilizing the above defined idea. In the base C implementation of Ruby, the ```Symbol``` class has a special implementation of the ```to_proc``` method. The result is that whatever method was specified by ```:symbol``` is found and converted into a ```Proc``` object. Thus, the following two are equivalent:

{% highlight ruby %}
#Without shortcut
%w[this is a test array].map{|s| s.upcase}

#With shortcut
%w[this is a test array].map(&:upcase)
{% endhighlight %}

Both return the input array in all-caps form. Pretty neat!

The combination of functional and object-oriented really makes me like this language. I certainly see myself using it more in the future. 
Well, that's all for my first post, I hope everyone's summer is going well!

[gtcoursewatch]: http://gtcoursewatch.us
[chef]: http://www.getchef.com/