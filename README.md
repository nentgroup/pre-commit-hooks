# pre-commit-hooks

Reads hooks metadata from Cargo.toml and executes on commit. A forked from unmaintained [pre-commit](https://github.com/rustation/pre-commit).



### Installing

```
[dependencies]
pre-commit = "0.1.0"
```

### Usage

Add a table like the following to your root `Cargo.toml`.

```
[package.metadata.precommit]
fmt = "cargo fmt -- --write-mode diff 2>&1"
test = "cargo test 2>&1"
```

Or, if you're ussing workspace:
```
[workspace.metadata.precommit]
fmt = "cargo fmt -- --write-mode diff 2>&1"
sort = "cargo sort -w"
```

Then run:

```
$ cargo clean
$ cargo build
```

You should now have a `pre-commit` file in your `./git/hooks` that will run the listed pre-commit entries.
