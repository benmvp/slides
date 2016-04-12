# JavaScript coding styles survey results!

### Frontend Friday | January 22, 2016

Ben Ilegbodu ([beni@](beni@eventbrite.com))  
German Frigerio ([gago@](gago@eventbrite.com))

=====

# Summary

NOTES:

- 29 submissions!
- Didn't spend to much looking at individual submissions
- But some people had specific opinions about everything
- Others who wanted no enforcement across the board
- Some "I don't care. I'll go along with whatever's most popular" for everything
- I kind of wish I had worded it "I don't care. I'll defer to Frontend Foundry" not "popular"
- I agree with a lot of the results, but some I'm kind of bummed with

=====

## 1. Had any issues with ESLint errors failing proposed?

<br />

- No, I fix ESLint errors before pushing to proposed
- Yes, but I've been able to fix the errors
- Yes, and fixing the errors has been a problem. I would like for errors to stop failing proposed.

NOTES:
- More of an informational question. Sanity check
- No one said they'd like for ESLint errors to stop failing proposed
- Most said they've run into errors but were able to fix
- Should be able to set up your editor to warn and you run locally
- Will make part of `arc lint` if it isn't

/////

## 2. What should ESLint do with `FIXME` and `TODO`?

- I don't care. I'll go along with whatever's most popular
- Continue to warn for FIXME & TODO (current setting)
- Warn for just FIXME
- Warn for just TODO
- Stop warning for both  <!-- .element class="fragment highlight-blue" -->

NOTES:
- This was pretty close between continuing to warn for both and stop warning
- **WINNER:** Stop warning for both

/////

## 3. How should we handle the `one-var` setting?

- I don't care. I'll go along with whatever's most popular
- Enforce single var declaration only (current setting)  <!-- .element class="fragment highlight-blue" -->
- Enforce multiple var declarations (no penalty)
- Enforce multiple var declarations (w/ penalty)
- No enforcement. Allow either (no penalty)
- No enforcement. Allow either (w/ penalty)

NOTES:
- **WINNER:** Enforce single var
- Surprised. Thought no enforcement would win.
- I've always done `one-var` but mostly for aesthetic purposes

=====

## 4. Spacing in `function` header

### Style A

```js
function(arg1, arg2){

}
```

### Style B  <!-- .element class="fragment highlight-blue" -->

```js
function(arg1, arg2) {

}
```

### Style C

```js
function (arg1, arg2) {

}
```

NOTES:
- **WINNER:** Style B
- This one wasn't really close. There were some votes for no enforcement
- As Simon says "We need to let the function breathe"
- Nick Williams wanted the option to have the curly braces on separate line
- We'll be adding an ESLint rule to enforce this which will require fixing all offending code

/////

## 5. Brace style ([`brace-style`](http://eslint.org/docs/rules/brace-style.html))

### Style A - One True Brace  <!-- .element class="fragment highlight-blue" -->

```js
if (...) {
} else {
}
```

### Style B - Stroustrup

```js
if (...) {
}
else {
}
```

### Style C - Allman

```js
if (...)
{
}
else
{
}
```

NOTES:
- **WINNER:** Style A - One True Brace
- Even less close than the previous one
- So bummed about this one!
- Going to avoid `else` statements!
- We'll add the ESLint rule & fix code

/////

## 6. Single statement `if` ([`curly`](http://eslint.org/docs/rules/curly.html))

### Style A   <!-- .element class="fragment highlight-blue" -->

```js
if (...) {
  foo();
}
```
<!-- .element: class="large" -->

### Style B

```js
if (...)
  foo();
```
<!-- .element: class="large" -->

NOTES:
- **WINNER:** Style A
- This was a landslide
- Not surprised. This was already an implicit rule
- Will add the ESLint rule. Hopefully not too much code change needed

/////

## 7. Dangling commas ([`comma-dangle`](http://eslint.org/docs/rules/comma-dangle.html))

```js
{
  defaults: {
    name: 'Ben',
    email: 'beni@',
  },
}
```
<!-- .element: class="large" -->

NOTES:
- This may be the closest one
- Technically "no enforcement" won
- But we'd like to enforce NO dangling commas
- It's currently implicitly enforced
- Would lead to better consistency
- Thoughts?

/////

## 8. Object literal spacing ([`key-spacing`](http://eslint.org/docs/rules/key-spacing.html))

### Style A - Single space after colon  <!-- .element class="fragment highlight-blue" -->

```js
{
  defaults: {
    name: 'Ben',
    email: 'beni@'
  }
}
```

### Style B - No space after colon

```js
{
  defaults:{
    name:'Ben',
    email:'beni@'
  }
}
```

NOTES:
- **WINNER:** Style A
- Blowout
- No one voted for Style B
- Will be adding the ESLint rule. Inline literals are probably the biggest offenders

/////

## 9. Object literal property quoting ([`quote-props`](http://eslint.org/docs/rules/quote-props.html))

### Style A

```js
{
  'name': 'Ben',
  'email_address': 'beni@'
}
```

### Style B

```js
{
  name: 'Ben',
  'email_address': 'beni@'
}
```

### Style C

```js
{
  name: 'Ben',
  email_address: 'beni@'
}
```

NOTES:
- **WINNER:** No enforcement!
- Most people said they didn't care, actually
- Our suggestion though is to quote keys coming from Python (single word or not)

/////

## 10. Private method naming convention

```js
{
  events: {
    'click @ui.showMoreLink': '_handleShowFooterLink'
  },

  _handleShowFooterLink: function() {

  }
}
```
<!-- .element: class="large" -->

NOTES:
- **WINNER:** Enforce underscore prefix
- Surprising!
- I hadn't seen this much in existing code
- It was something I was used to because we would minify underscore prefixed methods
- Have folks already been doing this?
- Only enforced with code reviews

/////

## 11. JavaScript shorthand coercion

```js
// truthy -> false, falsy -> true
if (!myObj) { }     

// truthy -> true, falsy -> false
var isBooleanTrue = !!myString;   

// value -> string
var valueString = myNumber + '';

// coerce a value to a number
var valNumeric = +myString;     
```
<!-- .element: class="large" -->

NOTES:
- Lots of people didn't care about this one
- Lots of people only wanted to allow negation boolean coercion
- **WINNER:** But most wanted to allow developers to use JavaScript shorthand
- Not forcing people to use it, but it's allowable and may be suggested

/////

## 12. Underscore programming style


### Style A - Functional  <!-- .element class="fragment highlight-blue" -->

```js
_.map(
  [1, 2, 3],
  function(n) { return n * 2; }
);
```

### Style B - Object-oriented  <!-- .element class="fragment highlight-blue" -->

```js
_([1, 2, 3]).map(
  function(n) { return n * 2; }
);
```

NOTES:
- **WINNER:** No enforcement!
- Equal amount of people wanted Style A & Style B
- Just ask that in a given file, keep style consistent

=====

# Questions?
