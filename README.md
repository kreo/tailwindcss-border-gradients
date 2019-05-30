# Border Gradients Plugin for Tailwind CSS

> This plugin is based on the [tailwindcss-gradients](https://github.com/benface/tailwindcss-gradients) plugin.

## Installation

```bash
npm install tailwindcss-border-gradients
```

## Simple usage

```js
{
  theme: {
    colors: {
      'red': '#f00',
      'blue': '#00f',
    },
    linearBorderGradients: theme => ({
      colors: theme('colors'),
    }),
    radialBorderGradients: theme => ({
      colors: theme('colors'),
    }),
  },
  plugins: [
    require('tailwindcss-border-gradients')(),
  ],
}
```

## Advanced usage

```js
{
  theme: {
    linearBorderGradients: {
      directions: { // defaults to these values
        't': 'to top',
        'tr': 'to top right',
        'r': 'to right',
        'br': 'to bottom right',
        'b': 'to bottom',
        'bl': 'to bottom left',
        'l': 'to left',
        'tl': 'to top left',
      },
      colors: { // defaults to {}
        'red': '#f00',
        'red-blue': ['#f00', '#00f'],
        'red-green-blue': ['#f00', '#0f0', '#00f'],
        'black-white-with-stops': ['#000', '#000 45%', '#fff 55%', '#fff'],
      },
    },
    radialBorderGradients: {
      shapes: { // defaults to this value
        'default': 'ellipse',
      },
      sizes: { // defaults to this value
        'default': 'closest-side',
      },
      positions: { // defaults to these values
        'default': 'center',
        't': 'top',
        'tr': 'top right',
        'r': 'right',
        'br': 'bottom right',
        'b': 'bottom',
        'bl': 'bottom left',
        'l': 'left',
        'tl': 'top left',
      },
      colors: { // defaults to {}
        'red': '#f00',
        'red-blue': ['#f00', '#00f'],
        'red-green-blue': ['#f00', '#0f0', '#00f'],
        'black-white-with-stops': ['#000', '#000 45%', '#fff 55%', '#fff'],
      },
    },
    repeatingLinearBorderGradients: theme => ({
      directions: theme('linearBorderGradients.directions'), // defaults to the same values as linearBorderGradients’ directions
      colors: theme('linearBorderGradients.colors'), // defaults to {}
      lengths: { // defaults to {}
        'sm': '25px',
        'md': '50px',
        'lg': '100px',
      },
    }),
    repeatingRadialBorderGradients: theme => ({
      shapes: { // defaults to this value
        'default': 'ellipse',
      },
      sizes: { // defaults to this value
        'default': 'farthest-corner',
      },
      positions: theme('radialBorderGradients.positions'), // defaults to the same values as radialBorderGradients’ positions
      colors: theme('radialBorderGradients.colors'), // defaults to {}
      lengths: { // defaults to {}
        'sm': '25px',
        'md': '50px',
        'lg': '100px',
      },
    }),
  },
  variants: {
    linearBorderGradients: ['responsive'], // defaults to ['responsive']
    radialBorderGradients: ['responsive'], // defaults to ['responsive']
    repeatingLinearBorderGradients: ['responsive'], // defaults to ['responsive']
    repeatingRadialBorderGradients: ['responsive'], // defaults to ['responsive']
  },
  plugins: [
    require('tailwindcss-border-gradients')(),
  ],
}
```

The plugin generates the following utilities:

```css
/* configurable with the "linearBorderGradients" theme object */
.border-gradient-[direction-key]-[color-key] {
  border-image: linear-gradient([direction-value], [color-value-1], [color-value-2], [...]);
}

/* configurable with the "radialBorderGradients" theme object */
/* note that the "default" [shape-key], [size-key], and [position-key] are omitted from the class */
.border-radial-[shape-key]-[size-key]-[position-key]-[color-key] {
  border-image: radial-gradient([shape-value] [size-value] at [position-value], [color-value-1], [color-value-2], [...]);
}

/* configurable with the "repeatingLinearBorderGradients" theme object */
.border-gradient-[direction-key]-[color-key]-[length-key] {
  border-image: repeating-linear-gradient([direction-value], [color-value-1], [color-value-2], [...] [length-value]);
}

/* configurable with the "repeatingRadialBorderGradients" theme object */
/* note that the "default" [shape-key], [size-key], and [position-key] are omitted from the class */
.border-radial-[shape-key]-[size-key]-[position-key]-[color-key]-[length-key] {
  border-image: repeating-radial-gradient([shape-value] [size-value] at [position-value], [color-value-1], [color-value-2], [...] [length-value]);
}
```