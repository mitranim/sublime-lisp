## Overview

An immature sketch of various Lisp syntaxes for Sublime Text. The syntax files **require Sublime Text 4** and will **not** work properly in earlier versions.

## Multiple Syntaxes and Inheritance

Unlike most syntax packages, this has multiple dialects, using [inheritance](https://www.sublimetext.com/docs/syntax.html):

* Lisp: base syntax.
* Common Lisp: inherits from Lisp.
* Scheme: inherits from Lisp.

The base syntax doesn't support _any_ special forms or functions, but does support some additional punctuation such as `[]` and `{}` for fringe dialects. It's intended for:

* Dialects that are neither Common Lisp nor Scheme.
* Creating new syntaxes by inheriting from the Lisp syntax.

See [#Customization](#customization) below.

## Features and Limitations

Current features:

* Basic AST structure: comments, atoms (symbols, strings, numbers), punctuation (parens, brackets, braces, quotes, dotted pair).
* Common Lisp: limited support for common declaration forms, to support ST symbol search and `goto_definition`.
* Scheme: limited support for common declaration forms, to support ST symbol search and `goto_definition`.

Current limitations:

* No automatic syntax tests.
* No support for editing experience (auto-indent etc.).
* No rational numbers.
* No exponents with scientific notation.
* No non-decimal numbers.
* No piped symbols.
* Incomplete support for characters.
* Incomplete support for string and character escape sequences.
* Numbers are considered symbols in some contexts, e.g. `(define 10 20)`.
* No attempt to scope function calls. In most dialects it would produce too many false positives.
* No attempt to scope "well-known" functions and special forms, other than declarations (`define` and such). This could be rectified on demand.
* Incomplete and immature support for definition forms, with many false negatives and positives.
* No support for variable-binding forms.
* No support for string format directives.
* ... more.

## Installation

Clone the repo and symlink it to your Sublime packages directory. Example for MacOS:

```sh
git clone https://github.com/mitranim/sublime-lisp.git
cd sublime-lisp
ln -sf "$(pwd)" "$HOME/Library/Application Support/Sublime Text/Packages/"
```

To find the packages directory on your system, use Sublime Text menu → Preferences → Browse Packages.

To avoid conflicts and confusion, disable the Lisp package built into ST.

## Customization

Lisp has many dialects and encourages further extension. It's very useful to customize the editor syntax support, to better suit your particular dialect or codebase. The best way is to create your own syntax files that **inherit** from the syntaxes provided by this package, and override their contexts.

To learn about syntax inheritance, read the official docs: https://www.sublimetext.com/docs/syntax.html.

Use the Common Lisp and Scheme files as examples.

## License

https://unlicense.org
