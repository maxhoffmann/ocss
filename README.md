bem
===

a BEM driven CSS preprocessor

Syntax
------

__in `widget.bem`:__

```
display: block

text
  color: blue
  font-size: 100%

  link
    text-decoration: underline
    
  =big
    font-size: 200%
    
=small
  font-size: 50%
  
  text
    
    link
      font-weight: bold # comment
      
    =big
      font-size: 100%
```

### CSS Output:

```css
.widget
{
  display: block;
}
.widget__text
{
  color: blue;
  font-size: 100%;
}
.widget__text--big
{
  font-size: 200%;
}
.widget__text__link
{
  text-decoration: underline;
}
.widget--small
{
  font-size: 50%;
}
.widget--small .widget__text__link
{
  font-weight: bold;
}
.widget--small .widget__text--big
{
  font-size: 100%;
}
```
