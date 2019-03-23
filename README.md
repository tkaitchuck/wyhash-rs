# wyhash fast portable non-cryptographic hashing algorithm

[![crates.io](https://img.shields.io/crates/v/wyhash.svg)](https://crates.io/crates/wyhash)
[![Docs](https://docs.rs/wyhash/badge.svg)](https://docs.rs/wyhash)
[![Build Status](https://travis-ci.org/eldruin/wyhash-rs.svg?branch=master)](https://travis-ci.org/eldruin/wyhash-rs)
[![Coverage Status](https://coveralls.io/repos/github/eldruin/wyhash-rs/badge.svg?branch=master)](https://coveralls.io/github/eldruin/wyhash-rs?branch=master)
![Maintenance Intention](https://img.shields.io/badge/maintenance-actively--developed-brightgreen.svg)

Rust implementation of the [wyhash algorithm by Wang Yi][original].

The hashing algorithm passes SMHasher and the random number generator passes BigCrush and practrand.
As of now it is the fastest algorithm in the SMHasher benchmark (faster than t1ha and XXH3).
See [here][original].

Furthermore, this algorithm is solid, simple, portable (does not need hardware support, can be
used in `no_std` environments) and has no dependencies.

The generated hashes are equal (see tests) as of the version stated [here][original-version]
although the speed varies ([PRs are welcome][issue-tracker]).

### Usage

```rust
extern crate wyhash;
use wyhash::WyHash;
use std::hash::Hasher;

fn main() {
  let mut hasher = WyHash::with_seed(3);
  hasher.write(&[0, 1, 2]);
  assert_eq!(0xcc24_2106_e707_6a48, hasher.finish());
}
```

## Support

For questions, issues, feature requests, and other changes, please file an
[issue in the github project][issue-tracker].

## License

Licensed under

 * Apache License, Version 2.0 ([LICENSE-APACHE](LICENSE-APACHE) or
   http://www.apache.org/licenses/LICENSE-2.0)

### Contributing

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in the work by you, as defined in the Apache-2.0 license, shall
be licensed as above, without any additional terms or conditions.

[issue-tracker]: https://github.com/eldruin/wyhash-rs/issues
[original]: https://github.com/wangyi-fudan/wyhash
[original-version]: https://github.com/eldruin/wyhash-rs/blob/master/original/CMakeLists.txt
