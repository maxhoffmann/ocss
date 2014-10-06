OCSS (Object CSS)
=================

A CSS preprocessor that restricts you to use best practices. Its goal is to make it easy to do the right thing and hard to do the wrong thing.

OCSS is intended for large scale web products, but it can also help to keep clean CSS in smaller projects. Its philosophy is to build pages/views out of multiple CSS objects that are independent of each other.

This repository is for the command line interface (CLI) of the OCSS parser. The parsing and stringifiing logic plus the [live editor](http://maxhoffmann.github.io/ocss-parser/) are inside the [ocss-parser](https://github.com/maxhoffmann/ocss-parser) repository.


What if
-------

- classes are the default?
- nesting compiles to BEM?
- IDs and `!important` would throw an error?
- objects can’t be overwritten outside of theirs files?
- the compiler throws an error if you already have an object with the same name?
- nesting deeper than 3 levels would throw an error?
- tags have to live inside of one single file?
- nesting objects is not possible?
- modifiers can only be added to objects (not elements of an object)?
- there are files that define the relationship between two objects?
- renaming an object is as simple as renaming a file?
- prefixing objects is as simple as putting them in a folder?
- the preprocessor could generate a documentation of all objects?
- rules can be easily added via plugins?

FAQ
--------

- Why disallowing IDs?
  - They prevent reuse and have no advantage to classes.
- Why preventing tags in every file?
  - Tags should only be used as a general baseline as it’s easy to overwrite other styles using them. (can only be included in `tags.css`)
- Why shouldn’t you add modifiers to element of an object?
  - If an element is worth to have a modifier, it has state and should therefore be an object.
- Why shouldn’t you nest objects?
  - Nesting objects creates a direct relationship between components. This reduces reusability and adds dependencies inside your style system. Instead of changing properties of another object, add modifiers to it and to apply changes depending on state.
- Why can’t I use dashes?
  - Dashes are used by the compiler to create scopes. You can use underscores instead.
- Why shouldn’t I use `!important`?
  - It’s the start of most specificity wars.
- Why can’t I have one object spread across different files?
  - One file for each object adheres to the single source of truth principle. This allows you to easily see all the styles related to one object.
