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

Now we're ready to install cake!

    sudo gem install --bindir /usr/bin cake
    cake deps

The last command will fetch clojure and clojure-contrib for us.

Hello World
-----------

Cake is a build management tool, but i've found that it also eases
using Clojure normally.  
Therefore, we're going to use cake to invoke Clojure.

Create a file called hello-clojure.clj with the following in it:

    #!/usr/bin/env cake
    (println "Hello world! Kind regards from Clojure!")


The first line is just the standard line for telling linux how to
execute it. Clojure recently added the feature to ignore such a line,
even though it's not valid Clojure code.

To run this file, simply type <code>cake run core.clj</code>.  
You can also run it by making it executable and doing
<code>./hello-clojure.clj</code>.

__Note:__ Every time you start up cake for the first time after a
reboot (or a 'cake kill') cake has to load the JVM. That means that
the first call to cake will always be a little slow, it might take a
few seconds, but after that it'll be fast!

Starting a REPL
---------------

Getting to a REPL (Read Eval Print Loop) is as easy as

    cake repl

Starting a new project
----------------------

Although you can work on simple scripts and one-liners in a file by
itself, for anything else you should use a project.  
Creating a project is as easy as:

    cake new project-name

Creating a project makes it a lot easier to handle dependencies,
create distributable jar-files and more.  
Create one now called <code>clojure-test</code>.  
Inside the project directory, you will find a lot of files, but of
primary interest for you is <code>project.clj</code>. This is where
you will define dependencies, what classes to run and a lot more.
For now, you'll note that, per default, <code>project.clj</code>
states that your project is called clojure-test, has the version
0.0.1-SNAPSHOT (the -SNAPSHOT part means that it's not a final
version), that you need to write a description, and that it has
clojure 1.2.0 as a dependency.  
To add dependencies, simply add them to the vector with name and
version. For more information about the syntax of project.clj and
other options you can put in there, refer to [leiningens
sample.project.clj](http://github.com/technomancy/leiningen/blob/master/sample.project.clj)
(leiningen is another build management tool like cake, and cake uses
leiningens syntax for project.clj).

__TODO:__ Write more about projects, maybe a whole section about
creating jars etc. Also the default project (~/.cake/project.clj)

Emacs integration
-----------------

slime, swank, cake swank

Ressources
==========

This is a collection of the best documentation on Clojure (1.2.0) and
related subjects i've been able to find.

[Clojuredocs Quickref](http://clojuredocs.org/quickref/Clojure%20Core)  
[Clojure-contrib 1.2.0
documentation](http://clojure.github.com/clojure-contrib)  
[Clojure on Wikipedia](http://en.wikipedia.org/wiki/Clojure)  
[Cake documentation on Github](http://github.com/ninjudd/cake)  
[Clojure 1.2.0 documentation](http://clojure.github.com/clojure)  
[Clojure cheatsheet](http://clojure.org/cheatsheet)  
