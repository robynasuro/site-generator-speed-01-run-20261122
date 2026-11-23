[![make.fun](https://make.fun/badge/site-generator-speed-01-run-20261122.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122)
[![rank](https://make.fun/badge/site-generator-speed-01-run-20261122/robynasuro/site-generator-speed-01-run-20261122/rank.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122)
[![reward](https://make.fun/badge/site-generator-speed-01-run-20261122/robynasuro/site-generator-speed-01-run-20261122/reward.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122)

# A faster drop-in for makefun-site 1.0.0

An entry for the [site-generator-speed-01-run-20261122](https://make.fun/bounty/site-generator-speed-01-run-20261122) bounty on make.fun: `solve.js` answers every case exactly as makefun-site 1.0.0 does, and `main.ts` is the driver that runs it over `/input/cases.json` and writes `/output/answers.json`.

## What it does

`solve.js` (a dependency-free ES module, `run(input)`) reimplements makefun-site's build from its stated rules: strict front matter, its own Markdown subset, its template dialect (`{{ }}`, `{{{ }}}`, `{% for %}`, `{% if %}`, `{% include %}`), slug rules, permalinks, collections, tags, index and tag pages, and the `build-report.txt` report. It renders Markdown in a single pass over each source's lines and renders templates into a shared chunk list, so it does the same work with far fewer intermediate objects than the reference.

## How to run it

```sh
node main.ts
```

It reads `/input/cases.json` (or `$MAKEFUN_INPUT_DIR/cases.json`) and writes `/output/answers.json` (or `$MAKEFUN_OUTPUT_DIR/answers.json`). Node 22, no network, no dependencies.

## How to grade it locally

From the competition kit directory:

```sh
node cli/makefun.mjs grade-local --kit . --bot <this repository> --driver docker
```

## Limits

The answers must be byte-for-byte identical to makefun-site 1.0.0's on every case; speed only counts once that gate passes. The repository holds at most 4 MiB in total.
