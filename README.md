# radeco-lib

[![Build Status](https://travis-ci.org/radare/radeco-lib.svg?branch=master)](https://travis-ci.org/radare/radeco-lib)
[![Coverage Status](https://coveralls.io/repos/github/radare/radeco-lib/badge.svg?branch=master)](https://coveralls.io/github/radare/radeco-lib?branch=master)

A radare2 based binary analysis framework


### Is this ready yet?

Nope. There is still a ton of work to do before this can be considered ready.
That said, parts of the library are already stable enough to write your own
analysis passes and use in your projects.


## Usage

Build like a regular rust project, using cargo:

`cargo build`

To include in your rust project, add to Cargo.toml:

```
[dependencies.radeco-lib]
git = "https://github.com/radare/radeco-lib"
```

See examples for usage.

## Development

Additional features to build with to help development.

### Trace Log

To debug, you may want to enable trace output from various parts of radeco.
Build with `trace_log` feature to enable this:

`cargo build --features 'trace_log'`


### Profiling

Requires [gperftools ](https://github.com/gperftools/gperftools). Check the
[cpuprofiler](https://github.com/AtheMathmo/cpuprofiler) repository for more details.

To enable profiling, build with `profile` feature:

`cargo build --features 'profiler'`

Wrap the code you want to profile with:

```rust
use cpuprofiler::PROFILER;

PROFILER.lock().unwrap().start("./my-prof.profile").unwrap();
// Code you want to sample goes here!
PROFILER.lock().unwrap().stop().unwrap();
```


## License
Licensed under The BSD 3-Clause License. Please check [COPYING](https://github.com/radare/radeco-lib/blob/master/COPYING) file for
complete license.
