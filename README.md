## scss notes

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
  these get emitted when not extended

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

### why scss?

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

###
