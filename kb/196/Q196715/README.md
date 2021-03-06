---
layout: page
title: "Q196715: WD97: How to Add a Graphic or Logo to Every Label on a Page"
permalink: /kb/196/Q196715/
---

## Q196715: WD97: How to Add a Graphic or Logo to Every Label on a Page

{% raw %}

	Article: Q196715
	Product(s): Word 97 for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbdta word97 kbmerge kblayout
	Last Modified: 05-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	This article describes how to add a graphic or logo to every label on a sheet of
	labels. You can add the graphic or logo either above the label text or to the
	left of the text.
	
	MORE INFORMATION
	================
	
	Use any of the following procedures to add a graphic to each mailing label.
	Instructions for creating a full page of the same labels are given first,
	followed by instructions for including graphics on mail merge labels.
	
	FULL PAGE OF SAME LABEL:
	------------------------
	
	To Place the Graphic Above the Label Text:
	
	1. On the Tools menu, click Envelopes And Labels.
	
	2. Click the Labels tab, and then type the text you want to appear on the
	  labels.
	
	3. Move the insertion point to the beginning of the label.
	
	4. Press ENTER and then move the insertion point up to the blank line.
	
	5. Press CTRL+F9 to insert field braces. Then type the INCLUDEPICTURE field,
	  followed by the path of your graphic.
	
	  NOTE: With Word 97 for Windows, you need to type quotation marks at the
	  beginning and end of the path. For example, to add a graphic named Apple.wmf
	  to your labels, press CTRL+F9 and then type the following:
	
	  includepicture "c:\\winword\\clipart\\apple.wmf"
	
	6. Click New Document.
	
	7. On the Edit menu, click Select All.
	
	8. Press F9 to update the fields.
	
	To Place the Graphic to the Left of the Text:
	
	1. On the Tools menu, click Envelopes And Labels.
	
	2. Click the Labels tab and then type the text you want to appear. Select all
	  the text in the label.
	
	3. Right-click once.
	
	4. Click Paragraph on the shortcut menu.
	
	5. In the Indent From Left box, type the amount of space you need for the
	  graphic. For example, if the graphic is a half-inch wide, type .5 in the box.
	
	6. Click OK.
	
	7. Click New Document.
	
	8. On the View menu, click Page Layout.
	
	9. Activate the Drawing toolbar by choosing the Drawing button on the Standard
	  toolbar.
	
	10. On the Drawing toolbar, click the Text Box button.
	
	11. Next to the first label, create a text box the size you want for your
	  graphic.
	
	12. On the Insert menu, point to Picture, and then click From File.
	
	13. Select the graphic you want to include.
	
	14. Click Insert. The graphic appears in the text box.
	
	15. Select the text box.
	
	16. On the Edit menu, click Copy.
	
	17. Move the insertion point to the beginning of the next label.
	
	
	18. On the Edit menu, click Paste.
	
	19. The graphic is actually pasted on top of the existing graphic. Using the
	  mouse, drag the graphic to the second label.
	
	20. On the Edit menu, click Paste.
	
	21. The graphic appears on top of the graphic in the first label. Drag this
	  graphic to the next label.
	
	22. Repeat steps 20 and 21 until all the labels have pictures.
	
	MAIL MERGE:
	-----------
	
	To Place the Graphic above the Label Text:
	
	1. In the Create Labels dialog box, after setting up the fields you want to
	  include in the label, place the insertion point at the beginning of the
	  label.
	
	2. Press ENTER and then move the insertion point up to the blank line.
	
	3. Press CTRL+F9 to insert field braces. Then type the INCLUDEPICTURE field,
	  followed by the path of your graphic.
	
	  NOTE: With Word 97 for Windows, you need to type quotation marks at the
	  beginning and end of the path. For example, to add a graphic named Apple.wmf
	  to your labels, press CTRL+F9 and then type the following:
	
	  includepicture "c:\\winword\\clipart\\apple.wmf"
	
	4. Click New Document.
	
	When you merge the file, the graphic appears on each label. Note that if you view
	the merge field names, <<Next Record>> appears at the beginning of
	every label except the first one. The graphic is to the right of it. This is
	normal, and the graphic will appear on the merged document correctly.
	
	
	To Place the Graphic to the Left of the Text:
	
	1. In the Create Labels dialog box, insert the merge fields in the label as you
	  want them to appear.
	
	2. Select all the fields in the label.
	
	3. Right-click once.
	
	4. Click Paragraph on the shortcut menu.
	
	5. In the Indent From Left box, type the amount of space you need for the
	  graphic. For example, if the graphic is a half-inch wide, type .5 in the box.
	
	6. Click OK.
	
	7. Click New Document.
	
	8. On the View menu, click Page Layout.
	
	9. Activate the Drawing toolbar by choosing the Drawing button on the Standard
	  toolbar.
	
	10. On the Drawing toolbar, click the Text Box button.
	
	11. Next to the first label, create a text box the size you want for your
	  graphic.
	
	12. On the Insert menu, point to Picture, and then click From File.
	
	13. Select the graphic you want to include.
	
	14. Click Insert. The graphic appears in the text box.
	
	15. Select the text box.
	
	16. On the Edit menu, click Copy.
	
	17. Move the insertion point to the beginning of the next label.
	
	
	18. On the Edit menu, click Paste.
	
	19. The graphic is actually pasted on top of the existing graphic. Using the
	  mouse, drag the graphic to the second label.
	
	20. On the Edit menu, click Paste.
	
	21. The graphic appears on top of the graphic in the first label. Drag this
	  graphic to the next label.
	
	22. Repeat steps 20 and 21 until all the labels have pictures.
	
	Additional query words: logo logos table labels graphics adding textbox 8.0 8.00 wd6x include
	
	======================================================================
	Keywords          : kbdta word97 kbmerge kblayout 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : :
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
