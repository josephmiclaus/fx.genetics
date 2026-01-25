# $fx.genetics ($DNA)

A genetics library for fxhash open-form generative artworks, modeling trait inheritance and evolution across generations.

## Example

```js
const schema = [
    { name: "Shape", variants: ["Ellipse", "Rectangle", "Triangle"] },
    { name: "Color", variants: ["Red", "Green", "Blue"] },
    { name: "Chaos", variants: [0, 50, 100] },
    { name: "Grain", variants: [true, false] },
];

$fx.genetics(schema).evolve(); // <-- magic

drawShape(
    $fx.getFeature("Shape"),
    $fx.getFeature("Color"),
    $fx.getFeature("Chaos"),
    $fx.getFeature("Grain"),
);
```

## LICENSE

Copyright (c) 2026 Joseph Miclaus. All rights reserved.

For licensing inquiries, contact the author.
