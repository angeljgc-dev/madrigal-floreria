[Español](README.md) · **English**

# MADRIGAL · Signature florist · Seasonal bouquets

Live demo: https://angeljgc-dev.github.io/madrigal-floreria/

![WebGL](https://img.shields.io/badge/WebGL1-raw%20shaders-990000?logo=webgl&logoColor=white)
![fake3d](https://img.shields.io/badge/fake3d-depth%20maps-6b8f71)
![GSAP](https://img.shields.io/badge/GSAP-ScrollTrigger-88CE02?logo=greensock&logoColor=black)

A signature florist built around imagery that actually reads as 3D: depth-mapped photos
that tilt and breathe as they follow your cursor. It's the fake3d technique, written by
hand in raw WebGL1 with no frameworks.

| Hero | Section |
| --- | --- |
| ![Hero](docs/hero.png) | ![Section](docs/seccion.png) |

## Techniques

- **fake3d (akella style)**: a fragment shader offsets the UV from the depth map
  (`uv + (depth - 0.5) * mouse / threshold`). I added a 5-tap depth blur in GLSL to soften
  the edges, `mirrored()` at the bounds, resolution-driven cover-fit, and a 0.05 lerp.
- With no cursor around, the photos keep drifting on their own along a sine wave.
- Every photo is paired with its own grayscale depth map.
- There are 4 WebGL instances, and if the context fails they fall back to `<img>`.
- One gotcha that cost me some time: if the local assets load before the layout, the canvas
  measures 0. I fixed it by re-measuring with rAF and a `setTimeout` once the textures upload.
- Typefaces: Italiana + Marcellus + EB Garamond; a still-life palette (#101511).

## Running locally

```bash
npx http-server . -p 8080
```

## License

Released under the [MIT](LICENSE) license. MADRIGAL is a made-up brand for portfolio work, not
a real shop. Third-party assets (photos, videos, 3D models) keep their authors' licenses; see
Credits for the details.

## Credits

Photography and video: [Pexels](https://www.pexels.com) · fake3d technique based on the
Ashima/akella experiment.

---
Ángel Josué García Canteros · cinematic landing pages series.
