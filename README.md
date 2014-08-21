CCSS (Component CSS)
===

A CSS preprocessor that restricts you to use best practices. Its goal is to make it easy to do the right thing and hard to do the wrong thing.

What if
--------

- nesting compiles to BEM?
- using IDs or `!important` would throw an error?
- components can’t be overwritten outside of theirs files?
- the compiler throws an error if you already have a component with the same name?
- nesting deeper than 3 levels would throw an error?
- tags have to inside of one single file?
- nesting components is not possible?
- adding modifiers to elements is not possible?
- there are files that define the relationship between two components?
- renaming a component is as simple as renaming a file?
- prefixing some components is as simple as putting them in a folder?

Example
------

__in `widget.ccss`:__

```
display: block

text
  color: blue
  font-size: 100%

  link
    text-decoration: underline
    
=small
  font-size: 50%
  
  text
    link
      font-weight: bold # comment
```

### CSS Output:

```css
.widget
{
  display: block;
}
.widget-text
{
  color: blue;
  font-size: 100%;
}
.widget-text-link
{
  text-decoration: underline;
}
.widget--small
{
  font-size: 50%;
}
.widget--small .widget-text-link
{
  font-weight: bold;
}
```

Compiler
--------

- uses an AST which is created by a seperate `ccss-parser`
- every rule is its own module
- all rules are turned on by default and can only to be disabled with a settings file (not recommended)

__prevents:__
- IDs
  - they prevent reuse and have no advantage to classes
- tags
  - tags should only be used as a general baseline (can only be included in `tags.nocss`)
- element modifiers
  - if an element is worth to have a modifier it should be a component
- nesting components
  - instead of changing properties of another component, you should add a modifier to it and apply those changes there
- dashes
  - dashes are used by the compiler to create scopes via prefixes, use underscores instead

__forbids:__
- `!important`
- multiple components with the same name
- nesting deeper than 3 levels (may be changed in `nocss.json`)

__adds:__
- `box-sizing: border-box` to all elements
