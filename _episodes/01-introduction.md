---
title: "Tree Generation App"
teaching: 30
exercises: 0
questions:
- "For NERC/DPT students, What is the project you will be working on for week 3?"
objectives:
- "Explain the background of the project."
- "Provide some getting started material on Javascript, Vue and the Nuxt framework."
- "Provide a template repository to get groups stated using the Nuxt framework"
keypoints:
- "Your group project is to implement and deploy a web application to specify and 
  visualise a number of fractal/biological patterns from the book \"The Algorithmic 
  Beauty of Plants\"." 
- "The suggested technology stack is Javascript, Vue and the Nuxt framework, although 
  you have the freedom to choose your own stack."
- "A template repository using Nuxt is provided 
  [here](https://github.com/SABS-R3/2020-software-engineering-project2-treegen) for your 
  convenience."
---

This project will get you to apply what you have learnt during this module (software 
engineering best practices, packaging, testing, continuous integration etc.), to a new 
technology domain, that of front-end web development. You will find that many of the 
concepts are the same, but of course all the details (e.g. language syntax, tools) are 
quite different.

During the week, you will work in groups to implement a single page web application 
using Javascript, Vue.js and the Nuxt framework, deploying it to a static web-page 
hosted on GitHub pages. The web application will allow users to generate and visualise 
branching tree structures using L-Systems.

The material below will give you some "getting started" information on each of these 
topics, and will provide you with some links to official documentation, or other further 
information, to allow you to implement the project.

There is also a "getting started" template project located 
[here](https://github.com/SABS-R3/2020-software-engineering-project2-treegen) which you 
can use, more description on this is provided below in the Nuxt section.

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

## Javascript, Node.js and npm

Javascript is a multi-paradigm language that support object orientated, functional and 
imperative programming styles. It is one of the core technologies of the world wide web, 
and most web browsers execute Javascript code alongside rendering HTML. Largely due to 
its dominance on the web, it is one of the most widely used programming languages, and 
there exist many 
[tutorials](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/JavaScript_basics) 
and [reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference) 
materials that you can use to become familiar with the language.  Similar to Python, it 
supports dynamic typing, and also similar to Python the user does not need to explicitly 
use a compiler to convert Javascript to an executable. Rather, Javascript is 
[just-in-time (JIT)](https://en.wikipedia.org/wiki/Just-in-time_compilation) compiled to 
bytecode during execution, and the bytecode is then run on a virtual machine.

A [Javascript](https://www.javascript.com/) runtime is a virtual machine that can 
interpret and execute a computer program written in Javascript. A number of these 
runtimes exist for various browsers, for example the Google V8 engine for Google Chrome. 
[Node.js](https://nodejs.org/en/docs/) is a runtime for executing Javascript on your 
computer, separate from any browser (although it is itself built on Chrome's V8 engine). 
The primary difference between Node.js and any browser-based runtime is that Node.js 
programs have access to the filesystem and the native environment of your computer, 
while Javascript programs running in a browser are sandboxed away from the rest of your 
computer, and instead have access to the [Document Object Model 
(DOM)](https://www.w3schools.com/js/js_htmldom.asp), a tree representation of the 
currently loaded web-page. 

To develop a web application using Javascript and Vue, you first need to install 
[Node.js](https://nodejs.org/en/) on your computer. In Ubuntu from version 16.04, one of 
the easiest ways to do this is to use the `snap` command to install one of the 
[NodeSource](https://github.com/nodesource/distributions/blob/master/README.md) 
distributions, which will allow you to install a specific Node.js version. At the time 
of writing the latest Long Term Support (LTE) version of Node.js is 12.19.0, and you can 
install this version via snap by typing on the command-line:

~~~
sudo snap install node --classic --channel=12
~~~
{: .language-bash}

Alternatively (e.g. if snap is not available), on an Ubuntu system you can type:

~~~
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
sudo apt-get install -y nodejs
~~~
{: .language-bash}

`npm` is a package manager for Node.js, similar to the `pip` package manager for 
Python. It will be installed as part of your Node.js install, and should be available on 
your command-line.

## Vue and the Nuxt framework

There exist a number of application frameworks for Javascript, which can be utilised to 
make the process of developing a web application much easier. A framework takes care of 
the overall design of the application itself, typically following a variant on the 
[model-view-controller](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller) 
paradigm, allowing you to focus on only implementing the functionality of the 
application itself. Using a framework also allows you to make use of the often large 
ecosystem of tools and libraries developed for that particular framework (for example 
the [Veutify](https://vuetifyjs.com/en/) UI component library for Vue).

[Vue.js](https://vuejs.org/) is a Javascript framework for building user interfaces. 
Similar to other Javascript UI frameworks like [React](https://reactjs.org/), a 
developer using the Vue frameworks writes a number of *components* using HTML templates 
and Javascript code, where a component is a separate logical item of your user 
interface. Your UI is constructed by using a hierarchy of such components working 
together. For example, a standard TODO list web application might be implemented by 
writing a TODO list component that renders the whole list, containing multiple child 
components rendering each item in that list. Each component has input properties, or 
*props*, that are like input arguments defining how that component looks or behaves, as 
well as an internal *state* that can be updated via user interaction, or interaction 
with other components. Using these props and internal state, the component itself is 
rendered using a HTML template defined by the developer. The Vue framework features 
excellent [documentation](https://v3.vuejs.org/guide/introduction.html#getting-started), 
as well as a [Command Line Interface (CLI)](https://cli.vuejs.org/) for creating and 
maintaining Vue projects, and a global state management library called 
[Vuex](https://vuex.vuejs.org/).

[Nuxt.js](https://nuxtjs.org/) is a Vue framework that builds upon Vue by providing 
developers with a set of plug-and-play modules that aim to make it easier to setup a 
fully featured Vue project that follows best practices for Vue.js and Node.js, and which 
includes useful developer features such as linting, testing and hot reloading (i.e. 
updating the app, while running, with newly edited files). You can easily create a new 
Nuxt application by using the `create-nuxt-app` tool, available via 
[npx](https://blog.npmjs.org/post/162869356040/introducing-npx-an-npm-package-runner#:~:text=npx%20is%20a%20tool%20intended,executables%20hosted%20on%20the%20registry.) 
(npx is available in your Node.js install) like so:

~~~
npx create-nuxt-app <project-name>
~~~
{: .language-bash}

The `create-nuxt-app` will then ask you a series of questions about the type of project 
you wish to create, then generate you a custom template project in which to start 
writing the app itself. The [template 
repo](https://github.com/SABS-R3/2020-software-engineering-project2-treegen) provided 
for this project was created using `create-nuxt-app`, using the following options:

- Project Name: `treegen`
- Programming Language: `Javascript`
- Package Manager: `Npm`
- UI framework: `Vuetify.js`. See [here](https://vuetifyjs.com/en/) for more details on 
  this framework.
- Nuxt.js modules: none
- Linting tools: `Prettier`
- Testing framework: `Jest`. See [here](https://jestjs.io/) for more details on Jest, 
  and [here](https://nuxtjs.org/examples/testing/) for an example of using it with Nuxt.
- Rendering mode: `Single Page App`
- Deployment target: `Static`
- Development tools: `jsconfig.json` (recommended for VSCode)

Once you have used `create-nuxt-app` to create your template application, you can run a 
local test server to see the running application via your browser. Navigate to the root 
directory of the application and use `npm` to install all the dependencies (defined by 
the `package.json` file created by `create-nuxt-app`).

~~~
npm install
~~~
{: .language-bash}


Then serve the application at [localhost:3000](localhost:3000) using:

~~~
npm run dev
~~~
{: .language-bash}


## Deploy to GitHub Pages

The Nuxt framework provides the option of deploying your web application to a static web 
server. Luckily, GitHub provides a free and convenient static web server via [GitHub 
Pages](https://pages.github.com/). Even more conveniently, Nuxt provides full details 
on their [website](https://nuxtjs.org/faq/github-pages/) of how to deploy a Nuxt 
application to Github Pages. They also show how this can be done automatically via your 
Travis or Appveyor Continuous Integration (CI), although the same can be achieved via 
GitHub actions as well.


> ## Project Description
>
> Your group project is to design and implement a web application that allows the user 
> to specify and visualise one or more of the fractal or biological patterns described 
> in the textbook "The Algorithmic Beauty of Plants". The web application should feature 
> UI controls to allow the user to choose patterns and/or parameters, and should be as 
> user-friendly as possible, incorporating information on how to use the app and what 
> each control is for, as well as background information on what pattern is being 
> visualised. The amount of features you incorporate into your web app is up to you and 
> what you feel comfortable implementing in the limited time you have (5 days). 
>
> Note that while the recommendation of this project is that you use the Nuxt framework, 
> this is not a requirement and you can use whatever technology stack you wish.
>
> Your application should be well tested by automatic tests that are run on every commit 
> by your CI, and be well commented and use a consistent coding style throughout. The 
> latest version of the application should be deployed either to GitHub pages or another 
> location, and ideally this should occur automatically on every commit to the GitHub 
> repository. It should be clear from your documentation how to setup a development 
> environment to further develop the application, how to run the tests, and how to 
> deploy the application itself.
{: .challenge}


## Hand-in

Your should hand-in your URL for the GitHub repository for each group, and the URL to 
where your web application is deployed. Please email these, along with the names of 
those in your group, to 
[martin.robinson@cs.ox.ac.uk](mailto:martin.robinson@cs.ox.ac.uk) by 5:30pm on Friday 
30th Oct.

{% include links.md %}

