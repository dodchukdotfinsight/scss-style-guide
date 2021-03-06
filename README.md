# Digitpaint (S)CSS Style Guide {

*A mostly reasonable approach to CSS and Sass stylesheets*

High level guidelines:

* Be consistent.
* Don't rewrite existing code to follow this guide.
* Don't violate a guideline without a good reason.
* A reason is good when you can convince a teammate.

## <a name='TOC'>Table of Contents</a>

1. [Whitespace](#whitespace)
1. [Naming Conventions](#naming-conventions)
1. [Comments](#comments)
1. [Browsers](#browsers)
1. [Media queries](#media-queries)
1. [Variables](#variables)
1. [Nesting](#nesting)
1. [Extends](#extends)
1. [Includes](#includes)
1. [License](#license)

## <a name='whitespace'>Whitespace</a>

- Use soft tabs set to 2 spaces
  
    ```scss
    // bad
    .selector {
    ∙∙∙∙property: value;
    } 

    // bad
    .selector {
    ∙property: value;
    } 

    // good
    .selector {
    ∙∙property: value;
    } 
    ```

- Indent every level (nesting, selector and property)

    ```scss
    // bad
    .selector {
    color: red;
    }

    // bad
    .selector {
    .nesting {
    color: red;
    }
    }

    // good
    .selector {
      .nesting {
        color: red;
      }
    }
    ```

- Place a space before the leading brace

    ```scss
    // bad
    .selector{
    }

    // good
    .selector {
    }
    ```

- Only write one selector per line

  ```scss
  // bad
  .selector, .selector2, .selector3 {
  }

  // good
  .selector,
  .selector2,
  .selector3 {
  }
  ```

- Separate rules by exactly one empty line
  
  ```scss
  // bad
  .selector {
  }
  .selector  {
  }


  .selector {
  }

  // good
  .selector {
  }

  .selector {
  }

  .selector {
  }  
  ```

- Only one property per line with a `;` directly after the property value

  ```scss
  // bad
  .selector {
    color: red; background: white;
    border: 1px solid red ;
  }

  // good
  .selector {
    color: red;
    background: white;
    border: 1px solid red;
  }
  ```

- Add exactly 1 space between the `:` and the property value;

  ```scss
  // bad
  .selector {
    color : red;
  }

  // bad
  .selector {
    color:red;
  }

  // good
  .selector {
    color: red;
  }
  ```

- 

## <a name='naming-conventions'>Naming conventions</a>

- Use BEM as much as possible (see Harry Robbert's excellend article ["MindBEMding – getting your head ’round BEM syntax"](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/) for an introduction)

    ```html
    <!-- bad -->
    <div class="weather header">
      <img src="sunny.png" class="icon">
      <p class="description">Sunny!</p>
    </div>


    <!-- good -->
    <div class="weather weather--header">
      <img src="sunny.png" class="weather__icon">
      <p class="weather__description">Sunny!</p>
    </div>
    ```
- Use full names instead of abbreviations.

    ```scss
    // bad
    .btn {
    }

    // good
    .button {
    }
    ```

- Use spinal-case (`.this-is-a-classname`) for class names, do not use uppercase letters in class names

    ```scss
    // bad
    .page_header {
    }

    // bad
    .pageHeader {
    }

    // good
    .page-header {
    }

    ```

**[[⬆]](#TOC)**

## <a name='comments'>Comments</a>

- Comment where necessary
- Write comments in proper English. Translate where necessary.

**[[⬆]](#TOC)**

## <a name='browser'>Browsers</a>

- Don't do manual vendorprefixing, use a tool like [autoprefixer](https://github.com/ai/autoprefixer) or [prefix-free](http://leaverou.github.io/prefixfree/. 

- Target features, not browsers. Prefer the use of `@supports` if possible, use modernizr otherwise.

- Only target IE < 9 with conditional comments.

**[[⬆]](#TOC)**

## <a name='media-queries'>Media queries</a>

TODO

## <a name='variables'>Variables</a>

TODO

**[[⬆]](#TOC)**

## <a name='nesting'>Nesting</a>

- Nest based on block name

- Don't mix properties and selectors in a nesting level. Use `&` instead.
  
    ```scss
    // bad
    .weather {
      color: #fff;

      .weather__icon {
        // ...
      }
    }

    // good
    .weather {
      & {
        color: #fff;
      }

      .weather__icon {
        // ...
      }
    }
    ```

- Nest up to a maximum of 2 levels. Too many levels of nesting make especially longer blocks of code unreadable.

    ```scss
    // bad
    .ice-cream {
      .ice-cream__cone {
        .ice-cream__cone__wrapper {
          // ...
        }
      }
    }

    // good
    .ice-cream {
      .ice-cream__cone .ice-cream__cone__wrapper {
         // ...
      }
    }
    ```

- Only point down with the `&` selector in a nesting, never up

    ```scss
    // bad
    .ice-cream {
      .desert & {
      }
    }

    // good
    .desert {
      .ice-cream {
      }
    }

    ```

**[[⬆]](#TOC)**

## <a name='extends'>Extends</a>

- Make abstract extends with `%name` instead of extending actual classes.

    ```scss
    // bad
    .page {
    }

    .page--home {
      @extend .page;
    }

    // good
    %centered-page {
    }

    .page {
      @extend %centered-page;
    }

    .page--home {
      @extend %centered-page;
    }
    ```

**[[⬆]](#TOC)**

## <a name='includes'>Includes</a>

TODO

**[[⬆]](#TOC)**

## <a name='license'>License</a>

(The MIT License)

Copyright (c) 2014 Digitpaint

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

**[[⬆]](#TOC)**

# }
