

Localization
============


kupfer is translated using gettext and it is managed in the build system
using ``intltool``. Translation messages are located in the ``po/``
directory.

Kupfer's localizations are listed among GNOME's modules. Its homepage
is:

    http://l10n.gnome.org/module/kupfer/

You can download the latest version of your language's translation file
there, if Kupfer is already translated to your language.

.. contents::

To create a new translation
---------------------------

Go into the directory ``po``

1. Add the language code ``$LANG`` to the file ``LINGUAS``
2. Run ``intltool-update --pot``, and copy ``untitled.pot`` to ``$LANG.po``
3. Edit and check the whole file header: 

   + Write in yourself as author
   + Check ``plurals`` (copy from a language that you know uses the same
     number of plural forms, or look up in GNOME's translation pages.)
   + Replace everything written in CAPS

Fill in the charset used; Kupfer translations *must* use the UTF-8 encoding.

When the header is filled-in, go to `To update or check an existing
translation`_


To update or check an existing translation
------------------------------------------

Go to your Kupfer source directory.

Here we will call your language ``$LANG``. You should use a two or
four-letter code for your language instead of ``$LANG``, for example
"de" for German or "pt_BR" for Brazilian Portuguese.

Go to the translation directory ``po``::

    cd po/

To update and check the translation file, run::

    intltool-update $LANG

Now check and edit ``$LANG.po``. Search for all messages marked "fuzzy",
and remove the word "fuzzy" from them when they are done.

Continue running ``intltool-update $LANG`` and check that you have 0
fuzzy and 0 untranslated, then you're finished.

This will also check consistency of the file, so that you know that all
your syntax is correct.

If you want to send in the translation to a repository, or as a patch,
you can use git if you have a checked-out copy of kupfer::

    git add po/$LANG.po
    git commit -m "$LANG: Updated translation"

    # now we create a patch out of the latest change
    git format-patch HEAD^

You can send the patch, or the whole file, to the mailing list
kupfer-list@gnome.org.

To try the new translation
--------------------------

Make sure the translation is listed in ``po/LINGUAS``.

To try it, you have to install kupfer with ``./waf install``, then you
can run kupfer as normal.

.. note::

    If you run ``./kupfer-run`` from the source directory it won't
    find the installed translations unless you make a symlink called
    ``locale`` to the installed location (for example
    ``~/.local/share/locale`` if install prefix was ``~/.local``)::

        $ ln -s ~/.local/share/locale

.. vim: ft=rst tw=72 et sts=4
.. this document best viewed with rst2html
