### Liam O'Callaghan

Research software engineer in Berlin.

### BoreTHM

Rock at 400 °C and above can yield several times more energy per well than conventional geothermal resources. Drilling into it is limited by the temperature of the downhole tools, most of which are rated to 200 °C or less, and by the stability of the borehole wall. Cold drilling fluid circulated down the pipe lowers the tool temperature. It also cools the wall, which changes the stresses around the hole, and the fluid density needed to keep the wall stable affects the circulating pressures and flow. The temperature and stability calculations therefore depend on each other.

[BoreTHM](https://github.com/ldocallaghan/BoreTHM) is an open-source set of models that solves them together for a given site and drilling programme. It calculates fluid and rock temperatures through drilling, connections and trips, and checks at each depth whether the tools stay below their temperature limit and whether a fluid density exists that keeps the wall stable without fracturing the formation. A separate design study changes one part of the programme at a time, such as the casing depth, the drill pipe insulation, the mud viscosity or the flow rate, and records which checks each version passes.

The circulation model has been compared with drilling data from Utah FORGE well 16B. With its parameters fitted on the other runs, it predicted the run with partly insulated pipe to within 2 to 4 °C. I then tested it blind on three more FORGE wells, with the forecasts committed to the repository before the measurements were examined. On the two wells with reliable inlet records, the return temperature came out within about 2 °C RMS, where a standard analytical method had an error of 4 to 6 °C. After circulation stops, the model reheats the bottom of the hole too slowly, and that is the next thing to fix. Rock strength is calibrated on the breakouts logged in UD-1 at United Downs and checked against the Soultz wells.

Apache-2.0, on PyPI as `borethm`, DOI [10.5281/zenodo.23549104](https://doi.org/10.5281/zenodo.23549104).

### Open source contributions

- **[Mozilla, UniFFI bindings generator](https://github.com/mozilla/uniffi-rs/pull/2966).** Fixed a code generation fault in the Kotlin and Swift backends that emitted source which would not compile, closing [#2411](https://github.com/mozilla/uniffi-rs/issues/2411).
- **[Qdrant, core repo](https://github.com/qdrant/qdrant/pull/10209).** Fixed a build failure that stopped the project compiling at all on RISC-V, s390x and WebAssembly.
- **[uniffi-bindgen-react-native](https://github.com/jhugman/uniffi-bindgen-react-native/pull/438).** Fixed the same class of fault in the TypeScript generator, found while generating bindings that produced a 12,000-line TypeScript file.
- **[PyPSA-Eur, European energy system model](https://github.com/PyPSA/pypsa-eur/pull/2414).** Fixed a constraint that meant flexible geothermal reservoirs never got any capacity, closing [#2413](https://github.com/PyPSA/pypsa-eur/issues/2413). Reported a second fault in the same code, [#2415](https://github.com/PyPSA/pypsa-eur/issues/2415).

### Other projects

**[kite-mcp](https://github.com/ldocallaghan/kite-mcp)**

An unofficial MCP server that lets a language model run trade-policy scenarios in KITE, the open-source trade models of the Kiel Institute. Every number it returns has to match a direct KITE run exactly, and CI compares 17,394 of them on every commit. While testing it I found a fault in KITE's example data and reported it.

**[misclosure](https://github.com/ldocallaghan/misclosure)**

The checks from kite-mcp, made into a Python tool for any MCP server and any model. It compares every number a server returns with a direct run of the model, bit for bit unless a tolerance is declared with a reason. It also checks that each number in a language model's answer comes from a tool result. On PyPI as `misclosure`.

**[Langsammm](https://github.com/ldocallaghan/Langsammm)**

Plays music three semitones slower and lower. Slowing normally drags vocal resonance down with the pitch and singers sound slurred. Langsammm lifts the spectral envelope back where it started while leaving the pitch down.

The DSP is Rust compiled to WebAssembly, 40KB with no dependencies, and runs inside a Web Audio AudioWorklet. It takes a cepstral envelope of each frame and applies a per-bin real gain to the original spectrum, leaving the phases alone. Runs in Chrome and Firefox 128+, [published on addons.mozilla.org](https://addons.mozilla.org/en-US/firefox/addon/langsammm/).

**[vaultbench](https://github.com/ldocallaghan/vaultbench)**

Five embedded vector search engines at personal-knowledge-base scale, measured on latency, memory, disk and recall against exact ground truth, across 1k, 10k and 100k document sample sets.

A plain array scan beats two of the four indexed engines above 1,000 documents. One engine's default configuration returns half the expected recall, with nothing in the output to indicate it. At 100k chunks Qdrant Edge answers in 0.52ms and stays exact, where brute force takes 32.66ms.

**[portcall](https://github.com/ldocallaghan/portcall)**

Ran Prisma 7 through the same eleven steps on Node, Bun, Deno and Cloudflare `workerd`. All four returned byte-identical output, which stops being interesting once you notice they load the same WASM query compiler. Cloudflare Workers was the exception: its default client imports `node:process` at module scope, so that target needs a generator block of its own.
