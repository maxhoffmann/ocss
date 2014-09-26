OCSS (Object CSS)
=================

A CSS preprocessor that restricts you to use best practices. Its goal is to make it easy to do the right thing and hard to do the wrong thing.

OCSS is intended for large scale web products, but it can also help to keep clean CSS in smaller projects. Its philosophy is to build pages/views out of multiple CSS objects that are independent of each other.

What if
-------

- classes are the default?
- nesting compiles to BEM?
- using IDs or `!important` would throw an error?
- objects can’t be overwritten outside of theirs files?
- the compiler throws an error if you already have an object with the same name?
- nesting deeper than 3 levels would throw an error?
- tags have to live inside of one single file?
- nesting objects is not possible?
- modifiers can only be added to objects (not elements of an object)?
- there are files that define the relationship between two objects?
- renaming an object is as simple as renaming a file?
- prefixing some objects is as simple as putting them in a folder?
- your preprocessor could generate a documentation of all objects?
- rules can easily added via plugins?

Example
-------

__in `widget.ocss`:__

```
display: block

text
  color: blue
  font-size: 100%

  link
    text-decoration: underline
    
=small // modifier
  font-size: 50%
  
  text
    link
      font-weight: bold
```

### CSS Output:

```css
.widget {
  display: block;
}
.widget-text {
  color: blue;
  font-size: 100%;
}
.widget-text-link {
  text-decoration: underline;
}
.widget--small {
  font-size: 50%;
}
.widget--small .widget-text-link {
  font-weight: bold;
}
```

Compiler
--------

uses an AST which is created by a seperate [ocss-parser](https://github.com/maxhoffmann/ocss-parser)

__prevents:__
- IDs
  - they prevent reuse and have no advantage to classes
- tags
  - tags should only be used as a general baseline (can only be included in `tags.css`)
- element modifiers
  - if an element is worth to have a modifier it should be an object
- nesting objects
  - instead of changing properties of another object, you should add a modifier to it and apply those changes there
- dashes
  - dashes are used by the compiler to create scopes via prefixes, use underscores instead
- `!important`
  - the evil of specificity
- multiple objects with the same name
  - the file for the object should be the single source of truth
