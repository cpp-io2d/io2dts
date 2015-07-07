==========================
IO2D Technical Specification Draft Sources
==========================

These are the sources used to generate drafts of the working paper for a proposal for an IO2D TS. These sources should not be considered an ISO publication,
nor should documents generated from them unless officially adopted by
the C++ working group (ISO/IEC JTC1/SC22/WG21).

More information about the C++ standard can be found at `isocpp.org <http://isocpp.org/std>`_.

--------------------------
Getting Started on Windows
--------------------------

1. Install a Perl distribution. Strawberry Perl is free and simple to install. (This ensures that latexmk will work correctly).
2. Install MiKTeX.
3. Install TeXstudio.
4. Run TeXstudio.
5. In TeXstudio, under "Options" -> "Configure TeXstudio...", first make sure the "Show Advanced Option" box is checked, then select "Build" from the menu on the left of the "Configure TeXstudio" window and then under the "Meta Commands" section, change the "Default Compiler" to "txs:///latexmk" using the drop down menu.

You are now ready to edit and build TeX documents.

When working with a multi-document project, open up or switch to the main project document in TeXstudio, e.g. io2d.tex, then from the "Options" menu, select the "Define Current Document as 'Master Document'" option. This will allow you to compile the project without switching back to that main document. If you don't do that, then TeXstudio will try to compile whichever .tex document you are currently editing as though it were the main document (resulting in errors (unless you happen to be editing the actual main document)).

---------------------------
Getting Started on Mac OS X
---------------------------

Install the `MacTeX distribution <http://tug.org/mactex/>`_.

If you are on a slow network, you'll want to get the `BasicTeX package <http://tug.org/mactex/morepackages.html>`_ instead,
then run the following command to install the other packages that the draft requires:

   sudo tlmgr install latexmk isodate substr relsize ulem fixme rsfs

------------
Instructions
------------

To typeset the draft document, from the ``source`` directory:

#. run ``latexmk -pdf io2d``

That's it! You should now have an ``io2d.pdf`` containing the typeset draft.

Alternative instructions
========================

If you can't use latexmk for some reason, you can use the Makefiles instead:

#. run ``make rebuild``
#. run ``make reindex``

If you can't use latexmk or make for some reason, you can run LaTeX manually instead:

#. run ``pdflatex io2d`` until there are no more changed labels or changed tables
#. run ``makeindex generalindex``
#. run ``makeindex libraryindex``
#. run ``makeindex impldefindex``
#. run ``pdflatex io2d`` twice more.

Generated input files
=====================

To regenerate figures from .dot files, run::

   dot -o<pdfname> -Tpdf <dotfilename>

For example::

   dot -ofigstreampos.pdf -Tpdf figstreampos.dot

To regenerate the grammar appendix, run the following from the source
directory::

   ../tools/makegram

To regenerate the cross-references appendix, run the following from
the source directory::

   ../tools/makexref

----------------
Acknowledgements
----------------

A great deal of gratitude goes out to Pete Becker for his amazing work
in the original conversion of the C++ standard drafts to LaTeX, and
his subsequent maintenance of the standard drafts up to C++11. Thank
you Pete.

Thanks to Walter Brown for suggesting the use of ``latexmk``.

Thanks to the above-mentioned folks for their hard work creating the
`C++ Standard Draft Sources <https://github.com/cplusplus/draft>`_,
from which this borrows heavily.