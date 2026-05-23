# llrepr

**Typed Representation IR for LLM output — "LLVM-for-expression."**

llrepr lets an LLM emit its output **once** as a typed node tree, then render it to many targets — Markdown (the always-safe degrade floor), SVG (web / articles), TUI (terminal), manga panels, and more. One IR, many backends: adding a renderer never touches the producer.

llrepr is part of the **FullSense** ecosystem (llmesh / llive / llove) — it is the *expression layer*: a typed representation contract that travels over MCP as standard `structuredContent`, with a Markdown degrade co-located in a `text` block so non-aware clients never break.

## Design
- **glTF-style extensions** — a small closed core node set (text / heading / list / table / code_block / figure / panel / container) plus `extensionsUsed` / `extensionsRequired`. Consumers fail-closed on unmet *required* extensions; unknown optional ones degrade gracefully.
- **MCP-native, no custom content type** — rides standard `structuredContent` + Markdown degrade, so generic MCP routers (e.g. llama.cpp) don't break.
- **Local-first / provenance-clean** — built for FullSense's on-prem philosophy.

## Status
Early proof-of-concept. The reference implementation currently lives in **llmesh** as the `llmesh.llrepr` package; this repository reserves the name and documents the concept. Standalone extraction will follow if/when llrepr graduates to a first-class layer.

## License
Apache-2.0 + Commercial (dual-license), consistent with the FullSense family.
