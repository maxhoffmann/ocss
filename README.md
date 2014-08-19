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
    
    
  =another_modifier
  
    element child_element
    
    element=modifier
```

### Example

`widget.bem`

```
display: block

=small
  font-size: 50%
  
  text=big
    font-size: 100%
    
  text link
    font-weight: bold # comment
    

text
  color: blue
  font-size: 100%

  =big
    font-size: 200%
    
  link
    text-decoration: underline
```

### CSS Output:

```css
.widget {
  display: block;
}
  .widget--small {
    font-size: 50%;
  }
  .widget--small .widget__text--big {
    font-size: 100%;
  }
  .widget--small .widget__text__link {
    font-weight: bold;
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
