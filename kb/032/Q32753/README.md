---
layout: page
title: "Q32753: RUNME Program Looks for Drive A Only"
permalink: /kb/032/Q32753/
---

## Q32753: RUNME Program Looks for Drive A Only

{% raw %}

	Article: Q32753
	Product(s): See article
	Version(s): 5.10   | 5.10
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | buglist5.10 | mspl13_masm
	Last Modified: 15-JUL-1988
	
	The MASM setup program is called RUNME. During the setup process,
	the RUNME program will only look to Drive A for the setup files.
	Computers with only a Drive B cannot run the setup program.
	   A workaround is to use the MS-DOS Assign command as follows:
	
	   assign b=a
	
	   Microsoft has confirmed this to be a problem in Version 5.10. We
	are researching this problem and will post new information as it
	becomes available.

{% endraw %}
