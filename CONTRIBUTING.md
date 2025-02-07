# Contributing to `eztd`

Thanks for wanting to contribute! There are many ways to contribute and we
appreciate any level you're willing to do.

## Feature Requests

Need some new functionality to help?  You can let us know by opening an
[issue][new issue]. It's helpful to look through [all issues][all issues] in
case its already being talked about.

## Bug Reports

Please let us know about what problems you run into, whether in behavior or
ergonomics of API.  You can do this by opening an [issue][new issue]. It's
helpful to look through [all issues][all issues] in case its already being
talked about.

## Pull Requests

Looking for an idea? Check our [issues][issues]. If it's look more open ended,
it is probably best to post on the issue how you are thinking of resolving the
issue so you can get feedback early in the process. We want you to be
successful and it can be discouraging to find out a lot of re-work is needed.

Already have an idea?  It might be good to first [create an issue][new issue]
to propose it so we can make sure we are aligned and lower the risk of having
to re-work some of it and the discouragement that goes along with that.

### Design Guidelines

- Minimize interaction with the lifetimes, including:
  - Inherent functions take `&self` (or `&mut self` for mutable types)
  - Functions return owned types
- Maintain interop when wrapping types that are "vocab terms" in Rust, including:
  - Function parameters accept a wide variety of types (e.g. `impl AsRef<str>` rather than `eztd::String`)
  - Types have functions to/from the wrapped type, in a separate "Interop" section
- Leverage Python muscle memory by including ports of Python functions on types with Python analogs:
  - **This is an ideal, not a blocker, for contributions**
  - Marked as deprecated, describing the idiomatic Rust approach
  - In a separate "transitional Python" section
  - These do not need extensive documentation
- Be mindful of build times
  - Leverage features to keep things paired down
  - It is considered a bug against `ezstd` to depend on multiple versions of a dependency
    - **This is an ideal, not a blocker, for contributions**
- Easy feature opt-in
  - Major functionality exists in separate crates with the name `ez-<role>`
  - `eztd` pulls in those crates as module `<role>` with non-default features named `<role>`
  - module `<role>`'s documentation will be inlined for easier browsing
  - Purpose:
    - Balance batteries-included with compile time
    - Make it easier to track semver breaking changes

### Process

When you first post a PR, we request that the commit history get cleaned
up.  We recommend avoiding this during the PR to make it easier to review how
feedback was handled. Once the commit is ready, we'll ask you to clean up the
commit history.  Once you let us know this is done, we can move forward with
merging!  If you are uncomfortable with these parts of git, let us know and we
can help.

We ask that all new files have the copyright header.  Please update the
copyright year for files you are modifying.

As a heads up, we'll be running your PR through the following gauntlet:
- warnings turned to compile errors
- `cargo test`
- `rustfmt`
- `clippy`
- `rustdoc`

Check out our [CI][travis] for more information.

[issues]: https://github.com/epage/eztd/issues
[new issue]: https://github.com/epage/eztd/issues/new
[all issues]: https://github.com/epage/eztd/issues?utf8=%E2%9C%93&q=is%3Aissue
[travis]: https://github.com/epage/eztd/blob/master/.travis.yml
