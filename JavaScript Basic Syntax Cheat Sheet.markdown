# JavaScript Syntax Cheatsheet

## ``// /* */`` Slashes and Stars for Comments
```javascript
// two slashes make the remainder of a line a comment
var a = 2; // they can start anywhere on a line

/* everything between slash-star and star-slash is also a comment */

/* these comments can span
multiple
lines */

var a /* and can even go most places in the middle of lines */ = 2;

/* comments inside lines are most useful for labeling function arguments */
Number.parseInt( "10", /* need radix for portability */ 10 );
```

## `var` Variables

```javascript
// always use `var`† to declare variables (likely to be bugs if you don't)
var a;

// you can also initialize the variables (give them their first value) at the same time
var a = 10;

// this can be done either at the top-level of a script or at the top-level of a function
```

† in ES6, you can also use `let` or `const` for various purposes, FYI

## `+ - * / ( ) % ++ --` for Math

Mostly follows standard algebra notation, with `/` for ÷ and `*` for ×. `-` is for subtraction and designating negatives. The `( )` are used for grouping expressions, just as in algebra. You always have to specify multiplication with the symbol, unlike in algebra where it is sometimes assumed.

```javascript
var a = 4 / (3 + 2); // 0.8
```

`--` and `++` are for incrementing and decrementing in place. **Use carefully!**

```javascript
var a = 1;
a++; // a now equals 2
```

While you can use `++` and `--` within expressions, it gets confusing fast—so probably best to leave them on lines by themselves.

## `=` for Assignment

Note that a single `=` is **never** used for comparison!

```javascript
var b;
b = 3 + 700 / a;
```

## `+= -=` are Shortcut Assignments

```javascript
b += 2; // the same as b = b + 2;
```

There are others, but these are the most commonly used.

## `'' ""` for Text

You can use single or double quotes for text; we will use single quotes unless the text itself contains a single quote.

```javascript
var text = 'some text';
```

## `=== !== > < >= <=` for Comparison

The 'triple equals' form will check *both* the value and type of each side of the comparison. The double equals form will try convert the types to something that matches—which sometimes has unexpected results. Generally, we recommend being very careful before using just `==` or `!=` for comparison.

```javascript
var a = 3;
var b = 4;
var c = '4'; // a text
a === 3; // true
a === a; // true
a === b; // false
a === c; // false
a !== b; // true
```

## `+` for Concatenation

```javascript
'this is ' + 'some text'; // yield 'this is some text' as a single string
```

## `[ ] ,` for Arrays

`[ ]` are used for both *creating* arrays. `,` are used to separate values.

```javascript
var a = ['a', 'b', 'c', 'd', 0, 'f'];
```

`[ ]` are also used to access elements of the array. Integers starting at 0 are the indexes.

```javascript
var b = a[3]; // now b will have 'd' stored in it
```

`[ ]` and `=` are used to change values in the array.

```javascript
a[3] = 'D'; // we changed the array to ['a', 'b', 'c', 'D', 0, 'f']
```

You can also put arrays within arrays as deeply nested as you'd like.

```javascript
var a = [[[[[[[[[[[[[[['deep']]]]]]]]]]]]]]];
a[0][0][0][0][0][0][0][0][0][0][0][0][0][0][0]; // 'deep' — did I get that right?
```

Finally, you can use variables inside the `[ ]` to access elements of an array.

```javascript
var a = ['a', 'b', 'c'];
var index = 2;
var b = a[index]; // 'c'
```

You may also want to look up 'destructuring' for arrays.

## `{ } [ ] : , .` for Objects

Arrays are collections of values accessed by an integer. Objects are collections of values accessed by a 'key' that is typically a string, and you end up with key-value pairs.

They are created with `{ } : ,`:

```javascript
// we generally recommend writing this on separate lines for clarity
var a = {
  one: 'i',
  two: 'ii',
  three: 'iii',
  four: 'iv'
};
```

The `{ }` are used to tell the computer where the object starts and ends, like the `[ ]` when making an array. The `:` separates keys and values: keys on the left, values on the right. `,` separates key-value pairs.

You can use quotes around the keys, but we don't unless it is a JSON file or the key is a reserved word or has a character that the intepreter won't accept (like a dash):

```javascript
// only use quotes if you need them
var a = {
  'var': 0,
  'return': 1,
  'scooby-doo': 2
};
```

To access elements of the array, you use `.`:

```javascript
var a = {
  one: 'i',
  two: 'ii',
  three: 'iii',
  four: 'iv'
};
a.one; // 'i'
a.four; // 'iv'
```

If you have a variable that you want to use as the key, or the key requires quotes, you can use `[ ]` like arrays:

```javascript
var a = {
  one: 'i',
  two: 'ii',
  three: 'iii',
  four: 'iv',
  'fifty-five': 'lv'
};
var key = 'one';
a[key]; // 'i'
a['fifty-five']; // 'lv'
```

Use can use either of these accessor methods—`.` or `[ ]`—for assignment purposes, just as in arrays. Also, just as in arrays, you can nest things as deeply as necessary.

You'll often see objects and arrays nested inside each other.

## `( ) { }` for If Blocks

While JavaScript has a lot of the usual control-flow statements, we use the `if` most often. It uses `( )` to enclose the condition and `{ }` to enclose the 'body' of statements you want to execute.

```javascript
var a = 3;
var b;
if (a > 2) {
  b = 14;
} else {
  b = 0;
}
```

While the curly braces are not required in some instances for an `if` block, please always use them.

## `( ) { } ,` Functions

Functions are one way of modularizing and reusing code. They are defined with the `function` keyword followed by `( )` (optionally containing parameters) and a 'function body' that has statements in it. A `return` statement will cause the function to 'return' that value to wherever called the function.

To call a function, `( )` are **required**.

```javascript
var helloWorld = function() {
  console.log('Hello, world!');
  return true;
};
helloWorld(); // both prints the 'Hello, world!' message and has the value `true`
```

You can use arguments to modularize the code, with multiple arguments separated by commas. You don't need to use the arguments

```javascript
var helloWorld = function(name, age) {
  console.log('Hello, ' + name + '!');
  return true;
};
helloWorld('Dr. Who', 1000); // both prints the 'Hello, Dr. Who!' message and has the value `true`
```

A function is data just like any other value, and as such can be assigned to a variable (like we've been doing) or even assigned inside an object.

```javascript
var conversation = {
  greet: function() {
    return 'Hello!';
  },
  goodbye: function() {
    return 'Bye!';
  }
}
conversation.greet(); // 'Hello!'
conversation.goodbye(); // 'Bye!'
```

May also want to look up "fat arrow" functions and default paramters as part of ES6.

# `< > / = { }` for JSX

React lets us use a subset of HTML within our JavaScript files. While I'd recommend a full [HTML cheatsheet](http://media.mediatemple.netdna-cdn.com/wp-content/uploads/images/html5-cheat-sheet/html5-cheat-sheet.pdf) for reference, a quick of the basic structure of HTML tags follows. JSX is not actually HTML, but it is close enough that you don't normally need to think about it.

A 'tag' is delimited by `< >` and usually comes in pairs. The 'opening' tag does not have a `/` in it, but the 'closing' tag does.

```html
<div></div>
```

The pair may have contents, which can include other HTML tags. Just make sure your opening and closing tags match up!

```html
<div>Some text.</div>
<div>
  Some <div>text</div>
</div>
```

If the pair doesn't have any contents, it can put the `/` inside the opening tag to 'self-close'. (JSX has slightly different rules than HTML about this.)

```html
<div />
```

Tags may also have attributes. The supported ones are specific to the tag (or React component), but they are key-value pairs separated by spaces. Mostly, we use attributes specific to the React component, and we don't use the `id` or `className` attributes much. (Note that React requires the `className` attribute instead of the HTML standard `class`.)

```html
<div id='test' className='super' />
```

JSX allows use to grab value from our JavaScript program to put in our HTML, as either attribute values or as contents. Use `{ }` for this.

```javascript
var js_id = 'my_id';
var contents = 'Four score and seven years ago…';
<div id={js_id} styles={{display: 'block'}}>
  {contents}
</div>
```

The double-curlies `{{display: 'block'}}` is actually putting a JavaScript object right into the JSX!

## Other Topics (probably other cheat-sheets or other JavaScript references available online)

Regular expressions, prototypical inheritance, expressions, `null` and `undefined` and `NaN`, variable scope, built-in functions, browser/DOM functions, `this`,
