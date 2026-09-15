# SetrixDB

**The arithmetic set engine** — exact membership and intersection over `uint64` IDs, in
microseconds, with no payloads, no joins and no vector search.

SetrixDB is an **in-memory, purely arithmetic engine** written in **Go**, designed to sit
**beside** your database (relational, columnar, KV or vector) as a fast **index / pre-filter**:
it stores **sets of IDs** and answers *"is this ID in the set?"* and *"which IDs are in both
sets?"* with vectorized (SIMD/AVX-512) arithmetic.

- **Main engine:** [setrixdb/setrixdb](https://github.com/setrixdb/setrixdb) — Apache-2.0
- **Docs & benchmarks:** [docs/](https://github.com/setrixdb/setrixdb/tree/main/docs)
- **Website:** https://setrixdb.com
- **Write-up (the real numbers, and where it loses):** https://dev.to/tgosoul/setrixdb-a-set-engine-in-go-exact-set-intersection-over-ids-and-where-it-loses-39dm
- **Contact:** contato@setrixdb.com

## What's inside

- Dense / sparse / **hybrid** bitsets
- **MPHF (CHD v2)** keygen — unique, dense IDs, 0 collisions
- **AVX-512** AND+popcount kernel with runtime dispatch (portable scalar fallback)
- Sharding and a small **cluster** mode (consistent hash ring, zero-copy binary protocol)
- CLI, HTTP/JSON server, C ABI (FFI) and a public Go API

## Honest scope

SetrixDB is an **engine / set index** — it stores **sets of IDs**, not payloads. It **loses** to
Roaring on huge sparse universes, does not do range/similarity queries, and rebuilds the MPHF on
frequent updates. See the README's *"where it loses"* section.

## Contributing

Start with the issues labeled
[`good first issue`](https://github.com/setrixdb/setrixdb/labels/good%20first%20issue).
See [CONTRIBUTING.md](https://github.com/setrixdb/setrixdb/blob/main/CONTRIBUTING.md).
