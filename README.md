noCSS
===

a CSS preprocessor that restricts you to use best practices

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
- tags
- element modifiers

__forbids:__
- `!important`
- multiple components with the same name
- nesting deeper than 3 levels (may be changed in `rules.nocss`)

__adds:__
- `box-sizing: border-box` to all elements
