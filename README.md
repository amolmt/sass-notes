## scss notes

- based on JS
- it is a superset of css
- compiles down to css
- used for:
  - clean code
  - makes you write fewer code so dev can write css faster
  - compatible with all versions of css

### general features

- nesting

```scss
.enlarge {
  font-size: 14px;
  transition: {
    property: font-size;
    duration: 4s;
    delay: 2s;
  }

  &:hover {
    font-size: 36px;
  }
}
```

- adding suffixes

  - scss code

  ```scss
  .accordion {
    max-width: 600px;
    margin: 4rem auto;
    width: 90%;
    font-family: "Raleway", sans-serif;
    background: #f4f4f4;

    &__copy {
      display: none;
      padding: 1rem 1.5rem 2rem 1.5rem;
      color: gray;
      line-height: 1.6;
      font-size: 14px;
      font-weight: 500;

      &--open {
        display: block;
      }
    }
  }
  ```

  - css code

  ```css
  .accordion {
    max-width: 600px;
    margin: 4rem auto;
    width: 90%;
    font-family: "Raleway", sans-serif;
    background: #f4f4f4;
  }
  .accordion__copy {
    display: none;
    padding: 1rem 1.5rem 2rem 1.5rem;
    color: gray;
    line-height: 1.6;
    font-size: 14px;
    font-weight: 500;
  }
  .accordion__copy--open {
    display: block;
  }
  ```

- placeholder selectors
  - these get emitted when not extended
  - used for reusing existing styles

```scss
%toolbelt {
  box-sizing: border-box;
  border-top: 1px rgba(#000, 0.12) solid;
  padding: 16px 0;
  width: 100%;

  &:hover {
    border: 2px rgba(#000, 0.5) solid;
  }
}

.action-buttons {
  @extend %toolbelt;
  color: #4285f4;
}
```

### benefits over traditional css

- syntax friendly
- offers variables
- uses nested syntax
- provides features such as mixins (for shortening the code)
- files can be seperated and merged (for code modularity)

### variables

Sass variables are simple: you assign a value to a name that begins with $, and then you can refer to that name instead of the value itself.

```scss
$base-color: #c6538c;
$border-dark: rgba($base-color, 0.88);

.alert {
  border: 1px solid $border-dark;
}
```

### at-rules

- @use loads mixins, functions, and variables from other Sass stylesheets, and combines CSS from multiple stylesheets together.

- @forward loads a Sass stylesheet and makes its mixins, functions, and variables available when your stylesheet is loaded with the @use rule.

- @import extends the CSS at-rule to load styles, mixins, functions, and variables from other stylesheets.

- @mixin and @include makes it easy to re-use chunks of styles.

- @function defines custom functions that can be used in SassScript expressions.

- @extend allows selectors to inherit styles from one another.

- @at-root puts styles within it at the root of the CSS document.

- Flow control rules like @if, @each, @for, and @while control whether or how many times styles are emitted.

```scss
@use "sass:map";

$theme-colors: (
  "success": #28a745,
  "info": #17a2b8,
  "warning": #ffc107,
);

.alert {
  background-color: map.get($theme-colors, "warning");
}
```

#### mixins and includes

- allows you to re-use code

  - scss code:

  ```scss
  @mixin corner-icon($name, $top-or-bottom, $left-or-right) {
    .icon-#{$name} {
      background-image: url("/icons/#{$name}.svg");
      position: absolute;
      #{$top-or-bottom}: 0;
      #{$left-or-right}: 0;
    }
  }

  @include corner-icon("mail", top, left);
  ```

  - css code:

  ```css
  .icon-mail {
    background-image: url("/icons/mail.svg");
    position: absolute;
    top: 0;
    left: 0;
  }
  ```

#### functions

- allows us to define complex operations that we can re-use.
- they make it easy to abstract out common formulas and behaviors in a readable way.

```scss
@function black($opacity) {
  @return rgba(black, $opacity);
}

@function white($opacity) {
  @return rgba(white, $opacity);
}

.my-class {
  background: black(0.15);
  color: white(0.9);
}
```
