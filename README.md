## scss notes

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
