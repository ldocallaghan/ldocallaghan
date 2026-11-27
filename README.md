I have eight years in software, mostly backend and research software, and an MSc in Applied Mathematics. This year I built BoreTHM, an open-source model for geothermal drilling, and tested it blind against field data. I have also contributed fixes to Mozilla's UniFFI, Qdrant and PyPSA-Eur.

I live in Berlin. You can reach me at liam.daniel.ocallaghan@gmail.com or on [LinkedIn](https://www.linkedin.com/in/ldocallaghan).

### Fixes in other projects

- [Mozilla UniFFI](https://github.com/mozilla/uniffi-rs/pull/2966). Fixed a code generation fault in the Kotlin and Swift backends that emitted source which would not compile, and the [same fault](https://github.com/jhugman/uniffi-bindgen-react-native/pull/438) in the TypeScript generator of uniffi-bindgen-react-native.
- [Qdrant](https://github.com/qdrant/qdrant/pull/10209). Fixed a build failure that stopped the project compiling at all on RISC-V, s390x and WebAssembly.
- [PyPSA-Eur](https://github.com/PyPSA/pypsa-eur/pull/2414). Fixed a constraint that meant flexible geothermal reservoirs never got any capacity, and reported a [second fault](https://github.com/PyPSA/pypsa-eur/issues/2415) in the same code.

### BoreTHM

[BoreTHM](https://github.com/ldocallaghan/BoreTHM) is an open-source Python model for assessing drilling programmes in superhot geothermal rock. There's no new physics required to make geothermal energy repeatable and cost-effective, just engineering problems to solve, and those solutions should be in the open.

I tested it blind on Utah FORGE wells, with the forecasts committed to the repository before the measurements were examined. On the two wells with reliable inlet records, the return temperature came out within about 2 °C RMS, where a standard analytical method had an error of 4 to 6 °C. After circulation stops, the model reheats the bottom of the hole too slowly, and that is the next thing to fix.

It has a [browser workbench](https://github.com/ldocallaghan/BoreTHM-Workbench) (FastAPI, React) that shows the well and its results in 3D.

<a href="https://github.com/ldocallaghan/BoreTHM-Workbench"><img src="https://raw.githubusercontent.com/ldocallaghan/BoreTHM-Workbench/main/docs/images/well-3d.png" width="640" alt="BoreTHM Workbench: 3D view of an inclined well, coloured by temperature"></a>

### kite-mcp and misclosure

[kite-mcp](https://github.com/ldocallaghan/kite-mcp) is an unofficial server that lets a language model run trade policy scenarios in KITE, the open-source trade models of the Kiel Institute. Every number it returns has to match a direct KITE run exactly. While testing it I found a fault in KITE's example data and [reported it](https://github.com/julianhinz/KITE/issues/21).

[misclosure](https://github.com/ldocallaghan/misclosure) was extracted from the tests of kite-mcp. It makes the same check on any MCP server that runs a scientific or engineering model.

### How I work

The modelling work and the fixes above were done with AI coding tools doing much of the implementation under my direction. I write the specification and check the results myself.
