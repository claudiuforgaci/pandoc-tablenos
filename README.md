
pandoc-tablenos 0.7
===================

*pandoc-tablenos* is a [pandoc] filter for numbering tables and table references.

Demonstration: Processing [demo.md] with `pandoc --filter pandoc-tablenos` gives numbered tables and references in [pdf], [tex], [html], [epub], [md] and other formats.

This version of pandoc-tablenos was tested using pandoc 1.16.0.2 and 1.15.2, and should be compatible with earlier pandoc versions.  It is known to work under linux, Mac OS X and Windows.

Installation of the filter is straight-forward, with minimal dependencies.  It is simple to use and has been tested extensively.

See also: [pandoc-fignos], [pandoc-eqnos]

[pandoc]: http://pandoc.org/
[demo.md]: https://raw.githubusercontent.com/tomduck/pandoc-tablenos/master/demos/demo.md
[pdf]: https://raw.githubusercontent.com/tomduck/pandoc-tablenos/master/demos/out/demo.pdf
[tex]: https://raw.githubusercontent.com/tomduck/pandoc-tablenos/master/demos/out/demo.tex
[html]: https://rawgit.com/tomduck/pandoc-tablenos/master/demos/out/demo.html
[epub]: https://raw.githubusercontent.com/tomduck/pandoc-tablenos/master/demos/out/demo.epub
[md]: https://github.com/tomduck/pandoc-tablenos/blob/master/demos/out/demo.md
[pandoc-fignos]: https://github.com/tomduck/pandoc-fignos 
[pandoc-eqnos]: https://github.com/tomduck/pandoc-eqnos 


Contents
--------

 1. [Rationale](#rationale)
 2. [Markdown Syntax](#markdown-syntax)
 3. [Usage](#usage)
 4. [Details](#details)
 5. [Installation](#installation)
 6. [Getting Help](#getting-help)


Rationale
---------

Table numbers and references are required for academic writing, but are not currently supported by pandoc.  Pandoc-tablenos is an add-on filter that provides the missing functionality.

The markdown syntax recognized by pandoc-tablenos was worked out in [pandoc Issue #813] -- see [this post] by [@scaramouche1].  It seems likely that this will be close to what pandoc ultimately adopts.  Pandoc-tablenos is a transitional package for those who need table numbers and references now.

[pandoc Issue #813]: https://github.com/jgm/pandoc/issues/813
[this post]: https://github.com/jgm/pandoc/issues/813#issuecomment-70423503
[@scaramouche1]: https://github.com/scaramouche1


Markdown Syntax
---------------

To number a table, add the label `tbl:id` to the attributes of its caption:

    A B
    - -
    0 1

    Table: Caption. {#tbl:id}

The prefix `#tbl:` is required. `id` should be replaced with a unique identifier composed of letters, numbers, dashes, slashes and underscores.

To reference the table, use

    @tbl:id

or

    {@tbl:id}

Curly braces around a reference are stripped from the output.

See [demo.md] for an example.


Usage
-----

To apply the filter, use the following option with pandoc:

    --filter pandoc-tablenos

Note that any use of `--filter pandoc-citeproc` or `--bibliography=FILE` should come *after* the pandoc-tablenos filter call.


Details
-------

For tex/pdf output, LaTeX's native `\label` and `\ref` macros are used; for all others the numbers are hard-coded.

Links are constructed for html and pdf output.


Installation
------------

Pandoc-tablenos requires [python], a programming language that comes pre-installed on linux and Mac OS X, and which is easily installed [on Windows].  Either python 2.7 or 3.x will do.


### Standard installation ###

Install pandoc-tablenos as root using the shell command

    pip install pandoc-tablenos 

To upgrade to the most recent release, use

    pip install --upgrade pandoc-tablenos 

Pip is a script that downloads and installs modules from the Python Package Index, [PyPI].  It should come installed with your python distribution.


### Installing on linux ###

If you are running linux, pip may be bundled separately.  On Debian-based systems (including Ubuntu), you can install it as root using

    apt-get update
    apt-get install python-pip

During the install you may be asked to run

    easy_install -U setuptools

owing to the ancient version of setuptools that Debian provides.  The command should be executed as root.  The pip install process detailed above should now work.

[python]: https://www.python.org/
[on Windows]: https://www.python.org/downloads/windows/
[PyPI]: https://pypi.python.org/pypi


### Installing from source ###

You may also choose to install sources [downloaded from github].  Execute the following command as root in the top directory of your download:

    python setup.py install

[downloaded from github]: https://github.com/tomduck/pandoc-tablenos/archive/master.zip


Getting Help
------------

If you have any difficulties with pandoc-tablenos, please [file an issue] on github.

[file an issue]: https://github.com/tomduck/pandoc-tablenos/issues
