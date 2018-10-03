# "Minimally-painful" React-Redux Testing Workshop

<br />

## Ben Ilegbodu

<br />

[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [#ReactAlicante](https://twitter.com/hashtag/reactalicante)

<br />

13 September 2018

<br />

## http://bit.ly/react-test-begin

NOTES:
- Who's done React before??

/////

# Introductions!

<br />

## Name
## Where You're From
## 1st Programming Language

=====
<!-- .slide: data-background="url(../../img/family/family-selfie-madrid.jpg) no-repeat center" data-background-size="cover" -->

NOTES:
- Christian, Husband, Father

/////

![Eventbrite logo](../../img/eventbrite/wordmark-orange.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none;" -->

NOTES:
- Currently a Principal UI Engineer at Eventbrite
- Eventbrite is an online ticketing & events platform
- I work on the Frontend Platform team and right now we've completed a transition from Backbone/Marionette to React

=====

# SETUP

<br />

# http://bit.ly/react-test-begin

NOTES:
- Last chance to get setup before begin

/////

## FUNdamental Concepts

- Rendered content
- Event handlers
- UI state
- Redux actions
- Redux reducers*

NOTES:
- With these steps, we'll learn these FUNdamentals React/Redux testing concepts
- These allow you to unit test React applications
- Learning other little things as we go

/////

<div style="display:flex;align-items:flex-end;justify-content:space-around;margin-top:5%">
	<div style="flex:0 0 45%;">
        <a href="https://reactjs.org/"><img
            src="../../img/react/react-logo.png"
            class="plain"
            style="background:none"
        /></a>
		<a href="https://reactjs.org/">React</a>
  </div>
	<div style="flex:0 0 45%;">
        <a href="http://redux.js.org/"><img
            src="../../img/nav-react/redux-logo.png"
            class="plain"
            style="background:none"
        /></a>
		<a href="http://redux.js.org/">Redux</a>
  </div>
</div>

NOTES:
- FYI - I'm making an assumption that you already know React & Redux
  * Won't be able to spend time teaching concepts
- However, certain implementations can make things easier to test
  * So we'll probably discuss the actual source code
- But if there's anything you see that you have questions about
  * Or just general questions you have about React/Redux
  * Please ask!

/////

# Watch along

### --or--

# Code along

NOTES:
- There are many different ways that people learn
- I actually learn best with written tutorials because I can go at my own pace and follow links
- Live workshops like these help me because I can ask questions and hear explanations
- I'm going to live code testing a React/Redux application
- I will go slowly enough that you can code along with me; some people like to do that
- But in order to cover what we need to cover, I'm going to move w/ pace so it _may_ be hard to type & grasp
- Won't be able to stop and debug
- Alternatively you can just watch and follow along
- The nice thing is that you can switch back and forth because you have the opportunity to start from any given step

=====

# DEMO

![Workshop screenshot](../../img/react/workshop-screenshot.png)
<!-- .element: style="width:65%" -->

NOTES:
- Gonna to learn to test with a "real" application
- Quick walkthrough of how it works

/////

# WHAT to test

### --and--

# HOW to test

NOTES:
- The biggest question is always **what** to test
  * Test any logic
  * Anywhere in components or Redux
  * Boils down to any `if` statement or computation
- The next question is **how** to test
  * How can be tricky
  * Greatly impacted by the implementation
  * Components: Public API - what's rendered & callback functions
  * Redux actions gets fun when they are async

/////

## Agenda

1. [Render (markup)](https://github.com/benmvp/react-workshop/blob/master/src/testing/01-render-markup/)
1. [Render (components)](https://github.com/benmvp/react-workshop/blob/master/src/testing/02-render-components/)
1. [Callbacks (markup)](https://github.com/benmvp/react-workshop/blob/master/src/testing/03-callbacks-markup/)
1. [Callbacks (components)](https://github.com/benmvp/react-workshop/blob/master/src/testing/04-callbacks-components/)
1. [UI State](https://github.com/benmvp/react-workshop/blob/master/src/testing/05-ui-state/)
1. [Redux Actions](https://github.com/benmvp/react-workshop/blob/master/src/testing/06-actions/)
1. [Redux Reducers](https://github.com/benmvp/react-workshop/blob/master/src/testing/07-reducers/)*

NOTES:
- Here's our agenda
- Hoping to get through the first 4, break and finish final 3
- But we may not make it to the last step on reducers
  * But _that's_ ok because testing reducers is like normal JS testing
- We'll start off real slow and the progressively pick up the pace

/////

# Questions

NOTES:
- What questions so far?


=====

![Minions Let's Get Started](../../img/giphy/lets-get-started.gif)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; width: 75%" -->

=====

=====

## More functionality

- [Redux Reducers](https://github.com/benmvp/react-workshop/blob/master/src/testing/07-reducers/)
- [Functional testing](https://github.com/benmvp/react-workshop/blob/master/src/testing/08-functional/)
- [End-to-end testing](https://github.com/benmvp/react-workshop/blob/master/src/testing/09-e2e/)

NOTES:
- Didn't get to Redux reducers as I suspected
- Function/integration testing to test everything together
- End-to-end testing for browser integration

/////

# Final Questions

NOTES:
- What questions can I answer about anything?
- Things you were hoping I'd cover?

=====

<a href="https://github.com/benmvp/react-workshop/stargazers" target="_blank">
  <img src="../../img/react/workshop-stars.png" class="plain" style="width: 75%" alt="Ben Ilegbodu's React Workshop Stars" />
</a>

<div class="code-highlight" style="height: 250px; top: 33px; left: 820px; width: 460px"></div>

NOTES:
- Do me a solid and and star the repo


/////

<!-- .slide: data-background="url(../../img/webdev/matt-jones-42954-unsplash.jpg) no-repeat center" data-background-size="cover"  -->

<div style="display: flex; align-items:center; justify-content: flex-start">
	<div style="width: 40%" class="content-overlay">
  
  <h1>Ben Ilegbodu</h1>

  <p><a href="https://twitter.com/benmvp" target="_blank">@benmvp</a> | <a href="/" target="_blank">benmvp.com</a></p>
  <p><a href="mailto:ben@benmvp.com">ben@benmvp.com</a></p>
  <p><a href="https://github.com/benmvp" target="_blank">github/benmvp</a></p>

  <br />

  <p>Ask me anything!<br /><a href="http://www.benmvp.com/ama/" target="_blank">benmvp.com/ama</a></p>
  
  </div>
</div>

NOTES:
- So that's it!
- Ask questions on Twitter, via email or AMA!
- Thanks!
