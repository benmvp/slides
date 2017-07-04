# React Native + ES.next = ♥

<br />

## Ben Ilegbodu

<br />

[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [#ChainReact2017](https://twitter.com/hashtag/ChainReact2017)    

<br />

July 10, 2017  

NOTES:
- My name is Ben Ilegbodu
- Here to talk about React Native + ES.next

/////

<!-- .slide: data-background="url(../../img/giphy/stand-up.gif) no-repeat center" data-background-size="cover" -->

# Stand Up!
<!-- .element: style="-webkit-text-stroke: black 4px; color: white" -->

NOTES:
- But first, would like everyone to stand up!
- Let's do 10 squats
- Now turn to your neighbors, introduce yourself & say hi
- You don't realize it, but I just tricked you
- Now you can't say that you didn't get anything out of my talk
- You at least got two things:
- Exercise & and met some people you didn't know
- But hopefully you'll get more out of the talk!

=====

ben-ilegbodu.json

<div style="display:flex;align-items:center">
	<div style="flex:0 0 50%;">
		<pre class="large"><code class="lang-json">
{
  "name": "Ben Ilegbodu",
  "priorities": [
    "Jesus", "family", "work"
  ],
  "location": "Pittsburg, CA",
  "work": "Eventbrite",
  "role": "Engineering Manager",
  "hobbies": [
    "basketball", "DIY", "movies"
  ]
}
			</code></pre>
	</div>
	<div style="flex:0 0 50%;">
		<img src="../../img/family-tahoe-beach-mountain.jpg" style="width:100%;height:auto" alt="Ilegbodu family on the beach at Lake Tahoe" />
	</div>
</div>

NOTES:
_[1 minute]_

/////

![Eventbrite logo](../../img/eventbrite/wordmark-orange.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none;" -->

NOTES:
- Currently an Engineering Manager at Eventbrite
- Eventbrite is an online ticketing & events platform
- Probably used Eventbrite before, but because an organizer told you to buy your tickets on Eventbrite
- This conference is using Eventbrite, so thank you very much :)
- But I'm leading the team tasked with making Eventbrite a Destination

/////

## Backstory

<br />

- [Jul 2015] [_Learning ES6 series_](http://www.benmvp.com/learning-es6-series)
- [Jan 2016] [React official tutorial (old)](https://github.com/facebook/react/blob/8cac523beaaacfeae179ca14a1d8a46d82892016/docs/docs/tutorial.md)
- [Nov 2016] [React Native Express](http://www.reactnativeexpress.com/) training course by [Devin Abbott](https://twitter.com/devinaabbott)

NOTES:
- Two years ago (Jul 2015) I began learning ES6 by writing a blog series called _Learning ES6_
- 6 months later (Jan 2016) I began learning React starting w/ the official tutorial
- It was the comments app still written in ES5 back then, but rewrote in ES6 to apply knowledge
- End of last year (Nov 2016) took a React Native workshop from Devin Abbott
- Blew my mind how React Native was just like React, just in a different environment
- Outside of JSX, React is just JavaScript, so naturally ES.next (future JavaScript) will apply well
- Given ES.next & React go well together, and React & React Native are very similar
- I’m going to spend time talking about how ES.Next & React Native go so well together


=====

## Agenda

0. Destructuring
0. Arrow functions
0. Rest operator
0. Spread operator
0. Classes

NOTES:
- Here's the agenda
- Focusing on the features you're most likely to use while building UI in React Native
- As opposed to features for APIs/Redux/etc
- Wish I could talk about everything but that's 40+ features
- Reason picking these 5 features is because they'll help write clear & concise code
- They target a wide range of audiences
- We'll see other features along the way that I will explain quickly

/////

![Chain React Conference App Ad](../../img/react-esnext/chain-react-app-ad.jpg)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; width: 75%" -->

[github/infinitered/ChainReactApp](https://github.com/infinitered/ChainReactApp)

NOTES:
- All of the examples I'll show come from the Chain React Conference app
- Some of the examples are code "improvements"; what I thought should've been done
- I considered submitting a "code improvements" PR
- But didn't wanna be _that_ guy nor get uninvited to speak 😉

/////

![Disclaimer](../../img/disclaimer.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none;" -->

NOTES:
- I gave my first ES6 talk in October 2015 right after the ES2015 spec was released, and 2 years later speaking on it
- Some people know everything & others know absolutely nothing
- For some of you, a lot of what I'll talk about will be new, and that's ok
- Others will know the core concepts, but I hope to remind of details
- There'll be some of you who have been doing it longer than me that will know most of this stuff
- Hoping there's at least one thing that maybe you forgot or hadn't used it in a way
- But even if you do know **EVERYTHING** you can teach others!


=====

## Recap

0. Destructuring
0. Arrow functions
0. Rest operator
0. Spread operator
0. Classes

NOTES:

/////

## Additional resources

- [React Native Official Tutorial](https://facebook.github.io/react-native/docs/tutorial.html)
- [_Learning ES6_ series](/learning-es6-series/)
- [Chain React Conference App](https://github.com/infinitered/ChainReactApp)
- [Eventbrite ES6+ coding style guide](https://github.com/eventbrite/javascript/tree/master/es6)
- [Eventbrite React coding style guide](https://github.com/eventbrite/javascript/tree/master/react)
- [Eventbrite React ESLint configuration](https://github.com/eventbrite/javascript/tree/master/packages/eslint-config-eventbrite-react)

=====

![Julian Edelman Thumbs Up](../../img/giphy/julian-edelman-thumbs-up.gif)
<!-- .element: style="width: 60%" -->

NOTES:
- So some quick shoutouts before I wrap

/////

![Chain React Conference logo](../../img/conf-logos/chain-react-logo.svg)
<!-- .element: style="width: 50%; border: 0; background: none; margin: 0; box-shadow: none;" -->

NOTES:
- Truly an honor & privilege to be here
- A year ago I didn't even know React Native
- And now I'm here sharing with you at the first React Native conf in the US
- Simply amazing
- Thanks to Tom, Ben, Beth & the rest of the team for the opportunity

/////

![Eventbrite logo](../../img/eventbrite/wordmark-orange.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none;" -->

NOTES:
- I'm here in part because Eventbrite allowed my Frontend Platform team to make the transition from Backbone to React
- So thanks to the leadership for that trust
- Also thanks for continued support in speaking at conference to share what I know and what we've been doing

/////

# YOU!
<!-- .element: style="font-size:12em" -->

NOTES:
- It's my hope that, the main reason I do this, is so you learn something new to make you a better developer
- Any feedback would be appreciated!

=====

![Take a bow](../../img/giphy/animated-take-a-bow.gif)
<!-- .element: style="width: 70%" -->

NOTES:

/////

# Questions?

<br />

## Ben Ilegbodu

[benmvp.com](/) | [@benmvp](https://twitter.com/benmvp) | [ben@benmvp.com](mailto:ben@benmvp.com)  
[github/benmvp](https://github.com/benmvp)

<br />

Ask me anything! [benmvp.com/ama](http://www.benmvp.com/ama/)

NOTES:
- Slides are available on Twitter and Blog
- Ask questions on Twitter, via email or AMA!
