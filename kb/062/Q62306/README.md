---
layout: page
title: "Q62306: C1001: Internal Compiler Error: '../grammar.c', Line 140"
permalink: /kb/062/Q62306/
---

## Q62306: C1001: Internal Compiler Error: '../grammar.c', Line 140

{% raw %}

	Article: Q62306
	Product(s): See article
	Version(s): 6.00   | 6.00
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | buglist6.00 | mspl13_c
	Last Modified: 24-JUL-1990
	
	The code below, when compiled with Microsoft C 6.00 for the compact or
	large memory models, produces the following error:
	
	   test.c(13) : fatal error C1001: Internal Compiler Error
	                (compiler file '../grammar.c', line 140)
	                Contact Microsoft Product Support Services
	
	Sample Code
	-----------
	
	#include <string.h>
	#pragma intrinsic( strcmp )         /* Intrinsic form of strcmp */
	
	char    *s1 = "Standard input",     /* s1 and s2 must be    */
	        *s2 = "Standard output";    /* initialized to fail. */
	
	void main()
	{
	    register int i;                 /* i must be register */
	
	    if( strcmp( s1, s2 ) == 0 );
	
	    for( i = 0; i < 5; ++i );
	}
	
	To work around this problem, one of several solutions may be used:
	
	1. Use the nonintrinsic form of strcpy.
	
	2. Do not specify i as a register variable.
	
	3. If appropriate, use a memory model with near data pointers.
	
	Microsoft has confirmed this to be a problem in C 6.00. We are
	researching this problem and will post new information here as it
	becomes available.

{% endraw %}
