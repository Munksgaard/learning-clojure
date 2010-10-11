---
---

Learning Clojure
================

This is where i will be documenting my experinces with Clojure, the
lisp-like language for the JVM.

Introduction
============

What is Clojure?
----------------

So, what is Clojure? From Wikipedia:

> Clojure is a modern dialect of the Lisp programming language. It is
> a general-purpose language supporting interactive development that
> encourages a functional programming style, and simplifies
> multithreaded programming.

Clojure is very new programming language (first made public in
2007). Therefore it is still in very active development, and many
exiting changes are happening all the time. This also means, that it
can be quite hard to keep up with all the changes. A new version may
break functionality in older versions, or have restructured the way
certain mechanics work.  
It is therefore a good idea to focus on one version of clojure and get
familiar with it before you move on to more recent versions.


What is the purpose of this document?
-------------------------------------

This document is created primarily with the purpose of helping me
learn Clojure.  
The idea is, that the process of documenting all my
experiences with the language, i might be able to get a better
understanding of it. 
This means that sometimes i might not go into detail with specifics
which i didn't care about, or maybe my installation guide isn't
fulfilling for some or something else might be wrong, inacurate,
inspecific or just plain bad.  
The hope is, that someone else might find this guide useful, but it's
not the purpose or the goal.


Target audience
---------------

Me.
I will assume that any readers of this document have basic
understanding of programming concepts, has programmed before in some
other language, possibly a Lisp but not necessarily and has some
computer savvy. 


Tools, technical prerequisites etc.
-----------------------------------

I will assume that the reader uses some form of Linux. I myself will
primarily be using Gentoo linux, but i will go through all the basic
steps of installation and setup on a virtual machine with Ubuntu 10.10
on it. I will therefore be supplying installation commands for Ubuntu,
but i will assume that if you use anything other than Ubuntu, you know
how to install things.  
Most commands will be executed at the command line, so i'll assume
that you're familiar with that.

I will be using Clojure 1.2.0 as that is the stable release at the
time of writing. I will be using cake for project management (more on
that later) and emacs (22 or 23) for my development environment. I
will assume that you are familiar with emacs, but i will probably be
describing some basic tips and tricks for working with Clojure.  

Later on, when we try learning how to code in Clojure, we'll be using
a few problems from [Project Euler](http://www.projecteuler.net
"Project Euler").


Getting started
===============

Basic Installation
------------------

Getting a good working environment in which to work with Clojure has
been one of the really hard things to do for me. Classpaths, java
dependencies, and third party libraries confused me to the point where i
was willing to quit.  

To get rid of all these problems, we're going to use cake, a build
tool for Clojure, that's designed to automate third party libraries,
dependencies, building and distributing.

But first of all, we're going to install java (sun-java, since
everything else gives me problems...).  
On ubuntu, edit <code>/etc/apt/sources.list</code> and uncomment the line that
says:

    # deb http://archive.canonical.com/ubuntu maverick partner

Now run

    sudo apt-get update
    sudo apt-get upgrade
    sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-bin libjline-java

_Note that we also install jline, so we can use the Clojure repl
properly from the command line._

Now you need to install ruby-gems:

    sudo apt-get install rubygems
    sudo ln -s /usr/bin/ruby1.8 /usr/bin/ruby


_Note that apparently ruby doesn't install itself on a proper path, so
in order for cake to work properly, we need to create the symlink._
_
Now we're ready to install cake!

    sudo gem install --bindir /usr/bin cake

Now we're actually ready to create our first Clojure project!
Go in to the directory where you want your project (for testing
purposes, i usually use <code>~/tmp/</code>).  
This is where we will create our project.

    cake new hello-clojure

The first time you run cake, it will take some time, since cake will
fetch and install Clojure. Don't worry, this is only the first time.

Cake has now created a new directory called hello-clojure, inside
which is your new Clojure project. For now, we will ignore all the
files and directories inside hello-clojure. Go into the src directory,
create a new directory named "hello-clojure" and create a file called
"core.clj" inside that directory. In this file, simply write:

    (ns hello-clojure.core)

    (println "Hello world! Kind regards from Clojure!")

To run this file, simply type <code>cake run core.clj</code>.

Note, that cake isn't interpreting the Clojure sourcecode or anything,
it's simply passing the files to a Clojure process running in the
background.

This is also how you run other clj files, they don't need to be in a
project. Just do "cake run \<someClojureFile\>.clj" to run it.

If you want a REPL (Read Eval Print Loop, like pythons commandline
interpreter) simple issue the command "cake repl"




