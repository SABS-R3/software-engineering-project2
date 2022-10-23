---
title: "NERC/DTP week 3 group project"
teaching: 30
exercises: 0
questions:
- "For NERC/DPT students, What is the project you will be working on for week 3?"
objectives:
- "Explain the background of the project."
keypoints:
- "Your group project is to implement and deploy a Python desktop GUI application based 
  around a particular research project. A couple of suggested project are provided, or 
  you can make up your own"
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
(e.g. [Qt](https://www.qt.io/)). Python has a number of GUI libraries, so we will be 
using this approach.

During the week, you will work in groups to implement an easily installable desktop GUI
application using Python. Below are a few possible projects that you can implement 
within your application, or you could suggest something else.

## Project 1 - Tree Modelling with L-Systems

*suggested by Professor Gail Preston, Department of Plant Sciences* 

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

For this project, your application will allow users to generate and visualise branching 
tree structures using L-Systems.

## Project 2 - Calculations for Planetary Reference models

*suggested by Andrew Walker, Senior Research Fellow in Computational Geosciences, 
Department of Earth Science*

Planetary reference models typically describe the density, elasticity, and viscosity of 
the interior of a planet, which is assumed to be spherically symmetric. This means that 
these properties are described by one dimensional functions giving e.g. density as a 
function of depth (or radius). These models are used for a wide range of purposes, for 
example they allow the travel time of seismic waves from earthquakes to be calculated 
and used to find earthquake locations from distant measurements of ground motion.

The easiest calculations make use of the density and I suggest you start with that. Density can be used to compute the total mass below any particular depth, and this can be used to calculate the gravitational acceleration at that depth. This in turn can be used to calculate the pressure as a function of depth. Furthermore, the density distribution yields the planetary moment of inertia, which is a measure of how difficult it is to change the planets rotation rate. This can be measured and used to validate the planetary model.

Commonly two approaches are used to parameterise properties as a function of depth. For Earth, the poster child model is the preliminary Earth reference model (PREM) developed by Dziewonski and Anderson (1981) where piecewise polynomials are used to describe the properties. Models like PREM are thus smooth between the handful of breakpoints which are chosen to coincide with major discontinuities (such as the boundary between the ocean and crust, or mantle and core).  Coefficients of the PREM polynomials can be found in Table 1 of Dziewonski and Anderson (1981). Many more recent models abandon the smoothness of piecewise polynomials and describe planets as a large collection of layers with constant properties. These are tabulated and values for depths between those provided are found by linear interpolation. Examples of this kind of model for Mars were collated ahead of data collection by the InSight mission. These models are shown in Figure 1 of  Lognonné et al. (2019). The underlying data can be downloaded from https://doi.org/10.5281/zenodo.1478804. It may be useful to note that these 'tabulated' models can also be represented by piecewise polynomials with many breakpoints and no quadratic or higher order terms. 

Going beyond density-based calculations probably requires the use of additional tools. One potential extension is to use the TauP module in Obspy (https://docs.obspy.org/) to calculate travel times of seismic waves for a given reference model. Seismic wave velocities are parameterised in the same way as density (and can be calculated from the density and elasticity). 

#### References

Dziewonski, A. M., & Anderson, D. L. (1981). Preliminary reference Earth model. Physics of the Earth and Planetary Interiors, 25, 297–356.

Lognonné, P., Banerdt, W.B., Giardini, D. et al. SEIS: Insight’s Seismic Experiment for Internal Structure of Mars. Space Sci Rev 215, 12 (2019). https://doi.org/10.1007/s11214-018-0574-6

## Project 3 - Climate Predictor Package

*suggested by Matthew Wright, a NERC student in Atmospheric, Oceanic and Planetary 
Physics*

Write a package to predicts planet surface temperature as the result of changing cloud 
cover and land usage over a chosen period of time. A potential model to use is a two 
layer model of the atmosphere (see for example 
https://biocycle.atmos.colostate.edu/shiny/2layer/). The atmosphere is assumed 
transparent to incoming radiation (in the visible range), but with a certain proportion 
reflected (set by the albedo, α). The atmosphere absorbs and reradiates a proportion of 
the outgoing radiation (in the infrared range) set by the emissivity (ϵ) of the two 
atmospheric layers. The package solves for the temperature of the surface and the two 
layers in the atmosphere.


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
specific knowledge of Python tools.

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
> application based around a particular research project. You can use one the suggested 
> projects or choose your own. The web application should feature UI controls to allow 
> the user to choose different parameters, models etc., and should be as user-friendly a 
> possible, incorporating information on how to use the app and what each control is 
> for, as well as background information on what is being displayed/visualised. The 
> amount of 
>features you incorporate into your app is up to you and what you feel comfortable 
>implementing in the limited time you have (5 days). 
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

