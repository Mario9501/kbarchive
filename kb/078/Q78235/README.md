---
layout: page
title: "Q78235: Bookshelf for Windows 1991: Manual Installation Instructions"
permalink: /kb/078/Q78235/
---

## Q78235: Bookshelf for Windows 1991: Manual Installation Instructions

{% raw %}

	Article: Q78235
	Product(s): Microsoft Home Multimedia Titles
	Version(s): 1991 edition
	Operating System(s): 
	Keyword(s): 
	Last Modified: 04-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Bookshelf for Windows 1991 edition 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Perform the following steps to manually install Microsoft Bookshelf for Windows,
	1991 edition. For instructions on how to copy or create directories, see your
	Windows documentation or online Help. These directions assume that your hard
	disk is drive C and your CD-ROM drive is drive X.
	
	1. Create a directory (folder) called Viewer on the hard disk (drive C).
	
	2. Copy all files from the X:\Viewer directory on the CD-ROM to the C:\Viewer
	  directory on the hard disk.
	
	3. Copy *.ico from the X:\Books directory on the CD-ROM to C:\Viewer.
	
	4. Add C:\Viewer to the path statement in the Autoexec.bat file.
	
	5. The Bookshelf Setup program installs special screen fonts during normal
	  installation. These fonts need to be installed manually if you install
	  Bookshelf manually. You can do this by doing the following:
	  a. From the Control Panel window, double-click Fonts.
	
	  b. Click the Add button in Windows 3.x. In Windows 95, click File, then click
	     Install New Font.
	
	  c. Change the drive to your CD-ROM drive.
	
	  d. Double-click the Viewer folder.
	
	  e. Select the following fonts by holding down the CTRL key while clicking
	     each desired font.
	
	     Select the fonts appropriate for the type of graphics adapter installed in
	     the computer:
	
	       For VGA and VGA+ (640 x 480) systems:
	              Lucida Sans B 10,12,14
	              Lucida Sans B1 10,12,14
	              Lucida Sans B2 10,12,14
	              Symbol B
	
	       For EGA:
	              Lucida Sans B (EGA) 10,12,14
	              Lucida Sans B1 (EGA) 10,12,14
	              Lucida Sans B2 (EGA) 10,12,14
	              Symbol B (EGA)
	
	        For 8514 (1024 x 768):
	              Lucida Sans B (8514) 10,12,14
	              Lucida Sans B1 (8514) 10,12,14
	              Lucida Sans B2 (8514) 10,12,14
	              Symbol B (8514)
	
	  f. Make sure the "Copy fonts to..." box is checked.
	
	  g. Click the OK button.
	
	Create the Program Group in Windows 3.x
	---------------------------------------
	
	1. Create a new program group called "Microsoft Bookshelf - 1991". In the
	  Program Manager, choose New from the File menu. Select New Program Group and
	  choose the OK button. Type "Microsoft Bookshelf - 1991" (without the
	  quotation marks) in the Description line and choose OK.
	
	2. Now, add the following new program items to this group. In the Program
	  Manager, choose New from the File menu and choose the OK button to add a
	  program item. Type the following description and command line for each
	  program item.
	
	     Description       Command Line
	     -----------       ------------
	
	     Bookshelf 1991    c:\viewer\viewer.exe x:\books\books.mvb
	
	     Concise Quotes    c:\viewer\viewer.exe x:\books\cquote.mvb
	
	     Bartlett's        c:\viewer\viewer.exe x:\books\bquote.mvb
	
	     Encyclopedia      c:\viewer\viewer.exe x:\books\encyc.mvb
	
	     Dictionary        c:\viewer\viewer.exe x:\books\dict.mvb
	
	     Thesaurus         c:\viewer\viewer.exe x:\books\roget.mvb
	
	     Atlas             c:\viewer\viewer.exe x:\books\atlas.mvb
	
	     1991 Almanac      c:\viewer\viewer.exe x:\books\wa91.mvb
	
	     Tutorial          c:\viewer\viewer.exe x:\books\bkstut1.mvh
	
	     Quickeys          c:\viewer\quickeys.exe
	
	3. Click once on each icon to select it. From the File menu, choose Properties.
	  Choose the Change Icon button and enter the appropriate icon filename.
	
	     Icon                     Icon Filename
	     ----                     -------------
	
	     Bookshelf 1991           c:\viewer\books.ico
	
	     Concise Quotes           c:\viewer\cquote.ico
	
	     Bartlett's               c:\viewer\bquote.ico
	
	     Encyclopedia             c:\viewer\encyc.ico
	
	     Dictionary               c:\viewer\dict.ico
	
	     Thesaurus                c:\viewer\roget.ico
	
	     Atlas                    c:\viewer\atlas.ico
	
	     1991 Almanac             c:\viewer\wa91.ico
	
	     Tutorial                 c:\viewer\tuticon.ico
	
	     Quickeys                 <none>
	
	Add the Bookshelf items to the Start Menu in Windows 95
	-------------------------------------------------------
	
	1. With your right mouse button, click the taskbar and then click Properties.
	
	2. Click the Start Menu Programs tab, and then click Advanced.
	
	3. Double-click the Programs folder
	
	4. Add a Bookshelf folder:
	  1. Click File, point to New, and then click Folder.
	
	  2. Type the following and press the ENTER key:
	
	  "Microsoft Bookshelf - 1991" (without the quotation marks)
	
	     Double-click the new Bookshelf folder to open it.
	
	5. Add each Bookshelf shortcut icon:
	  a. Click File, point to New, and then click Shortcut.
	
	  b. Type the following in the Command Line box:
	
	  "C:\Viewer\Viewer.exe X:\Books\Books.mvb" (without the quotation marks)
	
	  c. Click Next, and type the following in the "Select a name..." box:
	
	  "Bookshelf 1991" (without the quotation marks)
	
	  d. Click Finish.
	
	  Repeat step 5 to add a shortcut for each Bookshelf item listed above in the
	  Program Manager instructions (refer to the table with the headings
	  "Description" and "Command Line").
	
	6. Change each Bookshelf shortcut icon:
	  a. With your right mouse button, click the "Bookshelf 1991" shortcut, then
	     click Properties.
	
	  b. Click the Shortcut tab, and then click Change Icon.
	
	  c. In the File Name box, type the following:
	
	  "C:\Viewer\Books.ico" (without the quotation marks)
	
	  d. Click OK, then click OK again.
	
	  Repeat step 6 to change each shortcut icon according to the "Description" and
	  "Icon Filename" table in step 3 of the "Create the Program Group in Windows
	  3.x" section of this article.
	
	Restart Windows
	---------------
	
	Exit or Shut Down Windows and restart the computer. The installation is now
	complete.
	
	Additional query words: Viewer 1991 1.0 1.00 manually Usage set up install installation
	
	======================================================================
	Keywords          :  
	Technology        : kbHomeMMsearch kbBookshelfSearch kbBookShelf1991
	Version           : :1991 edition
	
	=============================================================================
	

{% endraw %}
