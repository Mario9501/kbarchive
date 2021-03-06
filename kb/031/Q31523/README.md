---
layout: page
title: "Q31523: MASM 5.10 EXT.DOC: DelFile - Deletes Contents of File"
permalink: /kb/031/Q31523/
---

## Q31523: MASM 5.10 EXT.DOC: DelFile - Deletes Contents of File

{% raw %}

	Article: Q31523
	Product(s): See article
	Version(s): 5.10   | 5.10
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | | mspl13_masm
	Last Modified: 12-JAN-1989
	
	The following information is from the MASM Version 5.10 EXT.DOC
	file.
	   Please note that numbering for both COL and LINE variables begins
	with 0.
	
	/*  DelFile - deletes contents of file
	 *
	 *  The DelFile function deletes the entire contents of an internal
	 *  file buffer. The effect of deleting contents can be made
	 *  permanent by calling the FileWrite function, which replaces the
	 *  contents of the file on disk with the contents of the internal
	 *  file buffer.
	 *
	 *  pFile       Handle to file that is to be cleared
	 */
	void pascal DelFile (pFile)
	PFILE pFile;

{% endraw %}
