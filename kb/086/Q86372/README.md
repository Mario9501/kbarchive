---
layout: page
title: "Q86372: PC Mac: New Features in 3.0 Macintosh Client"
permalink: /kb/086/Q86372/
---

## Q86372: PC Mac: New Features in 3.0 Macintosh Client

{% raw %}

	Article: Q86372
	Product(s): Microsoft Mail For PC Networks
	Version(s): WINDOWS:3.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 19-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for PC Networks, version 3.0, on platform(s):
	   - the operating system: Mac OS (ALL) 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following is a list of features new in version 3.0 of the Microsoft Mail for
	PC Networks Macintosh client.
	
	NOTE: The Macintosh client relies on the server and/or MS-DOS client to install
	template files. For example, to install a French Macintosh client on an English
	postoffice, the French MS-DOS client must be installed first.
	
	Global Address List
	-------------------
	
	The word "Global" appears as the first entry in the left-hand list of lists in
	the addressing dialog box when this dialog box appears for addressing mail or
	copying users to the personal address list (PAL). Double-clicking the Global
	entry causes the Global Address List (GAL) to appear in the left- hand list. GAL
	addresses can be selected for addressing mail. Only non- group addresses can be
	selected for moving to the Personal Address List (PAL). The client issues an
	error message if you attempt to move a group entry.
	
	In the Preferences dialog box, the pop-up menu for Default Address List contains
	the word "Global" as the first entry. Selecting this entry will make the GAL the
	default address list that appears whenever the addressing dialog is invoked.
	
	Orphaned Personal Address List (PAL) Entry Behavior
	---------------------------------------------------
	
	If an invalid address is found in the PAL while trying to transmit mail, the
	message "Invalid address for USER. Resume editing?" is displayed. Regardless of
	whether you select OK or Cancel, this first message is followed by the message,
	"Delete the alias for USER from your Personal Address List?" If you select OK,
	the alias is removed from your PAL.
	
	System 7 Features
	-----------------
	
	Under System 7, the following features are available:
	
	- Full international support
	
	  For complete support of extended characters found in code page 850, you must
	  use System 7 because the System 6 system font is missing some of the
	  necessary glyphs.
	
	- Core Apple events
	
	  The application processes open application, open document, print, and quit
	  Apple events. The print event can only be used on a file of type TEXT saved
	  by the application. Folders cannot be printed this way and no logon will
	  occur. The application quits immediately after printing.
	
	- File alias resolution
	
	  Aliases are resolved to the file or folder it refers to in the attachment
	  dialog.
	
	- TrueType fonts
	
	  The application uses TrueType fonts for all user interface text display.
	
	Editing of Forwarded Attachment List
	------------------------------------
	
	All attachments are still forwarded when you forward a message with attachments,
	but now you can remove any of the attachments from the attachments dialog box in
	the same way other attachments are removed. However, the attachments cannot be
	added once they are removed. A document icon is now associated with new
	attachments because the format option only applies to newly added attachments.
	
	Large Message Viewing
	---------------------
	
	You can read messages that are larger than 10 MB. The maximum size is limited by
	other factors such as the amount of memory allocated to the application.
	
	Multiple Compose Windows
	------------------------
	
	You can now open any number of Compose windows. The first one is titled "Compose
	- 1." The number is sequential and is increased for each new Compose window as
	long as any Compose windows remain. When there are no more Compose windows, the
	number is reset to 1 (one). Each Compose window is opened in a tiled position.
	
	Transmit Speed Increased
	------------------------
	
	The time to transmit a message has been decreased by a factor of about 14.
	
	Keyboard Focus Feedback
	-----------------------
	
	Standard System 7 visual feedback that indicates which list has the keyboard
	focus has been added to the Addressing and New Personal Group dialogs. The TAB
	key is used to change the focus.
	
	Scroll Thumb Position Maintenance
	---------------------------------
	
	The scroll thumb position is now maintained in folder windows after messages are
	deleted, moved, logged, saved, or copied to a folder. Previously, the thumb was
	reset to the top.
	
	Abort of Long Operations
	------------------------
	
	The feedback dialog boxes for long operations now have a Stop button. These
	operations include: Copy, Move, Delete, Attachment Save, Compress, and Resort.
	The original state is not recovered. The Send operation can be aborted before
	the message starts getting delivered to individual recipients (as indicated by
	the recipient's name being displayed in the progress dialog).
	
	Undo
	----
	
	A single level undo operation is now available in Compose windows.
	
	Enforcement of 78-Character Lines
	---------------------------------
	
	When you compose a message, you can insert a maximum of 78 characters on each
	line before word wrapping occurs.
	
	The rules for enforcing this limit are:
	
	- The words at the end of the growing sentence get wrapped to the next line.
	  Call this the "overflow".
	
	- If the next line is a blank line, a new line is inserted before the next line
	  for the overflow to go on. This preserves the blank line.
	
	- If the overflow can fit on the next line without causing another wrap, it is
	  inserted at the beginning of that line.
	
	- If the overflow cannot fit on the next line without causing the next line to
	  also wrap, a new line is inserted before the next line for the overflow to go
	  on.
	
	Viewing a Macbinary Data Fork
	-----------------------------
	
	To avoid displaying garbled characters, when you view a Macbinary file, only the
	data fork is shown.
	
	First Logon Becomes Default
	---------------------------
	
	After the first successful logon by a new user, the application uses the entered
	user information as the default for subsequent logon attempts.
	
	Prints Wide Messages
	--------------------
	
	You can print messages that are wider than the paper in the printer. The area
	that was previously truncated is now printed on the next sheet. To read the
	message, place the second piece of paper to the right of the first piece.
	
	Nonprintable Characters Filtered Out
	------------------------------------
	
	Nonprintable characters can no longer be entered in dialog edit boxes.
	
	Notification on Startup
	-----------------------
	
	The notifier can now detect new mail on startup rather than just new mail that
	arrives after startup.
	
	Additional query words: 3.00 Macintosh Apple AppleTalk
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3
	Version           : WINDOWS:3.0
	
	=============================================================================
	

{% endraw %}
