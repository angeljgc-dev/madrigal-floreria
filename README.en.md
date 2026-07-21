[Español](README.md) · **English**

# MADRIGAL — Signature florist · Seasonal bouquets

**Live demo → [https://b0b1a6ae23.github.io/madrigal-floreria/](https://b0b1a6ae23.github.io/madrigal-floreria/)**

![WebGL](https://img.shields.io/badge/WebGL1-raw%20shaders-990000?logo=webgl&logoColor=white)
![fake3d](https://img.shields.io/badge/fake3d-depth%20maps-6b8f71)
![GSAP](https://img.shields.io/badge/GSAP-ScrollTrigger-88CE02?logo=greensock&logoColor=black)

A signature florist built around **genuinely 3D imagery**: depth-mapped photographs
that tilt and breathe as they follow your cursor — the *fake3d* technique, hand-written
in raw WebGL1 with no frameworks.

| Hero | Section |
| --- | --- |
| ![Hero](docs/hero.png) | ![Section](docs/seccion.png) |

## Techniques

- **fake3d (akella style)**: a fragment shader that offsets the UV according to the
  depth map (`uv + (depth - 0.5) * mouse / threshold`), with a 5-tap depth blur in GLSL
  to soften edges, `mirrored()` at the bounds, resolution-driven cover-fit, and a 0.05 lerp.
- **Autonomous sine drift**: the photos "breathe" on their own when there is no cursor.
- Each photograph is paired with its own grayscale depth map.
- 4 WebGL instances, with a graceful fallback to `<img>` when the context fails.
- Documented gotcha: if local assets load faster than the layout, the canvas measures 0 —
  worked around by re-measuring with rAF + `setTimeout` after textures upload.
- Typefaces: Italiana + Marcellus + EB Garamond; still-life palette (#101511).

## Running locally

```bash
npx http-server . -p 8080
```

## License

Code released under the [MIT](LICENSE) license. **MADRIGAL** is a fictional brand created
to showcase portfolio work; any resemblance to a real business is coincidental. Third-party
assets (photographs, videos, and 3D models) retain their authors' original licenses — see Credits.

## Credits

Photography and video: [Pexels](https://www.pexels.com) · fake3d technique based on the
Ashima/akella experiment.

---
**Ángel Josué García Cantero** · *cinematic landing pages series*.
