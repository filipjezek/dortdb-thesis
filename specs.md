# Specification

- [ ] modular architecture - developer can include only the parts of the library he needs in order to improve bundle size

```ts
db = new CakeDB({
    lang: [
        SQL, EmbeddedJSON, XML // ...
    ]
});
```

- [ ] SQL queries
- [ ] SQL data modification
- [ ] Embedded JSON (Postgres style)
- [ ] XML (HTML tree) queries
- [ ] AST should be exposed and documented (this way more plugins can be eventually written)
- [ ] when it makes sense, use webassembly to improve speed
- [ ] allow definition of indices over data (there was an in memory db index which uses SIMD in the literature)
- [ ] transactions? Not really about concurrency (js is single-threaded), although that happen using async/await, more about atomicity / data consistency