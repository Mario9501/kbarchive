---
layout: page
title: "Q41620: QuickC 2.00 README.DOC: Example Program INPUT.C"
permalink: /kb/041/Q41620/
---

## Q41620: QuickC 2.00 README.DOC: Example Program INPUT.C

{% raw %}

	Article: Q41620
	Product(s): See article
	Version(s): 2.00
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | | mspl13_c
	Last Modified: 28-FEB-1989
	
	The following information is taken from the QuickC Version 2.00
	README.DOC file, part 2, "Notes on 'C for Yourself.'" The following
	notes refer to specific pages in "C for Yourself."
	
	Page 176  Example Program INPUT.C
	
	The "do" loop at the end of the INPUT.C program should read:
	
	   do
	   {
	    c = getch();
	    c = tolower( c );
	   } while ( c != 'y' && c != 'n');
	
	The INPUT.C program in on-line help already contains this correction,
	but you may want to correct the printed documentation, too.

{% endraw %}
