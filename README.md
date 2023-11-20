# tex2math

> _Warning_
>
> `tex2math` is currently in development, do not yet use it in production.

Compile latex math to mathml.

## Features:

- embedable library & standalone cli tool
- low memory footprint
- very fast conversion
- high performance
- zero dependencies
- custom macros

## Usage

### Cli tool

```shell
$ cat math.tex
\sqrt{5} \pm x_i
$ tex2math -i math.tex
<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mrow>
    <msqrt>
      <mn>5</mn>
    </msqrt>
    <mo>±</mo>
  </mrow>
  <mrow>
    <msub>
      <mi>x</mi>
      <mi>i</mi>
    </msub>
  </mrow>
</math>
```

### Library

```go
package main

import (
    "fmt"
    "github.com/xnacly/tex2math" t2m
)

func main() {
    expression := "\sqrt{5} \pm x_i"
    converter := t2m.New() // creates necessary internal structures for high performance conversion
    mathml, err := converter.Convert(expression)
    if err != nil {
        panic(err) // can occur on invalid symbols, expressions, missing closing braces, etc
    }
    fmt.Println(mathml) // resulting output
}
```

## Supported features

> Math features taken from [LaTeX/Mathematics](https://en.wikibooks.org/wiki/LaTeX/Mathematics)

### Relation symbols

### Binary operations

### Set, Logic

### Delimiters

| Implemented | Symbol | Script       |
| ----------- | ------ | ------------ |
|             | \|     | `\|`, `\mid` |
|             | {      | `\{`         |
|             | ↑      | `\uparrow`   |
|             | ↓      | `\downarrow` |
|             | ‖      | `\|`         |
|             | }      | `\}`         |
|             | ⇑      | `\Uparrow`   |
|             | ⇓      | `\Downarrow` |
|             | /      | `/`          |
|             | ⟨      | `\langle`    |
|             | ⌈      | `\lceil`     |
|             | ⌊      | `\lfloor`    |
|             | ∖      | `\backslash` |
|             | ⟩      | `\rangle`    |
|             | ⌉      | `\rceil`     |
|             | ⌋      | `\rfloor`    |

### Greek Letters

| Implemented | Symbol  | Script                         |
| ----------- | ------- | ------------------------------ |
|             | A, α    | `A`, `\alpha`                  |
|             | B, β    | `B`, `\beta`                   |
|             | Γ, γ    | `\Gamma`, `\gamma`             |
|             | Δ, δ    | `\Delta`, `\delta`             |
|             | E, ϵ, ε | `E`, `\epsilon`, `\varepsilon` |
|             | Z, ζ    | `Z`, `\zeta`                   |
|             | H, η    | `H`, `\eta`                    |
|             | Θ, θ, ϑ | `\Theta`, `\theta`, \vartheta  |
|             | I, ι    | `I`, `\iota`                   |
|             | K, κ    | `\kappa`, `\varkappa`          |
|             | Λ, λ    | `\Lambda`, `\lambda`           |
|             | M, μ    | `M`, `\mu`                     |

### Trigonometric functions

| Implemented | Symbol | Script    |
| ----------- | ------ | --------- |
|             | sin    | `\sin`    |
|             | cos    | `\cos`    |
|             | tan    | `\tan`    |
|             | cot    | `\cot`    |
|             | arcsin | `\arcsin` |
|             | arccos | `\arccos` |
|             | arctan | `\arctan` |
|             | sinh   | `\sinh`   |
|             | cosh   | `\cosh`   |
|             | tanh   | `\tanh`   |
|             | coth   | `\coth`   |
|             | sec    | `\sec`    |
|             | csc    | `\csc`    |

### Other

| Implemented | Symbol | Script |
| ----------- | ------ | ------ |
