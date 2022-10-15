# cljfmt-graalvm

> **Note**
>
> This fork and enhancement for [bsless/cljfmt-graalvm](https://github.com/bsless/cljfmt-graalvm)
> is because that repo is archived as of 2022-10-17

This is a re-packaging of `weavejester/cljfmt` as a fast-starting, native CLI tool.

[cljfmt](https://github.com/weavejester/cljfmt) is a tool for formatting Clojure code idiomatically.

Code vendored from `weavejester/cljfmt` or from `clojure.stacktrace` was to type
hint class types the native image could not figure out.

The compile script is based on
[clj-kondo's](https://github.com/borkdude/clj-kondo/blob/master/script/compile)

All credit goes to Weavejester (James Reeves, cljfmt) and Borkdude
(Michiel Borkent, clj-kondo) Stuart Sierra (stacktrace) and their
respective contributors.

## Prerequisites

- Get [GraalVM](https://github.com/graalvm/graalvm-ce-builds/releases)
- Set `GRAALVM_HOME` to the unpacked archive or add `$GRAALVM_HOME/bin` to your path
- Clone this repo

## Installation

- run `script/compile`
- copy `target/cljfmt` to someplace in your `$PATH`

## Usage

- drop-in replacement for the deprecated [node-cljfmt](https://github.com/snoe/node-cljfmt),
  reading `*in*` and writing formatted clojure code to `*out*`.  This is the interface
  used by [format-all for Emacs](https://github.com/lassik/emacs-format-all-the-code).
    - `stdio`

- also replicates the options of the original [cljfmt](https://github.com/weavejester/cljfmt) lein task.
    - `fix`
    - `check`

### Emacs

If you are using [doom emacs](https://github.com/doomemacs), add this to your `~/.doom.d/config.el`.

```emacs
(set-formatter! 'cljfmt "cljfmt stdio")
```

As of 2023-01-03, Doom emacs has its format module [pinned to `format-all` 0.5.0](https://github.com/doomemacs/doomemacs/blob/master/modules/editor/format/packages.el).
If you are using a later version of `format-all`, use [zprint](https://github.com/kkinnear/zprint) or set `zprint`.

```emacs
(set-formatter! 'zprint "cljfmt stdio")
```

[zprint](https://github.com/kkinnear/zprint) is an alternative to [cljfmt](https://github.com/weavejester/cljfmt).

## Options

Just like [`lein cljfmt`](https://github.com/weavejester/cljfmt#configuration)

```
--file-pattern FILE_PATTERN            \.clj[csx]?$
--indents INDENTS_PATH
--alias-map ALIAS_MAP_PATH
--project-root PROJECT_ROOT            .
--[no-]ansi
--[no-]indentation
--[no-]remove-surrounding-whitespace
--[no-]remove-trailing-whitespace
--[no-]insert-missing-whitespace
--[no-]remove-consecutive-blank-lines
```

## License

Copyright © 2022 Paul Bauer

Copyright © 2020 Ben Sless

This program and the accompanying materials are made available under the
terms of the Eclipse Public License 2.0 which is available at
http://www.eclipse.org/legal/epl-2.0.

This Source Code may also be made available under the following Secondary
Licenses when the conditions for such availability set forth in the Eclipse
Public License, v. 2.0 are satisfied: GNU General Public License as published by
the Free Software Foundation, either version 2 of the License, or (at your
option) any later version, with the GNU Classpath Exception which is available
at https://www.gnu.org/software/classpath/license.html.
