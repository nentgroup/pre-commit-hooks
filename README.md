# pre-commit-hooks

Reads hooks metadata from Cargo.toml and executes on commit. A forked from unmaintained [pre-commit](https://github.com/rustation/pre-commit).


### Installing

```
[dependencies]
pre-commit-hooks = "0.1"
```

For a workspace-based setup, one only need to add it in one of the package dependency, usually the main package (if any). This is because the pre-commit applies to the whole project.

### Usage

Add a table like the following to your root `Cargo.toml`:

```
[package.metadata.precommit]
fmt = "cargo fmt"
sort = "cargo sort"
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
