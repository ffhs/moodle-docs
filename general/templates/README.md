---
description: >-
  Templates are written in a language called "Mustache". Mustache is written as
  HTML with additional tags used to format the display of the data.
---

# Templates

## Introduction

A template is an alternative to writing blocks of HTML directly in javascript / php by concatenating strings. The end result is the same, but templates have a number of advantages:

* It is easier to see the final result of the template because the code for a template is very close to what the final HTML will look like
* Because the templating language is intentionally limited, it is hard to introduce complex logic into a template. This makes it far easier for a theme designer to override a template, without breaking the logic
* Templates can be rendered from javascript. This allows ajax operations to re-render a portion of the page.

More information under 

[https://docs.moodle.org/dev/Templates](https://docs.moodle.org/dev/Templates)

## Directives

#### Translate string

```markup
{{#str}} summary, block_ffhs_myoverview {{/str}}
```

