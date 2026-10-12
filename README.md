### Liam O'Callaghan

Software engineer in Berlin. Most of my recent work is on language bindings and numerical models.

### Open source, 2026

- **[Mozilla, UniFFI bindings generator](https://github.com/mozilla/uniffi-rs/pull/2966).** UniFFI generates the bindings that let Firefox ship one Rust codebase to both Android and iOS. Fixed a code generation fault in the Kotlin and Swift backends that emitted source which would not compile, closing [an issue open since January 2025](https://github.com/mozilla/uniffi-rs/issues/2411).
- **[Qdrant, core repo](https://github.com/qdrant/qdrant/pull/10209).** A vector database with 34,000 stars, run as infrastructure under AI search and retrieval products. Fixed a build failure that stopped the project compiling at all on RISC-V, s390x and WebAssembly.
- **[uniffi-bindgen-react-native](https://github.com/jhugman/uniffi-bindgen-react-native/pull/438).** UniFFI carried to TypeScript for React Native, Node and the browser, funded by Mozilla, LiveKit and Filament. Fixed the same class of fault in the TypeScript generator, found while generating bindings that produced a 12,000-line TypeScript file.
- **[Prisma, documentation site](https://github.com/prisma/web).** Their Cloudflare deployment guide had regressed to a deprecated setting during a documentation migration. Traced it to the commit that lost the original fix and restored it.
- **[Qdrant Edge, Node.js bindings](https://github.com/qdrant/qdrant/issues/10226).** Built and demonstrated end to end: shard creation, write, read, close, and reopen from disk. Awaiting a decision from the maintainers on which language bindings belong in the core repository.

### Projects

**[BoreTHM](https://github.com/ldocallaghan/BoreTHM)**

Coupled physical models in Python that test one approach to drilling geothermal wells into superhot rock (400 °C and above). Cold fluid is pumped down an insulated pipe to the bit, where it keeps the tools below their survival limit and quenches the rock face, and returns up the annulus. Water properties come from IAPWS-95, and the models are one-dimensional or axisymmetric and mostly steady-state.

The borehole-stability model is calibrated against the breakouts logged in the UD-1 well at United Downs and checked against the GPK wells at Soultz-sous-Forêts, where it places the onset of breakouts within a few hundred metres of the logs. At both sites a 400 °C hole holds with drilling fluid barely heavier than water, but only because the circulating fluid cools the wall. Without that cooling, the weight needed comes within 3% of the fracture limit. A single closed loop at Soultz recovers around 4 MW of heat, returning at 137 °C, so the cold loop answers the drilling problem and leaves production as the open question.

**[Langsammm](https://github.com/ldocallaghan/Langsammm)**

Plays music three semitones slower and lower, then puts the voices back. Slowing normally drags vocal resonance down with the pitch and singers sound slurred. Lifts the spectral envelope back where it started while leaving the pitch down.

The DSP is Rust compiled to WebAssembly, 40KB with no dependencies, and runs inside a Web Audio AudioWorklet. It takes a cepstral envelope of each frame and applies a per-bin real gain to the original spectrum, leaving the phases alone. Ships for Chrome and Firefox 128+, [published on addons.mozilla.org](https://addons.mozilla.org/en-US/firefox/addon/langsammm/).

**[vaultbench](https://github.com/ldocallaghan/vaultbench)**

Five embedded vector search engines at personal-knowledge-base scale, measured on latency, memory, disk and recall against exact ground truth, across 1k, 10k and 100k document sample sets.

A plain array scan beats two of the four indexed engines above 1,000 documents. One engine's default configuration returns half the expected recall, with nothing in the output to indicate it. At 100k chunks Qdrant Edge answers in 0.52ms and stays exact, where brute force takes 32.66ms.

**[portcall](https://github.com/ldocallaghan/portcall)**

Ran Prisma 7 through the same eleven steps on Node, Bun, Deno and Cloudflare `workerd`. All four returned byte-identical output, which stops being interesting once you notice they load the same WASM query compiler. Cloudflare Workers was the exception: its default client imports `node:process` at module scope, so that target needs a generator block of its own.
