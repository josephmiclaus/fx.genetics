<a id="top"></a>

# fx.genetics

A genetics library for [fxhash open-form generative artworks](https://docs.fxhash.xyz/creating-on-fxhash/programming-open-form-genart), modeling trait inheritance and evolution across generations. Think CryptoKitties-inspired crossing for open-form generative artworks.

It simplifies the evolution phase of open-form pieces and brings organic digital evolution to generative artworks. Generative artists no longer need to worry about manually handling how traits evolve with depth – the genetics system takes care of it. This lets you focus on designing and implementing how those traits actually manifest in your artwork.

The library is distributed as browser-ready JavaScript files and is currently [proprietary](#license). An open-source release may be considered in the future based on community support. For licensing inquiries, [contact the author](#support).

## What it enables
- Combine two pieces from the lineage and produce an offspring from the parents traits
- Enable trait mutations triggered by specific parent trait combinations
- Automatic feature registration with `$fx.features()`
- Configurable genetics for open-form projects, including:
  - Parent selection from lineage (built-ins or custom strategy)
  - Hidden variant counts per trait and their swap/weight chances
  - Mutation rules based on parent traits and depth-based chances
  - Anomaly injection by depth-based chances

## Quick start
Install via npm:

```bash
npm i fx.genetics
```

At runtime, use the browser build (not a Node module). Include fxhash first, then fx.genetics:

```html
<script src="./fxhash.min.js"></script>
<script src="./fx.genetics.min.js"></script>
<script src="./index.js"></script>
```

## Example
An example showing schema definition, configuration, evolution, and trait access:

```js
const schema = [
    { id: "S", name: "Shape", variants: ["Ellipse", "Rectangle"],
        mutations: [{
            value: "Triangle", requires: ["S:Ellipse", "S:Rectangle"]
        }]
    },
    { name: "Color", variants: ["Red", "Green", "Blue"] },
    { name: "Chaos", variants: [0, 50, 100] },
    { name: "Grain", variants: [true, false] },
];

$fx.genetics(schema)
    .mode("tiered")             // CryptoKittes-inspired crossing
    .parents("sliding")         // defines how parents are selected
    .hidden([0.25, 0.25, 0.25]) // defines hidden traits chances
    .mutations([0, 0.15, 0.25]) // defines mutation chances by depth
    .anomalies([0, 0.05])       // defines anomaly chances by depth
    .evolve();

// Features are registered automatically with fxhash
// $fx.features() now includes Shape, Color, Chaos, Grain

// Access the expressed traits (phenotype) for the current iteration:
const shapeViaFeature = $fx.getFeature("Shape");
const shapeViaName = $DNA.getTrait("Shape").value;
const shapeViaId = $DNA.getTrait("#S").value;

// Trait identifiers can be the gene name ("Shape") or the gene id ("#S")
```

> **Note:** `$DNA` is a convenience alias for `$fx.genetics`. For example:
>
> ```js
> $DNA(schema).evolve();
> // is the same as:
> $fx.genetics(schema).evolve();
>
> const trait = $DNA.getTrait("Shape").value;
> // is the same as:
> const trait = $fx.genetics.getTrait("Shape").value;
> ```

[Go to top ⬆](#top)


<a id="support"></a>

## Support

Need help or found issues?
- Open an issue on [GitHub](https://github.com/josephmiclaus/fx.genetics/issues)
- DM the author on [𝕏 @josephmiclaus](https://x.com/josephmiclaus)

License holders receive the full in-depth `REFERENCE.md` library documentation.


<a id="license"></a>

## License

Copyright (c) 2026 Joseph Miclaus. All rights reserved.

For licensing inquiries, contact the author.
