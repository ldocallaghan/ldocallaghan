I’m a software engineer in Berlin with eight years of experience, mostly in backend and research software, and an MSc in Applied Mathematics. I built BoreTHM, an open-source geothermal drilling model, and tested its temperature forecasts blind against field data. I’ve also contributed fixes to Mozilla’s UniFFI, Qdrant, and PyPSA-Eur.

You can reach me at [liam.daniel.ocallaghan@gmail.com](mailto:liam.daniel.ocallaghan@gmail.com) or on [LinkedIn](https://www.linkedin.com/in/ldocallaghan).

### BoreTHM

[BoreTHM](https://github.com/ldocallaghan/BoreTHM) is an open-source Python model for assessing drilling programmes in superhot geothermal rock. I built it so researchers and engineers can inspect and improve the assumptions behind its forecasts.

I tested BoreTHM on Utah FORGE wells, committing the forecasts to the repository before examining the measured return temperatures. On the two wells with reliable inlet records, the return-temperature RMSE was about 2 °C, compared with 4–6 °C for a standard analytical method. After circulation stops, the model predicts slower reheating at the bottom of the hole than the measurements show. That’s the next thing I want to fix.

The [BoreTHM Workbench](https://github.com/ldocallaghan/BoreTHM-Workbench) uses FastAPI and React to show the well and simulation results in 3D.

<a href="https://github.com/ldocallaghan/BoreTHM-Workbench"><img src="https://raw.githubusercontent.com/ldocallaghan/BoreTHM-Workbench/main/docs/images/well-3d.png" width="640" alt="3D view of an inclined well coloured by temperature in the BoreTHM Workbench"></a>

### Open-source contributions

- [Mozilla UniFFI](https://github.com/mozilla/uniffi-rs/pull/2966). Fixed a bug that caused the Kotlin and Swift generators to emit code that wouldn’t compile. I fixed the [same bug](https://github.com/jhugman/uniffi-bindgen-react-native/pull/438) in the TypeScript generator for uniffi-bindgen-react-native.
- [Qdrant](https://github.com/qdrant/qdrant/pull/10209). Fixed a build failure affecting RISC-V, s390x, and WebAssembly.
- [PyPSA-Eur](https://github.com/PyPSA/pypsa-eur/pull/2414). Fixed a constraint that prevented flexible geothermal reservoirs from receiving any capacity and reported a [second bug](https://github.com/PyPSA/pypsa-eur/issues/2415) in the same code.

### kite-mcp and misclosure

[kite-mcp](https://github.com/ldocallaghan/kite-mcp) is an unofficial MCP server that lets language models run trade policy scenarios using the Kiel Institute’s open-source KITE models. Its tests check that numerical outputs exactly match direct KITE runs. While testing it, I found and [reported a bug](https://github.com/julianhinz/KITE/issues/21) in KITE’s example data.

I extracted [misclosure](https://github.com/ldocallaghan/misclosure) from those tests so the same check can be applied to other MCP servers that run scientific or engineering models.

### How I work

I wrote the specifications and verified the results myself. AI coding tools handled much of the implementation under my direction.