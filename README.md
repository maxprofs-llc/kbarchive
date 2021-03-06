---
layout: page
title: Microsoft KnowledgeBase Archive
permalink: /
---

{% comment %}

# Microsoft KnowledgeBase Archive

This is a static archive of Microsoft KnowledgeBase articles.

There is no search functionality yet, so you must browse by product.

See this [PCjs](https://www.pcjs.org) [blog post](https://www.pcjs.org/blog/2017/10/13/) on the
frustration that inspired this archive.

{% endcomment %}

## KB Articles by Product/Category

- [Internet Information Server](id/iis/)
- [Microsoft Access Distribution Kit](id/accother/)
- [Microsoft Automap](id/automap/)
- [Microsoft C Compiler](id/visualc/)
- [Microsoft Developer Network](id/msdn/)
- [Microsoft Disk Operating System](id/msdos/)
- [Microsoft Exchange](id/exchange/)
- [Microsoft Fortran Compiler](id/fortran/)
- [Microsoft Fox Miscellaneous Products](id/foxmisc/)
- [Microsoft FoxPro](id/foxpro/)
- [Microsoft Home Games](id/homegame/)
- [Microsoft Home Kids Products](id/homekids/)
- [Microsoft Home Miscellaneous Products](id/homemisc/)
- [Microsoft Home Multimedia Titles](id/homemm/)
- [Microsoft LAN Manager](id/lanman/)
- [Microsoft Macro Assembler](id/masm/)
- [Microsoft Mail For Appletalk Networks](id/macmail/)
- [Microsoft Mail For PC Networks](id/pcmail/)
- [Microsoft Mastering Series](id/mastering/)
- [Microsoft PowerPoint for Windows](id/powerpt/)
- [Microsoft Press](id/mspress/)
- [Microsoft Product Support Information](id/techinfo/)
- [Microsoft Programmer's Library 1.3: BASIC](id/mspl13_basic/)
- [Microsoft Programmer's Library 1.3: C](id/mspl13_c/)
- [Microsoft Programmer's Library 1.3: MASM](id/mspl13_masm/)
- [Microsoft Programming Utilities](id/utilities/)
- [Microsoft SNA Server](id/sna/)
- [Microsoft Schedule+ for Windows](id/schedplus/)
- [Microsoft SourceSafe](id/ssafe/)
- [Microsoft Systems Journal](id/msj/)
- [Microsoft Systems Management Server](id/sms/)
- [Microsoft Tips for the Macintosh System](id/macsys/)
- [Microsoft Visual Basic for Windows](id/vbwin/)
- [Microsoft Windows 3.x Retail Product](id/win3x/)
- [Microsoft Windows 95.x Retail Product](id/win95x/)
- [Microsoft Windows Device Driver Kit](id/win16ddk/)
- [Microsoft Windows NT](id/winnt/)
- [Microsoft Windows Printing Issues](id/winprint/)
- [Microsoft Windows Software Development Kit](id/win16sdk/)
- [Miscellaneous Software Development Kits](id/miscsdk/)
- [Miscellaneous Windows Products](id/winmisc/)
- [Open Database Connectivity (ODBC)](id/odbc/)
- [The Microsoft Network](id/msnetwork/)
- [Windows for Workgroups and Windows NT Networking Issues](id/crossnet/)
- [Word 97 for Windows](id/word97/)
- [Word Front Page](id/frontpg/)

{% comment %}

This repository was initially populated with KB content from Microsoft's FTP archive, circa 2002, courtesy
of [Michal Necasek](http://www.os2museum.com/wp/ms-kb-articles/), and then back-filled with KB articles from
other sources (eg, the Microsoft Programmer's Library CD-ROM, courtesy of
[neozeed](https://virtuallyfun.superglobalmegacorp.com/2012/07/05/2133/)).

It might have been useful to start with the oldest articles first, commit them to the repository, and then add
and commit successively newer batches of articles, thereby capturing the evolution of certain articles.  However,
the collection of KB articles is an on-going process, and older batches may not be discovered until after newer
batches have already been added.

All the original text files have been [converted](scripts/genmd.js) to Markdown files in preparation for
publishing via GitHub Pages.  The boilerplate legal notices have been removed from the Markdown files,
in part to save a little space, but they will be restored by the page template that's used to publish them.

A [log file](scripts/genmd.log) records the use of non-ASCII characters.  These haven't been examined yet,
so it's unclear if the files used CP-437, CP-1252, UTF-8, or some other character set.  In some cases, it might
simply be garbled data, or binary data that should have been translated to something readable.

{% endcomment %}
