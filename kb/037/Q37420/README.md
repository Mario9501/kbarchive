---
layout: page
title: "Q37420: BSEDOSPC.BI Is Missing DosSetSigHandler Definition; for OS/2"
permalink: /kb/037/Q37420/
---

## Q37420: BSEDOSPC.BI Is Missing DosSetSigHandler Definition; for OS/2

{% raw %}

	Article: Q37420
	Product(s): See article
	Version(s): 6.00 6.00b 7.00 7.10
	Operating System(s): OS/2
	Keyword(s): ENDUSER | docerr | mspl13_basic
	Last Modified: 8-JAN-1991
	
	The include file BSEDOSPC.BI fails to include the definition for
	DosSetSigHandler. It should be defined as follows:
	
	   DECLARE FUNCTION DosSetSigHandler%( _
	           BYVAL P1seg AS INTEGER,_
	           BYVAL P1offset AS INTEGER,_
	           SEG   P2 AS LONG,_
	           SEG   P3 AS INTEGER,_
	           BYVAL P4 AS INTEGER,_
	           BYVAL P5 AS INTEGER)
	
	This information applies to Microsoft BASIC Compiler Versions 6.00 and
	6.00b for MS OS/2 and to Microsoft BASIC Professional Development System
	(PDS) Versions 7.00 and 7.10 for MS OS/2.

{% endraw %}
