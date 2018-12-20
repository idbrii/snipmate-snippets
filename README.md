Consistent UltiSnip Snippets
============================

[![Build Status](https://travis-ci.org/idbrii/vim-uniformsnippets.svg)](https://travis-ci.org/idbrii/vim-uniformsnippets)

This is a fork of honza/vim-snippets that focuses making snippet triggers
uniform across all languages.

**Current priority is making snippets consistent and not
backwards-compatibility.**

For snippets to be useful when switching languages, we should have the same
triggers for them:

```
if : if without else
ife: if $1 else $2
eif : else if ($1) { .. }
el  : else ..
wh  : while (cond) ...
sw  : switch (var) ...
fun : function/method
```

Contents
--------

- `UltiSnips/*`: snippets using UltiSnips format

Snippet engines supporting vim-uniformsnippets
----------------------------------------

vim-uniformsnippets provides snippets for [github.com/SirVer/ultisnips][1].

Vendor Snippets
---------------

Additional library and framework snippets are available for UltiSnips users in
the `UltiSnips/` directory. These files are removed from the default language
namespaces to prevent them from all being loaded automatically. If there is a
separate library, framework, or package you would like to support open a pull
request!

Additional snippets can be added to the current buffer with the
`:UltiSnipsAddFiletypes` command followed by the snippet name without the
"snippets" ending. For example, to add the JavaScript Jasmine snippets, run:
`:UltiSnipsAddFiletypes javascript-jasmine`. To have this snippet loaded
everytime a JavaScript file is opened or created you can add the command to your
 -`.vim/ftplugin/javascript.vim` file. Another way is to add
 `autocmd FileType js UltiSnipsAddFiletypes javascript-jasmine` in your `.vimrc`.


For more see the UltiSnips docs (`:help UltiSnips`).

Getting help
------------

If you still have trouble getting this to work, please create a GitHub issue.

Things to consider when contributing
------------------------------------

Avoid placeholder text that doesn't add value. Use `${VISUAL}` for any trigger
that might wrap other code.

Bad:
```
if (${1:condition}){
  ${0:some code here}
}
```

Good:
```
if (${1}) {
  ${2:${VISUAL}}
}
```

Function arguments and other hints make for good placeholder text (such as
Vim's `matchall()`, `matchstr()` functions which case hints may be helpful to
remember order).

For conditions (while, if ..) and block bodies just use ${N}.

No snippets for oneliners (if else endif on one line).

Open questions:
* Which policies can we encourage upstream?
 * Discuss at: https://github.com/honza/vim-snippets/issues/230

Currently all snippets from UltiSnips have been put into UltiSnips - some work
on merging should be done (dropping duplicates etc). Also see engines section above.

For new snippets, also try contributing to vim-snippets!

Related repositories
--------------------

We also encourage people to maintain sets of snippets for particular use cases
so that all users can benefit from them.  People can list their snippet repositories here:

* https://github.com/honza/vim-snippets (original snippet repository)
* https://github.com/rbonvall/snipmate-snippets-bib (snippets for BibTeX files)
* https://github.com/sudar/vim-arduino-snippets (snippets for Arduino files)
* https://github.com/zedr/zope-snipmate-bundle.git (snippets for Python, TAL and ZCML)
* https://github.com/bonsaiben/bootstrap-snippets (snippets for Twitter Bootstrap markup, in HTML and Haml)
* https://github.com/sniphpets (advanced snippets for PHP, Symfony 2/3, Doctrine and etc.)

Versions / dialects / ..
========================

Language maintainers
--------------------

The original vim-snippets has maintainers for different languages:

* Elixir - [lpil](https://github.com/lpil), [iurifq](https://github.com/iurifq)
* Falcon - [steveno](https://github.com/steveno)
* HTML Django - [honza](http://github.com/honza)
* Javascript - [honza](http://github.com/honza)
* Markdown - [honza](http://github.com/honza)
* PHP - [chrisyue](http://github.com/chrisyue)
* Python - [honza](http://github.com/honza)
* Ruby - [taq](http://github.com/taq)
* Scala - [gorodinskiy](https://github.com/gorodinskiy)
* Supercollider - [lpil](https://github.com/lpil)

License
-------

Just as the original snipMate plugin, all the snippets are licensed under the
terms of the MIT license.

[1]: http://github.com/SirVer/ultisnips
