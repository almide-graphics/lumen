# lumen

Pure graphics math primitives for [Almide](https://github.com/almide/almide). No `@extern(wasm)` — works on every target.

## Install

```toml
[dependencies]
lumen = { git = "https://github.com/almide/lumen.git" }
```

## Modules

### lumen.vec3

```almide
import lumen.vec3 as v

let a = v.new(1.0, 2.0, 3.0)
let b = v.new(4.0, 5.0, 6.0)
let c = v.add(a, b)                 // (5, 7, 9)
let d = v.dot(a, b)                 // 32.0
let n = v.normalize(a)              // unit length
let x = v.cross(v.right(), v.up())  // (0, 0, 1)
let m = v.lerp(a, b, 0.5)          // midpoint
```

### lumen.mat4

```almide
import lumen.mat4 as mat

let model = mat.identity()
  |> mat.rotate_y(0.5)
  |> mat.translate(0.0, 1.0, -5.0)
let view = mat.look_at(0.0, 0.0, 5.0, 0.0, 0.0, 0.0, 0.0, 1.0, 0.0)
let proj = mat.perspective(0.785, 1.333, 0.1, 100.0)
let mvp = mat.multiply(proj, mat.multiply(view, model))
```

### lumen.color

```almide
import lumen.color as c

let red = c.rgb(1.0, 0.0, 0.0)
let sky = c.from_hex("#87CEEB")
let mid = c.mix(red, sky, 0.5)
let dim = c.darken(sky, 0.3)
let css = c.to_css(c.with_alpha(sky, 0.8))  // "rgba(135,206,235,0.8)"
```

## Used by

- [wasm-webgl](https://github.com/almide/wasm-webgl) — WebGL bindings
- [wasm-canvas](https://github.com/almide/wasm-canvas) — Canvas 2D bindings
- [obsid](https://github.com/almide/obsid) — 3D rendering foundation

## License

MIT
