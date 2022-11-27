# Title Escaping, special characters

REGEX TUTORIAL: Escaping, special characters

## Summary

As we’ve seen, a backslash \ is used to denote character classes, e.g. \d. So it’s a special character in regexps (just like in regular strings).

There are other special characters as well, that have special meaning in a regexp, such as [ ] { } ( ) \ ^ $ . | ? * +. They are used to do more powerful searches.

Don’t try to remember the list – soon we’ll deal with each of them, and you’ll know them by heart automatically.

## Table of Contents

- [Escaping](#escaping)
- [A slash](#aslash)
- [new RegExp](#new-regexp)
- [Flags](#flags)
- [Author](#author)

## Regex Components

### Escaping

To use a special character as a regular one, prepend it with a backslash: \..
That’s also called “escaping a character”.

Parentheses are also special characters, so if we want them, we should use \(. 

If we’re looking for a backslash \, it’s a special character in both regular strings and regexps, so we should double it.


### Aslash

A slash symbol '/' is not a special character, but in JavaScript it is used to open and close the regexp: /...pattern.../, so we should escape it too.

ex. alert( "/".match(/\//) ); // '/'

On the other hand, if we’re not using /.../, but create a regexp using new RegExp, then we don’t need to escape it

ex. alert( "/".match(new RegExp("/")) ); // finds /

### new RegExp

If we are creating a regular expression with new RegExp, then we don’t have to escape /, but need to do some other escaping.

ew.
let regexp = new RegExp("\d\.\d");

alert( "Chapter 5.1".match(regexp) ); // null

he similar search in one of previous examples worked with /\d\.\d/, but new RegExp("\d\.\d") doesn’t work, why?

The reason is that backslashes are “consumed” by a string. As we may recall, regular strings have their own special characters, such as \n, and a backslash is used for escaping.

Here’s how “\d.\d” is perceived =

ex.

 alert("\d\.\d"); // d.d

 String quotes “consume” backslashes and interpret them on their own, for instance:

\n – becomes a newline character,
\u1234 – becomes the Unicode character with such code,
…And when there’s no special meaning: like \d or \z, then the backslash is simply removed.
So new RegExp gets a string without backslashes. That’s why the search doesn’t work!

To fix it, we need to double backslashes, because string quotes turn \\ into \:

ex. 

 let regStr = "\\d\\.\\d";
alert(regStr); // \d\.\d (correct now)

let regexp = new RegExp(regStr);

alert( "Chapter 5.1".match(regexp) ); // 5.1



### Flags

Regular expressions may have flags that affect the search.

There are only 6 of them in JavaScript:

i
With this flag the search is case-insensitive: no difference between A and a (see the example below).
g
With this flag the search looks for all matches, without it – only the first match is returned.
m
Multiline mode (covered in the chapter Multiline mode of anchors ^ $, flag "m").
s
Enables “dotall” mode, that allows a dot . to match newline character \n (covered in the chapter Character classes).
u
Enables full Unicode support. The flag enables correct processing of surrogate pairs. More about that in the chapter Unicode: flag "u" and class \p{...}.
y
“Sticky” mode: searching at the exact position in the text (covered in the chapter Sticky flag "y", searching at position)



## Author

Born in Monterrey,NL and currently working to become a full-stacl developer

- [David´s Github](https://github.com/Vallejo1194)
- [David's Linkedin](https://www.linkedin.com/feed/)
- 📩[David's Email](mailto:adrian.vallejo94@gmail.com)
