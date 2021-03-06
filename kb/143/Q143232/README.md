---
layout: page
title: "Q143232: 3D Movie Maker: MIDI Does Not Work Properly with SB AWE 32"
permalink: /kb/143/Q143232/
---

## Q143232: 3D Movie Maker: MIDI Does Not Work Properly with SB AWE 32

{% raw %}

	Article: Q143232
	Product(s): Microsoft Home Kids Products
	Version(s): 1.00
	Operating System(s): 
	Keyword(s): kbfaq
	Last Modified: 08-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft 3D Movie Maker for Windows, versions 95, 1.0 
	- Microsoft Nickelodeon 3D Movie Maker for Windows, version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you run 3D Movie Maker on a computer using a SoundBlaster AWE 32 card, you
	experience MIDI sound problems. Problems include very low volume, or a lack of
	MIDI sound from any program you use after running 3D Movie Maker and until you
	restart your computer.
	
	RESOLUTION
	==========
	
	Try one of the following resolutions.
	
	Resolution 1
	------------
	
	Use the following steps to play MIDI with the Creative Labs SB AWE 32 driver v.
	4.11.10:
	
	1. Restart your computer.
	
	2. With the right mouse button, click the Volume control icon located on the
	  Windows 95 taskbar, and then click Volume Controls.
	
	3. Set master Volume Control (far left control) to half of the maximum volume
	  level.
	
	4. Set Wave volume to maximum volume level.
	
	5. Set MIDI (Synthesizer) volume to maximum volume level.
	
	6. Close Volume Controls.
	
	7. Use Media player to play canyon.mid.
	
	  To find Canyon.mid, do the following:
	  1. With you right mouse button, click the Start button, and then click Find.
	
	  2. In the Named: box, type the following:
	
	  " canyon.mid " (without the quotation marks)
	
	  3. In the Look in box, enter the hard drive where you installed Windows. For
	     example, enter
	
	  " c:\ " (without the quotation marks)
	
	     where C is the letter of the hard drive where you installed Windows.
	
	  4. Click Find Now.
	
	  5. Double-click Canyon.mid.
	
	8. Set your speaker volume to your preferred setting.
	
	9. Start 3D Movie Maker and create a movie with MIDI sounds.
	
	MIDI should now play correctly.
	
	Resolution 2
	------------
	
	Switch the MIDI drive to use FM Synthesis rather than WaveTable Synthesis. To use
	FM Synthesis, follow the steps below.
	
	1. Click the Start button, point to Settings, and click Control Panel.
	
	2. Open the Multimedia control panel.
	
	3. Click the MIDI tab.
	
	4. In the MIDI output section, select the FM Synthesis for Single Instrument.
	
	NOTE: Switching to FM Synthesis eliminates the problems with MIDI volumes and 3D
	Movie Maker (as well as other products from other vendors), but you may notice
	that the FM Synthesis sound quality is lower than the WaveTable Synthesis sound
	quality.
	
	MORE INFORMATION
	================
	
	If you are using Creative Labs, SB AWE 32 driver v.4.12.7 (dated 12/21/95), you
	should hear MIDI regardless of system volume levels. With this driver, however,
	you can no longer change the volume of individual MIDI sounds in 3D Movie
	Maker.
	
	The older (4.11.10) driver incorrectly reports volume settings and always returns
	to full volume (100 percent), regardless of the setting. The volume setting is
	logarithmic, not linear; anything below 50 percent with this driver is silence.
	
	The newer (4.12.7) driver locks the volume at 100 percent to avoid losing sound
	in applications such as 3D Movie Maker.
	
	3D Movie Maker experiences this problem because it allows individual MIDI volumes
	adjustments within the program and the driver does not report these volumes
	correctly to the system. Most other programs leave MIDI as is or set it to 100
	percent.
	
	Other sound boards (such as the UltraSound Max) may display similar problems
	because of borrowed hardware or software from Creative Labs AWE 32.
	
	The third-party products discussed here are manufactured by vendors independent
	of Microsoft; we make no warranty, implied or otherwise, regarding these
	products' performance or reliability.
	
	Additional query words: kids mczee kbmm director animated movies melanie 3-d three dimensional sound blaster creative technologies quiet nothing silence blank halts halting off blaster sound s-b sound-blaster ultra 3dmm audio creative labs
	
	======================================================================
	Keywords          :  kbfaq
	Technology        : kbHomeProdSearch kbZNotKeyword kbKidsSearch kb3dMovieMaker
	Version           : 1.00
	
	=============================================================================
	

{% endraw %}
