Zotelo help you efficiently keep local bibliographic databases (.bib
files etc) up to date with the contents of your
[Zotero](http://www.zotero.org) collections.

Zotelo can be used in conjunction with any emacs mode and is
particularly useful when writing latex documents. It is useful for
`LaTeX`/`BibTeX` authoring, in conjunction with
[RefTeX](http://staff.science.uva.nl/~dominik/Tools/reftex/reftex-nutshell.html),
and works well with org-mode using [org-ref](https://github.com/jkitchin/org-ref).


Installation
============

Install `zotelo` from [Melpa](https://melpa.org/) or put [zotelo.el](https://raw.github.com/vitoshka/zotelo/master/zotelo.el) into your emacs path.

Install the [Better
Bibtex](https://github.com/retorquere/zotero-better-bibtex) add-on for Zotero.


Activate `zotelo-minor-mode` in `LaTeX` mode:

```lisp
(add-hook 'TeX-mode-hook 'zotelo-minor-mode)
```

Similarly you can activate `zotelo` in org mode if you use it to draft your LaTeX papers.

Usage
=====

_*Key-map*_
```
C-c z u         zotelo-update-database
C-c z e         zotelo-export-secondary
C-c z c         zotelo-set-collection (also "C-c z s")
C-c z s         zotelo-set-collection
```

In order to export a zotero collection you need first to associate it with the
current buffer with `C-c z c` (`zotelo-set-collection`). Select `*ALL*` to
export the whole Zotero library.

Zotelo uses [IDO](http://www.emacswiki.org/emacs/InteractivelyDoThings ) interface for the collection selection:

![set_collection](https://github.com/vitoshka/zotelo/raw/master/img/set_collection.png)

![zotero_collection](https://github.com/vitoshka/zotelo/raw/master/img/zotero_collection.png)

After modifying your zotero collection from the zotero interface, update the the
local database file with `C-c z u` (`zotelo-update-database`).

Exported File Names
-------------------

If the current file contains any of the following bibliography declarations:

```tex
\bibliography{file1, file2, ...}
\zotelo{file1, file2, ...}
\nobibliography{file1, file2, ...}
```

`zotelo` exports the associated Zotero collection as a `file1.xxx` file,
otherwise it exports into `[current-file-name].xxx`.


Multiple Databases and Collections
----------------------------------

You can list several files in `\thebibliography{...}` list. The first file is the primary database which you set with `C-c z s` and update with `C-c z u`. All others are secondary databases. 

Usually one database is enough, but for some projects you might want to
use several zotero collections. Use `zotelo-export-secondary` (bound to
`C-c z e`) to export any zotero collection into one of the secondary
files.  You will be asked to select a file and a collection to export.
This way you can have as many databases and zotero collections as you
want. 

Configuring the bib(la)tex output
---------------------------------

Better Bibtex a large amount of customisation in how exactly the
contents of Zotero collections are exported. It includes options for
exporting as bibtex or biblatex, as well as configuration of the format
of citation keys. Configuration can be done in the Better Bibtex options
within Zotero; see
[customised
exports](https://github.com/retorquere/zotero-better-bibtex/wiki/Customized-Exports)
on the wiki.

