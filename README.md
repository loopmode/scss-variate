# @loopmode/scss-variate

A collection of SCSS mixins.

## variate

Generates variations of a given style property.

```scss
@mixin variate($style, $sizes, $variations, $withUnits);
```

| option        | description                                                                                    | default value                              |
| ------------- | ---------------------------------------------------------------------------------------------- | ------------------------------------------ |
| `$style`      | The name of a css style property to variate                                                    | -                                          |
| [`$sizes`](#the-sizes-option)      | A list of size values for variations. May include units or percents (stripped for zero-values) | `(0px, 5px, 10px, 20px, 40px, 80px, auto)` |
| [`$variations`](#the-variations-option) | A list of variation names for the given `$style`                                               | `('', 'top', 'left', 'bottom', 'right')`   |
| [`$withUnits`](#the-withunits-option)  | Whether to additionally generate class names with concrete units                               | `false`                                    |

Note: You can pass `null` for an option to use its default value.

### Usage

#### Without any options

This will create a whole bunch of helper classes based on the default options. See output examples at the bottom.

```scss
@import "~@loopmode/scss-variate";
variate(margin);
variate(padding);
```

#### The `$sizes` option

Specifies a custom list of values.

The default value list is pixel-based and in steps of 5px. That may or may not fit well with your project.
However, you can specify a custom list of sizes/values that do fit your project's needs:

```scss
@import "~@loopmode/scss-variate";

$sizes: (0, 0.6rem, 1.2rem, 2.4rem, 4.8rem, 50%, 100%);
@include variate(margin, $sizes);
@include variate(padding, $sizes);
```

#### The `$variations` option

Specifies a custom list of variations.

The default variations list contains an empty string plus all available sides, which generates e.g. `margin`, `margin-top`, `margin-bottom`, `margin-left` and `margin-right` variations.

However, you can also specify your own list of variations if you don't care for all those sides.

```scss
@import "~@loopmode/scss-variate";

$variations: (top, left);
@include variate(margin, null, $variations);
```

_Note: You can pass `null` to use the default value of an option!_

#### The `$withUnits` option

Creates additional classnames that contain concrete values instead of step numbers.

```scss
@import "~@loopmode/scss-variate";

@include variate(margin, null, null, true);
```

The default behaviour creates "step-based" class names. For example, if you create paddings for a list of values `(0px, 5px, 10px)`, the created classnames would be `.p-0, p-1, .p-2`.

```scss
@include variate(margin, (0px, 5px, 10px), (""));
```

```css
.m-0 {
  margin: 0;
}

.m-1 {
  margin: 5px;
}

.m-2 {
  margin: 10px;
}
```

However, if you specify `true` for the last option `$withUnits`, unit-based classnames will be generated additionally:

```scss
@include variate(margin, (0px, 5px, 10px), (""), true);
```

```css
.m-0,
.m-0px {
  margin: 0;
}

.m-1,
.m-5px {
  margin: 5px;
}

.m-2,
.m-10px {
  margin: 10px;
}
```

### Example output

The generated output for some examples.

#### Default

The default behavior, without any additional options.

```scss
@include '~@loopmode/scss-variate';
variate(margin);
variate(padding);
```

```css
.m-0 {
  margin: 0;
}

.mt-0 {
  margin-top: 0;
}

.ml-0 {
  margin-left: 0;
}

.mb-0 {
  margin-bottom: 0;
}

.mr-0 {
  margin-right: 0;
}

.m-1 {
  margin: 5px;
}

.mt-1 {
  margin-top: 5px;
}

.ml-1 {
  margin-left: 5px;
}

.mb-1 {
  margin-bottom: 5px;
}

.mr-1 {
  margin-right: 5px;
}

.m-2 {
  margin: 10px;
}

.mt-2 {
  margin-top: 10px;
}

.ml-2 {
  margin-left: 10px;
}

.mb-2 {
  margin-bottom: 10px;
}

.mr-2 {
  margin-right: 10px;
}

.m-3 {
  margin: 20px;
}

.mt-3 {
  margin-top: 20px;
}

.ml-3 {
  margin-left: 20px;
}

.mb-3 {
  margin-bottom: 20px;
}

.mr-3 {
  margin-right: 20px;
}

.m-4 {
  margin: 40px;
}

.mt-4 {
  margin-top: 40px;
}

.ml-4 {
  margin-left: 40px;
}

.mb-4 {
  margin-bottom: 40px;
}

.mr-4 {
  margin-right: 40px;
}

.m-5 {
  margin: 80px;
}

.mt-5 {
  margin-top: 80px;
}

.ml-5 {
  margin-left: 80px;
}

.mb-5 {
  margin-bottom: 80px;
}

.mr-5 {
  margin-right: 80px;
}

.m-auto {
  margin: auto;
}

.mt-auto {
  margin-top: auto;
}

.ml-auto {
  margin-left: auto;
}

.mb-auto {
  margin-bottom: auto;
}

.mr-auto {
  margin-right: auto;
}

.p-0 {
  padding: 0;
}

.pt-0 {
  padding-top: 0;
}

.pl-0 {
  padding-left: 0;
}

.pb-0 {
  padding-bottom: 0;
}

.pr-0 {
  padding-right: 0;
}

.p-1 {
  padding: 5px;
}

.pt-1 {
  padding-top: 5px;
}

.pl-1 {
  padding-left: 5px;
}

.pb-1 {
  padding-bottom: 5px;
}

.pr-1 {
  padding-right: 5px;
}

.p-2 {
  padding: 10px;
}

.pt-2 {
  padding-top: 10px;
}

.pl-2 {
  padding-left: 10px;
}

.pb-2 {
  padding-bottom: 10px;
}

.pr-2 {
  padding-right: 10px;
}

.p-3 {
  padding: 20px;
}

.pt-3 {
  padding-top: 20px;
}

.pl-3 {
  padding-left: 20px;
}

.pb-3 {
  padding-bottom: 20px;
}

.pr-3 {
  padding-right: 20px;
}

.p-4 {
  padding: 40px;
}

.pt-4 {
  padding-top: 40px;
}

.pl-4 {
  padding-left: 40px;
}

.pb-4 {
  padding-bottom: 40px;
}

.pr-4 {
  padding-right: 40px;
}

.p-5 {
  padding: 80px;
}

.pt-5 {
  padding-top: 80px;
}

.pl-5 {
  padding-left: 80px;
}

.pb-5 {
  padding-bottom: 80px;
}

.pr-5 {
  padding-right: 80px;
}

.p-auto {
  padding: auto;
}

.pt-auto {
  padding-top: auto;
}

.pl-auto {
  padding-left: auto;
}

.pb-auto {
  padding-bottom: auto;
}

.pr-auto {
  padding-right: auto;
}
```

#### Specific

Generate just a few classes based on specific options:

```scss
@import "~@loopmode/scss-variate";
@include variate(margin, (0px, 5px), (top, right));
```

```css
.mt-0 {
  margin-top: 0;
}

.mr-0 {
  margin-right: 0;
}

.mt-1 {
  margin-top: 5px;
}

.mr-1 {
  margin-right: 5px;
}
```

#### Bells and whistles

Notice that you could be generating a lot of CSS output, depending on your usage:

```scss
@import "~@loopmode/scss-variate";

html,
body {
  @include variate(margin, null, null, true);
  @include variate(padding, null, null, true);
}
```

```css
html .m-0,
html .m-0px,
body .m-0,
body .m-0px {
  margin: 0;
}

html .mt-0,
html .mt-0px,
body .mt-0,
body .mt-0px {
  margin-top: 0;
}

html .ml-0,
html .ml-0px,
body .ml-0,
body .ml-0px {
  margin-left: 0;
}

html .mb-0,
html .mb-0px,
body .mb-0,
body .mb-0px {
  margin-bottom: 0;
}

html .mr-0,
html .mr-0px,
body .mr-0,
body .mr-0px {
  margin-right: 0;
}

html .m-1,
html .m-5px,
body .m-1,
body .m-5px {
  margin: 5px;
}

html .mt-1,
html .mt-5px,
body .mt-1,
body .mt-5px {
  margin-top: 5px;
}

html .ml-1,
html .ml-5px,
body .ml-1,
body .ml-5px {
  margin-left: 5px;
}

html .mb-1,
html .mb-5px,
body .mb-1,
body .mb-5px {
  margin-bottom: 5px;
}

html .mr-1,
html .mr-5px,
body .mr-1,
body .mr-5px {
  margin-right: 5px;
}

html .m-2,
html .m-10px,
body .m-2,
body .m-10px {
  margin: 10px;
}

html .mt-2,
html .mt-10px,
body .mt-2,
body .mt-10px {
  margin-top: 10px;
}

html .ml-2,
html .ml-10px,
body .ml-2,
body .ml-10px {
  margin-left: 10px;
}

html .mb-2,
html .mb-10px,
body .mb-2,
body .mb-10px {
  margin-bottom: 10px;
}

html .mr-2,
html .mr-10px,
body .mr-2,
body .mr-10px {
  margin-right: 10px;
}

html .m-3,
html .m-20px,
body .m-3,
body .m-20px {
  margin: 20px;
}

html .mt-3,
html .mt-20px,
body .mt-3,
body .mt-20px {
  margin-top: 20px;
}

html .ml-3,
html .ml-20px,
body .ml-3,
body .ml-20px {
  margin-left: 20px;
}

html .mb-3,
html .mb-20px,
body .mb-3,
body .mb-20px {
  margin-bottom: 20px;
}

html .mr-3,
html .mr-20px,
body .mr-3,
body .mr-20px {
  margin-right: 20px;
}

html .m-4,
html .m-40px,
body .m-4,
body .m-40px {
  margin: 40px;
}

html .mt-4,
html .mt-40px,
body .mt-4,
body .mt-40px {
  margin-top: 40px;
}

html .ml-4,
html .ml-40px,
body .ml-4,
body .ml-40px {
  margin-left: 40px;
}

html .mb-4,
html .mb-40px,
body .mb-4,
body .mb-40px {
  margin-bottom: 40px;
}

html .mr-4,
html .mr-40px,
body .mr-4,
body .mr-40px {
  margin-right: 40px;
}

html .m-5,
html .m-80px,
body .m-5,
body .m-80px {
  margin: 80px;
}

html .mt-5,
html .mt-80px,
body .mt-5,
body .mt-80px {
  margin-top: 80px;
}

html .ml-5,
html .ml-80px,
body .ml-5,
body .ml-80px {
  margin-left: 80px;
}

html .mb-5,
html .mb-80px,
body .mb-5,
body .mb-80px {
  margin-bottom: 80px;
}

html .mr-5,
html .mr-80px,
body .mr-5,
body .mr-80px {
  margin-right: 80px;
}

html .m-auto,
body .m-auto {
  margin: auto;
}

html .mt-auto,
body .mt-auto {
  margin-top: auto;
}

html .ml-auto,
body .ml-auto {
  margin-left: auto;
}

html .mb-auto,
body .mb-auto {
  margin-bottom: auto;
}

html .mr-auto,
body .mr-auto {
  margin-right: auto;
}

html .p-0,
html .p-0px,
body .p-0,
body .p-0px {
  padding: 0;
}

html .pt-0,
html .pt-0px,
body .pt-0,
body .pt-0px {
  padding-top: 0;
}

html .pl-0,
html .pl-0px,
body .pl-0,
body .pl-0px {
  padding-left: 0;
}

html .pb-0,
html .pb-0px,
body .pb-0,
body .pb-0px {
  padding-bottom: 0;
}

html .pr-0,
html .pr-0px,
body .pr-0,
body .pr-0px {
  padding-right: 0;
}

html .p-1,
html .p-5px,
body .p-1,
body .p-5px {
  padding: 5px;
}

html .pt-1,
html .pt-5px,
body .pt-1,
body .pt-5px {
  padding-top: 5px;
}

html .pl-1,
html .pl-5px,
body .pl-1,
body .pl-5px {
  padding-left: 5px;
}

html .pb-1,
html .pb-5px,
body .pb-1,
body .pb-5px {
  padding-bottom: 5px;
}

html .pr-1,
html .pr-5px,
body .pr-1,
body .pr-5px {
  padding-right: 5px;
}

html .p-2,
html .p-10px,
body .p-2,
body .p-10px {
  padding: 10px;
}

html .pt-2,
html .pt-10px,
body .pt-2,
body .pt-10px {
  padding-top: 10px;
}

html .pl-2,
html .pl-10px,
body .pl-2,
body .pl-10px {
  padding-left: 10px;
}

html .pb-2,
html .pb-10px,
body .pb-2,
body .pb-10px {
  padding-bottom: 10px;
}

html .pr-2,
html .pr-10px,
body .pr-2,
body .pr-10px {
  padding-right: 10px;
}

html .p-3,
html .p-20px,
body .p-3,
body .p-20px {
  padding: 20px;
}

html .pt-3,
html .pt-20px,
body .pt-3,
body .pt-20px {
  padding-top: 20px;
}

html .pl-3,
html .pl-20px,
body .pl-3,
body .pl-20px {
  padding-left: 20px;
}

html .pb-3,
html .pb-20px,
body .pb-3,
body .pb-20px {
  padding-bottom: 20px;
}

html .pr-3,
html .pr-20px,
body .pr-3,
body .pr-20px {
  padding-right: 20px;
}

html .p-4,
html .p-40px,
body .p-4,
body .p-40px {
  padding: 40px;
}

html .pt-4,
html .pt-40px,
body .pt-4,
body .pt-40px {
  padding-top: 40px;
}

html .pl-4,
html .pl-40px,
body .pl-4,
body .pl-40px {
  padding-left: 40px;
}

html .pb-4,
html .pb-40px,
body .pb-4,
body .pb-40px {
  padding-bottom: 40px;
}

html .pr-4,
html .pr-40px,
body .pr-4,
body .pr-40px {
  padding-right: 40px;
}

html .p-5,
html .p-80px,
body .p-5,
body .p-80px {
  padding: 80px;
}

html .pt-5,
html .pt-80px,
body .pt-5,
body .pt-80px {
  padding-top: 80px;
}

html .pl-5,
html .pl-80px,
body .pl-5,
body .pl-80px {
  padding-left: 80px;
}

html .pb-5,
html .pb-80px,
body .pb-5,
body .pb-80px {
  padding-bottom: 80px;
}

html .pr-5,
html .pr-80px,
body .pr-5,
body .pr-80px {
  padding-right: 80px;
}

html .p-auto,
body .p-auto {
  padding: auto;
}

html .pt-auto,
body .pt-auto {
  padding-top: auto;
}

html .pl-auto,
body .pl-auto {
  padding-left: auto;
}

html .pb-auto,
body .pb-auto {
  padding-bottom: auto;
}

html .pr-auto,
body .pr-auto {
  padding-right: auto;
}
```
