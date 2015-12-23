# Revisiting JavaScript coding styles

### Frontend Friday | December 4, 2015

Ben ([beni@](beni@eventbrite.com)) & Gago ([gago@](gago@eventbrite.com))

=====

# Background

### jshint / eslint

=====

# [Current eslint rules](https://github.com/eventbrite/core/blob/master/.eslintrc)

### Do we want to continue to have ESLint warnings fail the build?

/////

## ESLint rules (Possible Errors)

- NONE!

/////

## ESLint rules (Best Practices)

- [block-scoped-var](http://eslint.org/docs/rules/block-scoped-var)
- [complexity](http://eslint.org/docs/rules/complexity)
- [default-case](http://eslint.org/docs/rules/default-case)
- [dot-notation](http://eslint.org/docs/rules/dot-notation) (allowed)
- [guard-for-in](http://eslint.org/docs/rules/guard-for-in)
- [no-eq-null](http://eslint.org/docs/rules/no-eq-null)
- [no-div-regex](http://eslint.org/docs/rules/no-div-regex)
- [no-floating-decimal](http://eslint.org/docs/rules/no-floating-decimal)
- [no-param-reassign](http://eslint.org/docs/rules/no-param-reassign) (allowed)
- [no-self-compare](http://eslint.org/docs/rules/no-self-compare)
- [no-throw-literal](http://eslint.org/docs/rules/no-throw-literal)
- [no-void](http://eslint.org/docs/rules/no-void)
- [no-warning-comments](http://eslint.org/docs/rules/no-warning-comments) (['FIXME', 'TODO'])
- [radix](http://eslint.org/docs/rules/radix)
- [vars-on-top](http://eslint.org/docs/rules/vars-on-top)
- [wrap-iife](http://eslint.org/docs/rules/wrap-iife) ('inside')

/////

## ESLint rules (Variables)

- [no-unused-vars](http://eslint.org/docs/rules/no-unused-vars)

/////

## ESLint rules (Stylistic issues)

- [comma-style](http://eslint.org/docs/rules/comma-style) ('last')
- [consistent-this](http://eslint.org/docs/rules/consistent-this) ('self')
- [func-style](http://eslint.org/docs/rules/func-style) ('declaration')
- [quotes](http://eslint.org/docs/rules/quotes) ('single')
- [new-cap](http://eslint.org/docs/rules/new-cap) ('Backbone')
- [newline-after-var](http://eslint.org/docs/rules/newline-after-var)
- [no-inline-comments](http://eslint.org/docs/rules/no-inline-comments)
- [no-multiple-empty-lines](http://eslint.org/docs/rules/no-multiple-empty-lines) (max=2)
- [no-nested-ternary](http://eslint.org/docs/rules/no-nested-ternary)
- [no-underscore-dangle](http://eslint.org/docs/rules/no-underscore-dangle) (allowed)
- [one-var](http://eslint.org/docs/rules/one-var) (var='always')
- [space-after-keywords](http://eslint.org/docs/rules/space-after-keywords) ('always')
- [semi](http://eslint.org/docs/rules/semi) ('always')

/////

## ESLint rules (ES6)

=====

# Purpose of code reviews

- Finding bugs
- Code health
- Shared understanding

/////

# Intended JS code audience

- Junior JS devs? Unfamiliar backend devs?
- How do we determine what's readable?

=====

# Game time:
# +1 &nbsp; / &nbsp; &mdash;1 &nbsp; / &nbsp; 0

/////

## Spacing in `function` header

```js
function(arg1, arg2){

}
```
<!-- .element: class="large" -->

### vs

```js
function(arg1, arg2) {

}
```
<!-- .element: class="large" -->

### vs

```js
function (arg1, arg2) {

}
```
<!-- .element: class="large" -->

/////

## Line breaks for `else` / `else if`

```js
if (...) {

} else {

}
```
<!-- .element: class="large" -->

### vs

```js
if (...) {

}
else {

}
```
<!-- .element: class="large" -->

/////

## Single statement `if`

```js
if (...) {
  foo();
}
```
<!-- .element: class="large" -->

### vs

```js
if (...)
  foo();
```
<!-- .element: class="large" -->

/////

## Dangling commas

```js
{
  defaults: {
    name: 'Ben',
    email: 'beni@',
  },
}
```
<!-- .element: class="large" -->

/////

## Object literal spacing

```js
{
  defaults: {
    name: 'Ben',
    email: 'beni@'
  },
}
```
<!-- .element: class="large" -->

## vs

```js
{
  defaults:{
    name:'Ben',
    email:'beni@'
  }
}
```
<!-- .element: class="large" -->

/////

## Object literal property quoting

```js
{
  'name': 'Ben',
  'email_address': 'beni@'
}
```

## vs

```js
{
  name: 'Ben',
  'email_address': 'beni@'
}
```

## vs

```js
{
  name: 'Ben',
  email_address: 'beni@'
}
```

/////

## Property index quoting

```js
obj['name'] = 'Ben';
obj['email_address'] = 'beni@';
```
<!-- .element: class="large" -->

## vs

```js
obj.name = 'Ben';
obj['email_address'] = 'beni@';
```
<!-- .element: class="large" -->

## vs

```js
obj.name = 'Ben';
obj.email_address = 'beni@';
```
<!-- .element: class="large" -->

/////

## Semicolon usage

```js
name = 'Ben';
emailAddress = 'beni@';
```
<!-- .element: class="large" -->

## vs

```js
name = 'Ben'
emailAddress = 'beni@'
```
<!-- .element: class="large" -->

ESLint: [`semi`](http://eslint.org/docs/rules/semi)

/////

## Underscore prefix for private methods

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

/////

## Fully leveraging JavaScript (aka "tricks")

```js
!value;     // truthy -> false, falsy -> true

!!value;    // truthy -> true, falsy -> false

value + ''; // coerce a value to a string

+value;     // coerce a value to a number
```
<!-- .element: class="large" -->

/////

## Fully leveraging JavaScript (aka "tricks"), cont...

```js
var methodName;
if (...) {
  methodName = 'foo';
}
else {
  methodName = 'baz';
}
this[methodName]();
```

## vs

```js
if (...) {
  this.foo();
}
else {
  this.baz();
}
```

/////

## Nested helper functions

<div style="display:flex">
	<div style="flex:0 0 45%;">
		<pre class="small"><code class="lang-js" data-trim>
{
  templateHelpers: function () {
    var color = '#ff0000',
        name = 'Ben';

    function getRect(width, height) {
      var area = width \* height;
      return area +
        '\nName:' + name +
        '\nColor:' + color;
    }

    return {
      big: getRect(100,50),
      small: getRect(2.5, 5)
    };
  }
}
			</code></pre>
	</div>
	<div style="flex:0 0 55%;">
		<pre class="small"><code class="lang-js" data-trim>
{
  getRect: function(width, height, name, color) {
    var area = width \* height;
    return area +
      '\nName:' + name +
      '\nColor:' + color;
  },

  templateHelpers: function () {
    var color = '#ff0000',
        name = 'Ben';

    return {
      big: this.getRect(100,50, name, color),
      small: this.getRect(2.5, 5, name, color)
    };
  }
}
			</code></pre>
	</div>
</div>

/////

## Factoring out one-time use blocks of code

/////

## Programming styles

```js
_.map(
  [1, 2, 3],
  function(n) { return n * 2; }
);
```
<!-- .element: class="large" -->

## vs

```js
_([1, 2, 3]).map(
  function(n) { return n * 2; }
);
```
<!-- .element: class="large" -->

=====

# Is ESLint our **SOLe** enforcement of coding styles?
