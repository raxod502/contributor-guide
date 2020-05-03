# Contributor guide

This repository has some handy instructions on contributing to my
open-source projects.

## How to write a changelog

The idea of the CHANGELOG.md file is to document *user-visible*
changes to the project in a *user-readable* way (unlike the commit
history, which is much more detailed and hard to read).

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
