---
layout: page
title: "Q123967: Code Example Shows How to Manage Navigation Buttons"
permalink: /kb/123/Q123967/
---

## Q123967: Code Example Shows How to Manage Navigation Buttons

{% raw %}

	Article: Q123967
	Product(s): Microsoft FoxPro
	Version(s): MACINTOSH:2.5b,2.5c,2.6,2.6a; MS-DOS:2.0,2.5,2.5a,2.5b,2.6,2.6a; WINDOWS:2.5,2.5a,2.5b,
	Operating System(s): 
	Keyword(s): kbcode
	Last Modified: 11-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	- Microsoft FoxPro for Windows, versions 2.5, 2.5a, 2.5b, 2.6, 2.6a 
	- Microsoft FoxPro for MS-DOS, versions 2.0, 2.5, 2.5a, 2.5b, 2.6, 2.6a 
	- Microsoft FoxPro for Macintosh, versions 2.5b, 2.5c, 2.6, 2.6a 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	When creating a screen, most developers need to add navigation buttons to move
	through the database. You can easily put a push button on a screen to go forward
	one record, but you also need to control button behavior when reaching the
	beginning or the end of a database.
	
	For example, if the user is navigating through a table and reaches the end of
	that table, you might want to have the Next and Bottom buttons disabled.
	Likewise, when the user reaches the top of the table, you might want to have the
	Top and Prior buttons disabled. This article shows by example how to do this.
	
	MORE INFORMATION
	================
	
	The code sample in this article moves the pointer before or after the next or
	prior record you really want to display, thus allowing you to test for BOF() and
	EOF() conditions and have your program respond accordingly by disabling or
	enabling the appropriate buttons.
	
	Code Sample
	-----------
	
	NOTE: While this code can serve as a solid base for use in your own work, it is
	by no means necessarily the only or best way of handling buttons. In its present
	form, the code does not check the status of a record to see if it is deleted. If
	deleted is OFF (the default), this code has the potential to misbehave, so you
	need to check for and handle deleted records and other types of exceptions.
	
	You might want to add code to the "On Screen Entry" or "When" clause code
	snippet, because "Top" and "Prior" are not valid at the beginning of a database.
	You may need to add this code:
	
	     && Disable Top and Prior buttons on startup.
	     SHOW GET Buttnvar,1 DISABLE   && Disable "Top"
	     SHOW GET Buttnvar,2 DISABLE   && Disable "Prior"
	
	Place the following code in the VALID clause of your button array, and change the
	name of the "Buttnvar" variable to the name of the variable you are actually
	using:
	
	  DO CASE
	    CASE Buttnvar = 1         && 'TOP' button
	      GO TOP
	      SCATTER MEMVAR
	      SHOW GET Buttnvar,1 DISABLE   && Disable "Top"
	      SHOW GET Buttnvar,2 DISABLE   && Disable "Prior"
	
	      IF (RECCOUNT() > 1)
	        SHOW GET Buttnvar,3 ENABLE  && Enable  "Next"
	        SHOW GET Buttnvar,4 ENABLE  && Enable  "Bottom"
	      ELSE
	        SHOW GET Buttnvar,3 DISABLE   && Disable "Next"
	        SHOW GET Buttnvar,4 DISABLE   && Disable "Bottom"
	      ENDIF
	      SHOW GETS
	      WAIT WINDOW "At first record" TIMEOUT 1
	      _CUROBJ = OBJNUM(Buttnvar)+3  && Transfer focus to "Next" button
	
	    CASE Buttnvar = 2         && 'PRIOR' button
	      SKIP - 1
	      IF NOT BOF()
	        SCATTER MEMVAR
	      ELSE
	        WAIT WINDOW "At first record" TIMEOUT 1
	        SHOW GET Buttnvar,1 DISABLE   && Disable "Top"
	        SHOW GET Buttnvar,2 DISABLE   && Disable "Prior"
	      ENDIF
	
	      IF (RECCOUNT() > 1)
	        SHOW GET Buttnvar,3 ENABLE  && Enable  "Next"
	        SHOW GET Buttnvar,4 ENABLE  && Enable  "Bottom"
	      ELSE
	        SHOW GET Buttnvar,3 DISABLE   && Disable "Next"
	        SHOW GET Buttnvar,4 DISABLE   && Disable "Bottom"
	      ENDIF
	      SHOW GETS
	
	    CASE Buttnvar = 3         && 'NEXT' button
	      IF  NOT EOF()
	        SKIP 1
	      ENDIF
	
	       IF  EOF()
	        SKIP - 1
	        WAIT WINDOW "At last record" TIMEOUT 1
	        SHOW GET Buttnvar,3 DISABLE   && Disable "Next"
	        SHOW GET Buttnvar,4 DISABLE   && Disable "Bottom"
	      ELSE
	        SHOW GET Buttnvar,1 ENABLE  && Enable  "Top"
	        SHOW GET Buttnvar,2 ENABLE  && Enable  "Prior"
	        SCATTER MEMVAR
	      ENDIF
	      SHOW GETS
	
	    CASE Buttnvar = 4         && 'BOTTOM' button
	      GO BOTTOM
	      SCATTER MEMVAR
	      SHOW GET Buttnvar,3 DISABLE   && Disable "Next"
	      SHOW GET Buttnvar,4 DISABLE   && Disable "Bottom"
	
	      IF (RECCOUNT() > 1)
	        SHOW GET Buttnvar,1 ENABLE  && Enable  "Top"
	        SHOW GET Buttnvar,2 ENABLE  && Enable  "Prior"
	      ELSE
	        SHOW GET Buttnvar,1 DISABLE   && Disable "Top"
	        SHOW GET Buttnvar,2 DISABLE   && Disable "Prior"
	      ENDIF
	      _CUROBJ = OBJNUM(Buttnvar)+1  && Transfer focus to "Prior" button
	      SHOW GETS
	      WAIT WINDOW "At last record" TIMEOUT 1
	
	    CASE Buttnvar = 5      && 'QUIT' button
	      CLEAR READ
	  ENDCASE
	
	You could place the "Show Gets" command at the end of the CASE statement.
	However, sometimes it provides a snappier response when placed at the end of a
	given instruction.
	
	Additional query words: VFoxWin FoxWin FoxMac FoxDos
	
	======================================================================
	Keywords          : kbcode 
	Technology        : kbHWMAC kbOSMAC kbVFPsearch kbAudDeveloper kbFoxproSearch kbZNotKeyword3 kbFoxPro250bMac kbFoxPro260aMac kbFoxPro250cMac kbFoxPro200DOS kbFoxPro250DOS kbFoxPro250aDOS kbFoxPro250bDOS kbFoxPro260DOS kbFoxPro260aDOS kbFoxPro260 kbFoxPro250 kbFoxPro250a kbFoxPro250b kbFoxPro260a kbVFP300
	Version           : MACINTOSH:2.5b,2.5c,2.6,2.6a; MS-DOS:2.0,2.5,2.5a,2.5b,2.6,2.6a; WINDOWS:2.5,2.5a,2.5b,2.6,2.6a,3.0
	
	=============================================================================
	

{% endraw %}
