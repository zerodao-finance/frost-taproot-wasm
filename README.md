# frost-taproot-wasm

WASM bindings for [frost-taproot](https://github.com/zerodao-finance/frost-taproot).

## Build

Make sure you have `wasm-pack` installed.  It can be acquired with Cargo with
`cargo install wasm-pack`.

Then, it can be built with `wasm-pack build --target web` and the outputs will
be in `pkg/`, with a `package.json` to be used with NPM as normal, or used
directly.

Make sure not to use `cargo build`, or else you'll just compile it natively and
get a mystery `.so` with unknown secrets contained within.

## Test

The hard parts are more thoroughly tested in the `frost-taproot` repo.  Since
this repo is just bindings, we are taking an unconventional approach to testing.

* Build normally as above.
* In the `pkg/` output dir, run `python3 -m http.server`.
* Navigate to https://localhost:8000/test.html in your browser.
* Open the js console and you should see it run a few setups and print "OK".

This is lazy, but it shows that all the parts are working in WASM in a realistic
environment.

