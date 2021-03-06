---
layout: page
title: "Q61204: C 6.00 README: Nested Anonymous Structs/Unions"
permalink: /kb/061/Q61204/
---

## Q61204: C 6.00 README: Nested Anonymous Structs/Unions

{% raw %}

	Article: Q61204
	Product(s): See article
	Version(s): 6.00   | 6.00
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | | mspl13_c
	Last Modified: 15-AUG-1990
	
	The following information is taken from the C Version 6.00 README.DOC
	file.
	
	Nested Anonymous Structs/Unions Must Be Completely Specified
	------------------------------------------------------------
	
	You cannot use a tag or typedef to add the members of an anonymous
	(nameless) struct or union to another anonymous struct or union.
	Instead, you must give the full definition of the struct to be nested.
	Assume you have the following anonymous struct:
	
	   struct oneTag
	   {
	       int aMem;
	       int bMem;
	   };
	
	The following code fragment shows the incorrect way to include the
	members of this struct in another anonymous struct:
	
	   struct anotherTag
	   {
	       struct oneTag;       // INCORRECT
	       int cMem;
	   };
	
	The correct method is to specify the nested struct fully:
	
	   struct anotherTag
	   {
	       struct              // CORRECT
	       {
	           int aMem;
	           int bMem;
	       };
	       cMem;
	   };

{% endraw %}
