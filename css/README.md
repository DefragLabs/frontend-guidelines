## CSS guidelines

### Use variables defined for adding css such as padding, margin, font-size etc

```
// variables.scss

$default-font-size: 10px;

$default-padding: 10px;

$default-margin: 10px;

$default-border-radius: 4px;

$default-line-height: 10px;
```

### For text/font use the defined mixins

```
@mixin set-font($font-family, $font-size, $color, $line-height, $text-align, $font-weight) {
  color: $color;
  font-size: $font-size;
  font-family: $font-family;
  line-height: $line-height;
  font-weight: $font-weight;
  text-align: $text-align;
}
```

### Define colors in a single css file before using it in

```
// colors.scss

$white: #FFFFFF;
$green: #2adb13;
```

### if images can be converted to fonts, prefer that. 

[icomooon](https://icomoon.io/) for converting images to fonts
