---
title: "Vue v.s. React (Extended Commentary)"
layout: doc
---

# Extended Commentary: Vue vs. React

## Original Post

**Brian's Post:** [link](https://brianzheng205.github.io/portfolio-brian/blogs/blog_1.html)

After reading Brian’s blog post, I was inspired to extend on Brian’s comparison of Vue and React. Brian focused on the syntactical/functionality differences between Vue and React, so to expand on his blog, I wanted to extend the comparison to a high level view. 

As someone new to React and Vue, I appreciate the comparison Brian made between Vue and React on the design front. As a preface to this information, I would've liked a quick description of what React and Vue are and a clear distinction that React is a Javascript library versus Vue which is a Javascript framework. In this blog, I will provide some context on frameworks vs libraries and outlined their differences. 

**Extended:**

React is a Javascript library that is widely used for building reactive websites. By reactive, it means that the website is responsive to user input and events. Vue is a Javascript framework to build interactive UIs. Libraries can be summed up as a collection of tools (i.e. functions) that developers can use to carry out a specific task. Frameworks are more broad and provide structure to your application in addition to functions like libraries.

In addition to their library vs framework difference, they have a different philosophy when it comes to rendering. Brian’s coding samples and explanations display this. As a high level overview, React takes on a more wide-sweeping approach to rendering as once a state updates, the whole component is re-rendered (see Brian’s ref() vs useState()). On the other hand, Vue’s rendering is more fine-grained as it only updates the parts that are affected by the state change.
