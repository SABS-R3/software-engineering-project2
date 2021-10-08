---
title: "Tree Generation App"
teaching: 30
exercises: 0
questions:
- "For NERC/DPT students, What is the project you will be working on for week 3?"
objectives:
- "Explain the background of the project."
keypoints:
- "Your group project is to implement and deploy a Python application to specify and 
  visualise a number of fractal/biological patterns from the book \"The Algorithmic 
  Beauty of Plants\"."
---

A [recent survey](https://zenodo.org/record/495360#.YV8aDHVKhH5) of RCUK-funded research 
being undertaken in 15 Russell Group universities found that 92% of researchers used 
research software of some kind. However, the majority of these researchers are probably 
unfamiliar with programming, or perhaps just Python in particular, so using a library 
written in Python is not going to be a suitable option for most of the potential users 
of your research software. 

A graphical user interface (GUI) can make your research software accessible to everyone 
with a computer. By increasing the base of potential users, it can ultimately increasing 
both citations and impact.

There are generally two approaches to developing GUIs. One approach is to write a web 
application written in Javascript that a user can view like a normal webpage using their 
browser. This is a popular approach as the user does not need to install any software. 
The other approach is to write a desktop application using one of the many GUI libraries 
(e.g. [Qt](https://www.qt.io/). Python has a number of GUI libraries, so we will be 
using this approach.

During the week, you will work in groups to implement an easily installable desktop GUI
using Python. The web application will allow users to generate and visualise branching 
tree structures using L-Systems.

## Tree Modelling with L-Systems

[*The Algorithmic Beauty of Plants*](http://algorithmicbotany.org/papers/#abop), a 
textbook from 1990, is concerned with two main factors that organise plant structures, 
that of *developmental algorithms* that describe plant development in time, and that of 
*self-similarity*, where each individual element of a shape is similar to the whole. 

The book starts by introducing 
[L-Systems](http://algorithmicbotany.org/papers/abop/abop-ch1.pdf), introduced in 1968 
by Lindenmayer, which provides a formal language for describing the evolution of plant 
geometry over multiple iterations. This is a well-known language for plant generation 
and is widely used in industry in programs such as 
[SpeedTree](https://store.speedtree.com/) and [X-frog](http://xfrog.com/). [Chapter 
2](http://algorithmicbotany.org/papers/abop/abop-ch2.pdf) covers the application of 
L-systems in the generation of branching patterns in trees, and gives a number of 
different examples.

L-systems are a popular method for the automatic generation of beautiful fractal 
patterns, particularly for generation of patterns that exist in biology, and have been 
implemented in many different computer languages. Javascript is no exception, and there 
are [Javascript L-system libraries](https://github.com/nylki/lindenmayer), as well as 
online tutorials of [visualising 
L-systems](https://eng.qualia.com/drawing-fractals-in-the-browser-with-l-systems-and-es6-6cecfd74e084)
in the 
[browser](https://hardlikesoftware.com/weblog/2008/01/23/l-systems-in-javascript-using-canvas/)

## Python GUI libraries

[These](https://dev.to/codesharedot/best-python-framework-for-building-a-desktop-application-and-gui-58n5) 
[pages](https://docs.python-guide.org/scenarios/gui/) contain information about many 
different Python GUI libraries and links to tutorials showing you how to use them. You 
can use whichever library you wish, but note that 
[Tkinter](https://docs.python.org/3/library/tkinter.html) has the advantage of being 
part of the Python standard library and is thus the de-facto standard Python GUI 
library. [PyQt](https://wiki.python.org/moin/PyQt) is also very popular as it is based 
on the well known and well regarded [Qt](https://www.qt.io/) GUI framework for C++, and 
can be used in conjunction with the [fman](https://build-system.fman.io/) build system.

## Packaging a python desktop application

Its no use writing a GUI if it can only be used on a machine with Python already 
installed, or only runs on Linux. Additional effort must be made to make it 
cross-platform across Linux, Mac and Windows, and easily installed by anyone without 
specific knowledge of Python tools such as `pip`.

There are a number of third-party libraries for writing cross-platform Python 
applications, two examples are [Pyinstaller](https://www.pyinstaller.org/), and 
[fman](https://build-system.fman.io/). The former is a very flexible library for 
bundling up any Python application into stand-alone executables for Windows, Linux, Mac 
OS X, FreeBSD, Solaris and AIX. The latter is specific to bundling a Python/Qt desktop 
GUI application. There are other similar libaries as well, such as 
[py2app](https://py2app.readthedocs.io/en/latest/) and [py2exe](http://www.py2exe.org/), 
so I'd encourage you to have a look at what is available.


> ## Project Description
>
> Your group project is to design and implement a cross-platform Python GUI desktop 
> application that allows the user to specify and visualise one or more of the fractal 
> or biological patterns described in the textbook "The Algorithmic Beauty of Plants". 
> The web application should feature UI controls to allow the user to choose patterns 
> and/or parameters, and should be as user-friendly as possible, incorporating 
> information on how to use the app and what each control is for, as well as background 
> information on what pattern is being visualised. The amount of features you 
> incorporate into your app is up to you and what you feel comfortable implementing in 
> the limited time you have (5 days). 
>
> If you have time, it is well worth investigating common design patterns for GUIs, such 
> as Model-View-Controller (MVC), Model-View-Presenter (MVP) or Model-View-ViewModel 
> (MVVM). Also consider how you would test your software, you might want to look at 
> GUI-specific testing libraries such as 
[pytest-qt](https://pytest-qt.readthedocs.io/en/latest/intro.html), and/or use Mocking 
to make mocks of your GUI objects, then write tests for the non-GUI parts of your code.
{: .challenge}

## Hand-in

Your should hand-in your URL for the GitHub repository for each group, and stand-alone 
executables for Linux, Mac OS X and Windows (or as many operating systems as your 
software supports). Please email these, along with the names of those in your group, to 
[martin.robinson@cs.ox.ac.uk](mailto:martin.robinson@cs.ox.ac.uk) by 5:30pm on Friday 
29th Oct.

{% include links.md %}

