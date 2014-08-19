noCSS
===

A CSS preprocessor that restricts you to use best practices.

Background
----------



Example
------

__in `widget.nocss`:__

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
.widget.small
{
  font-size: 50%;
}
.widget.small .widget-text-link
{
  font-weight: bold;
}
```

Compiler
--------

__prevents:__
- IDs
  - they prevent reuse and have no advantage to classes
- tags
  - tags should only be used as a general baseline (can only be included in `tags.nocss`)
- element modifiers
  - if an element is worth to have a modifier it should be a component

__forbids:__
- `!important`
- multiple components with the same name
- nesting deeper than 3 levels (may be changed in `nocss.json`)

__adds:__
- `box-sizing: border-box` to all elements
