---
layout: page
title: "Q127912: Writer/Artist: Paint Bucket Does Not Fill"
permalink: /kb/127/Q127912/
---

## Q127912: Writer/Artist: Paint Bucket Does Not Fill

{% raw %}

	Article: Q127912
	Product(s): Microsoft Home Kids Products
	Version(s): WINDOWS:1.0,1.1,1.1a
	Operating System(s): 
	Keyword(s): kbfaq
	Last Modified: 30-APR-1999
	
	1.00 1.10 1.10a
	WINDOWS
	kbenv kbprb kbfaq
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Fine Artist for Windows, versions 1.0, 1.1, 1.1a 
	- Microsoft Creative Writer for Windows, versions 1.1, 1.1a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you use the Paint Bucket tool to color an object or background in Fine
	Artist, or to color a picture in the CD-ROM version of Creative Writer, the tool
	may place a small line of color instead of filling the area.
	
	This behavior occurs if you are using an ATI Mach 64 video card set for more than
	256 colors and with certain other settings.
	
	NOTE: It may also occur if other certain video drivers are set to show more than
	256 colors.
	
	
	RESOLUTION
	==========
	
	To resolve the problem, use the following steps:
	
	Set the video display driver to show 256 colors.
	
	If using ATI Mach 64 video card:
	
	In Program Manager, go to the ATI DeskTop program group and click About DeskTop
	to determine which version of ATI DeskTop is installed on your computer.
	
	Follow the appropriate steps according to your version of ATI DeskTop.
	
	ATI DeskTop Version 1.2 and FlexDesk Version 3.0
	------------------------------------------------
	
	1. Run the ATI FlexDesk utility and choose Advanced.
	
	2. Make sure Color Palette is set to On, then choose OK.
	
	3. Choose OK again to close FlexDesk.
	
	4. A message appears stating that you need to restart Windows for changes to
	  take effect. Do NOT restart Windows; choose Continueinstead.
	
	5. From the ATI DeskTop, choose WinSwitch.
	
	6. If the Enabled check box is selected, clear the check box.
	
	7. You should again receive a message to restart Windows. Choose Restart
	  Windows.
	
	  This version of the ATI Mach 64 driver with these settings works with all
	  Microsoft Kids products.
	
	ATI DeskTop version 1.31 and FlexDesk version 3.0
	-------------------------------------------------
	
	You need a newer video driver to correctly run these programs. If the Color
	Palette is turned On, you can save your work, but the paint bucket does not
	work. If the Color Palette is turned Off, the paint bucket works, but when you
	save your work in Fine Artist, the saved document is black.
	
	ATI DeskTop version 1.4 and FlexDesk version 3.0
	------------------------------------------------
	
	1. Run the ATI FlexDesk utility and choose Advanced.
	
	2. Make sure Color Palette is set to Off, then choose OK.
	
	3. Choose OK again to close FlexDesk.
	
	4. You should receive a message stating that you need to restart Windows for
	  changes to take effect. Do NOT restart Windows; choose Continue instead.
	
	5. From the ATI DeskTop, choose WinSwitch.
	
	6. If the Enabled check box is selected, clear the check box to turn off
	  (disable) this feature.
	
	7. You should again receive a message to restart Windows. Click Restart Windows.
	
	This version of the ATI Mach 64 driver with these settings works only with
	Creative Writer and Fine Artist. For other Microsoft Kids products, or other
	multimedia products that require 256 palette colors, obtain the ATI Mach 64
	DeskTop version 1.2 with FlexDesk version 3.0 from ATI or from your computer
	manufacturer.
	
	MORE INFORMATION
	================
	
	The third-party products discussed in this article are manufactured by vendors
	independent of Microsoft; we make no warranty, implied or otherwise, regarding
	these products' performance or reliability.
	
	Additional query words: 1.00 1.10 1.10a kids mskids cw fa mczee cd disk diskette ATI color paintbucket Mach64 picture pictures sticker stickers palette wm_writer cd-rom cdrom floppy graphic
	
	======================================================================
	Keywords          :  kbfaq
	Technology        : kbHomeProdSearch kbZNotKeyword2 kbCreativeWriter110 kbCreativeWriter110a kbFineArtist100 kbFineArtist110 kbFineArtist110a
	Version           : WINDOWS:1.0,1.1,1.1a
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
