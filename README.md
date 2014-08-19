bem
===

a BEM driven CSS preprocessor

Syntax
------

```
block
  
  =modifier
    
  element
  
  another_element
  
    =modifier
  
    element
```

### Example

```css
widget
  display: block
  
  =hidden
    display: none
  
  text
    color: blue
    font-size: 100%
  
    =big
      font-size: 200%
      
    link
      text-decoration: underline
```

### CSS Output:

```
.widget {
  display: block;
}
.widget--hidden {
  display: none;
}
    
  .widget__text {
    color: blue;
    font-size: 100%;
  }
  .widget__text--big {
    font-size: 200%;
  }
      
    .widget__text__link {
      text-decoration: underline;
    }
```
