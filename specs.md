# Specification

- [ ] modular architecture - developer can include only the parts of the library he needs in order to improve bundle size, also allow user extensions

```ts
db = new DortDB({
    lang: [
        SQL, EmbeddedJSON, XML // ...
    ]
});
```
  - languages will be separate bison grammars, can be combined using `SYNTAX` blocks like so:
```
SELECT * FROM (
  SYNTAX SPARQL
  ...
)
```
  - languages themselves will not be easily modifiable - I have found no way to extend existing grammars from outside. This means no configs like this:

```ts
db = new DortDB({
    lang: [
        new SQL(Queries, Modifications, WithStatements)
    ]
});
```
  - it might however be possible to specify SQL grammar as a whole - either by creating a new language, or using config like this (which would mean creating precompiled parser for each level):
```ts
db = new DortDB({
    lang: [
        new SQL({level: QueriesOnly})
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