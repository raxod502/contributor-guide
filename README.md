# Contributor guide

This repository has some handy instructions on contributing to my
open-source projects.

## Linters

Most of my projects include automated linters to improve code quality.
Run them locally with `make lint`. Typically this will do the
following:

* Check for no byte-compiler warnings.
* Run
  [Checkdoc](https://www.gnu.org/software/emacs/manual/html_node/elisp/Tips.html)
* Check for no lines longer than 79 characters. [Why
  79?](https://www.reddit.com/r/learnpython/comments/1h2eug/pep_8_why_is_the_character_limit_79_and_not_80/)
* Check that the code is indented correctly.
* Update the table of contents in the README. *Please install
  [markdown-toc](https://www.npmjs.com/package/markdown-toc) for this
  to work!*

The linters are run automatically against your pull request by
[CircleCI](https://circleci.com/). All pull requests must pass CI
before being merged.

One reason the CI can fail even though `make lint` worked for you is
that your code doesn't work in an older version of Emacs. CircleCI
runs the linters against every supported version of Emacs. You can do
the same by installing [Docker](https://www.docker.com/) and running
`make docker VERSION=25.3` (or equivalently for whatever version is of
interest). That will put you in a shell with the project source code
and all dependencies automatically installed in a sandbox.

## Documentation

We write documentation. Every symbol, public or private, needs a
docstring which is enough to fully understand the behavior without
inspecting the source code. Every public symbol (the ones without `--`
in their name) needs furthermore to be explained in the README.

## How to write a changelog

We also write changelogs. The changelog is kept in `CHANGELOG.md`.

The idea of the changelog is to document *user-visible* changes to the
project in a *user-readable* way (unlike the commit history, which is
much more detailed and hard to read).

Here is a changelog in progress:

```markdown
## Unreleased
### Enhancements
* In `read-file-name`, when a default is provided (for example in the
  `dired-do-rename` command), we actually use it as the initial
  contents of the minibuffer, which allows you to have convenient
  access to the default filename when that default file does not exist
  ([#25]).
* We now bind `minibuffer-completing-file-name` during
  `read-file-name`, in conformance with the standard Emacs interface
  ([#30]).

## Bugs fixed
* You can now use the undo system in the minibuffer. Previously,
  trying to do so would break Selectrum ([#31]).

[#25]: https://github.com/raxod502/selectrum/pull/25
[#30]: https://github.com/raxod502/selectrum/issues/30
[#31]: https://github.com/raxod502/selectrum/issues/31
```

Notice:

* There's a section called `Unreleased` where all the info goes. When
  I make a release, I relabel the section with the name of the release
  and copy it into the GitHub release. After the release, we add in a
  new `Unreleased` section at the top.
* We have sub-sections for the different types of changes. There
  aren't any strict rules about which sub-sections should be used, but
  here are some suggestions: `Breaking changes`, `Added`,
  `Enhancements`, `Deprecated`, `Removed`, `Bugs fixed`,
  `Performance`.
* Each change goes in a new bullet point, and includes a link to the
  relevant issue(s) or pull request(s) in parentheses. The link
  anchors go at the bottom of the `Unreleased` section, in
  alphabetical order.

**What to include in the changelog:** Any *user-visible* changes since
the last release. Changes to the implementation of an internal
function don't qualify, unless they fix a bug or improve performance
significantly. Also, if you fix a bug that was introduced since the
last release, there's no need to document that. The audience of a
changelog should be assumed to be running the last release.

**Example changelogs:**

* [Apheleia](https://github.com/raxod502/apheleia/blob/master/CHANGELOG.md)
* [Blackout](https://github.com/raxod502/blackout/blob/master/CHANGELOG.md)
* [CTRLF](https://github.com/raxod502/ctrlf/blob/master/CHANGELOG.md)
* [`diary-manager`](https://github.com/raxod502/diary-manager/blob/master/CHANGELOG.md)
* [`el-patch`](https://github.com/raxod502/el-patch/blob/master/CHANGELOG.md)
* [`prescient.el`](https://github.com/raxod502/prescient.el/blob/master/CHANGELOG.md)
* [Selectrum](https://github.com/raxod502/selectrum/blob/master/CHANGELOG.md)
