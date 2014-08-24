OCSS (Object CSS)
===

A CSS preprocessor that restricts you to use best practices. Its goal is to make it easy to do the right thing and hard to do the wrong thing.

OCSS is intended for large scale web products, but it can also help to keep clean CSS in smaller projects. It’s philosophy is to build pages/views out of multiple CSS objects that are independent of each other.

What if
--------

- classes are the default?
- nesting compiles to BEM?
- using IDs or `!important` would throw an error?
- components can’t be overwritten outside of theirs files?
- the compiler throws an error if you already have a component with the same name?
- nesting deeper than 3 levels would throw an error?
- tags have to live inside of one single file?
- nesting components is not possible?
- modifiers can only be added to components (not elements of a component)?
- there are files that define the relationship between two components?
- renaming a component is as simple as renaming a file?
- prefixing some components is as simple as putting them in a folder?
- your preprocessor could generate a documentation of all components?
- you could add html inside the styles that will generate the docs?
- every rule would be an optional?
- rules can easily added via plugins?

Example
------

__in `widget.ocss`:__

```
display: block

text
  color: blue
  font-size: 100%

  link
    text-decoration: underline
    
=small # component modifier
  font-size: 50%
  
  text
    link
      font-weight: bold
      
^big # parent modifier
  font-size: 200%
  
  text
    color: blue
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
._widget--big .widget {
  font-size: 200%;
}
._widget--big .widget-text {
  color: blue;
}
```

### Example with HTML

__Note: This won’t change the compiled CSS. It’s just for adding HTML examples to the docs.__

__in `widget.ccss`:__
```
(div)

  display: block
  
  (p)text
    color: blue
    font-size: 100%
  
    (a)link
      text-decoration: underline
      
  =small
    font-size: 50%
    
    text
      link
        font-weight: bold # this is a comment
        
  (div)@big
    font-size: 200%
    
    text
      color: blue
```

__Adds this markup:__

```html
<div class="_widget--big">

<div class="widget">
  <p class="widget-text">
    <a class="widget-text-link"></a>
  </p>
</div>

</div>
```

Compiler
--------

- uses an AST which is created by a seperate [ocss-parser](https://github.com/maxhoffmann/ocss-parser)
- every rule is its own module
- all rules are turned on by default and can only to be disabled with a settings file (not recommended)

__prevents:__
- IDs
  - they prevent reuse and have no advantage to classes
- tags
  - tags should only be used as a general baseline (can only be included in `tags.css`)
- element modifiers
  - if an element is worth to have a modifier it should be a component
- nesting components
  - instead of changing properties of another component, you should add a modifier to it and apply those changes there
- dashes
  - dashes are used by the compiler to create scopes via prefixes, use underscores instead
- components starting with an underscore
  - underscore prefix is used by the compiler to point out parent modifiers

__forbids:__
- `!important`
- multiple components with the same name
- nesting deeper than 3 levels (may be changed in `ocss.json`)

__adds:__
- `box-sizing: border-box` to all elements
