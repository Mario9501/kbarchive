---
layout: page
title: "Q249291: BUG: Dialog Editor Doesn't Permit a Taskbar Icon if Titlebar Off"
permalink: /kb/249/Q249291/
---

## Q249291: BUG: Dialog Editor Doesn't Permit a Taskbar Icon if Titlebar Off

{% raw %}

	Article: Q249291
	Product(s): Microsoft C Compiler
	Version(s): winnt:5.0,6.0
	Operating System(s): 
	Keyword(s): kbEditor kbide _IK920 kbVC600bug kbDSupport kbGrpDSTools
	Last Modified: 07-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, versions 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Professional Edition, versions 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	It is possible to create an MFC dialog box-based application with no title bar
	by turning off the dialog box's standard Title bar style. However, when the
	application runs, the shell taskbar displays a blank button with no icon and no
	text, even though the icon resource exists.
	
	CAUSE
	=====
	
	For the shell's taskbar to display an icon, the dialog template needs the System
	menu style WS_SYSMENU. The resource editor automatically disables that style and
	others if the Title bar style is not turned on.
	
	RESOLUTION
	==========
	
	Manually add the WS_SYSMENU style by editing the resource as text. If you will
	be editing any resources afterwards, you will also need to move the dialog
	resource to the res\<projname>.rc2 file. This prevents the resource editor
	from overwriting your change, but it also prevents you from being able to edit
	the dialog box with the resource editor.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	For some applications, a dialog box functions conveniently as a main window.
	Visual C++ provides a dialog-based option in the MFC AppWizard (exe) for that
	purpose. If you want a main dialog window without a standard title bar in such
	an application, you must edit the dialog properties in ResourceView. To do this,
	follow these steps in your open project:
	
	1. From the File menu, select New. Select the MFC AppWizard (exe). Name it
	  NoTitle and click OK.
	
	2. In Step 1 of the AppWizard, select Dialog-based. Click Finish, then click OK
	  on the confirmation dialog box.
	
	3. In ResourceView, expand the Dialog resources. Double-click
	  IDD_NOTITLE_DIALOG.
	
	4. Right-click an unused area of the dialog box, and select Properties.
	
	5. In the Properties editor, click the Styles tab, and clear the Title bar check
	  box.
	
	If you build and run the project at this point, you will notice that the button
	that the shell normally displays in the taskbar for your running application is
	completely blank. There is no icon, and there is no text.
	
	If you go back to the Properties editor for the main dialog box at this point,
	you will notice that various items in the Styles tab are disabled. One of those
	items is the System menu check box. That check box controls adding the
	WS_SYSMENU style to the dialog resource. The dialog needs this style in order
	for the application icon to appear in the taskbar. For additional information on
	how to display an icon in the title bar, click the article number below to view
	the article in the Microsoft Knowledge Base:
	
	  Q179582 HOWTO: Set the Title Bar Icon in a Dialog Box
	
	Though the resource editor prevents adding the WS_SYSMENU style to a dialog box
	with no title, the combination is possible. You can manually edit the
	<projname>.rc file to put the WS_SYSMENU style in and verify that it
	causes an icon to appear in the taskbar button:
	
	1. In the open project created earlier, from the File menu, select Open.
	
	2. In the Open as dropdown list, select Text.
	
	3. Type NoTitle.rc in the File name edit box, then click Open. If the
	  ResourceView is open for the project, you will see a warning dialog box that
	  the resource editor will be closed. Click OK to allow that.
	
	4. Move down to the Dialog section of the .rc file. Locate the
	  IDD_NOTITLE_DIALOG DIALOGEX resource.
	
	5. On the line labeled STYLE following the dialog name, append:
	
	   | WS_SYSMENU
	
	6. Now, select the lines defining the dialog resource, starting with the
	  resource name down to and including the END tag. Using the standard editor,
	  select by dragging the mouse over those lines.
	
	7. From the Edit menu, select Cut. The selected resource disappears.
	
	8. Open the NoTitle.rc2 resource file. On the workspace pane, click the FileView
	  tab. Expand the project's Resource Files folder, and double-click the
	  NoTitle.rc2 file.
	
	9. Position the cursor at the end of any text in the NoTitle.rc2 file (or at
	  another convenient location), then from the Edit menu, click Paste. The
	  dialog resource has now been transferred to the manually edited resource
	  file.
	
	10. Press CTRL+F5 to build and run the project. Note that an icon now appears on
	  the taskbar button associated with your application.
	
	Clearing the Title bar check box also disables the Caption field in the dialog
	resource General properties. If you add a CAPTION entry in the resource with or
	without a WS_CAPTION style, you will get a title bar anyway. To display text in
	the taskbar button, you must call SetWindowText() in the OnCreate() handler or
	some other appropriate place:
	
	1. From the View menu, select ClassWizard.
	
	2. On the Message Maps tab, select the main dialog class from the Class name
	  drop down list.
	
	3. In the Messages list, double-click the WM_CREATE message. Click the Edit code
	  button.
	
	4. Under the TODO line, just before the return from the function, add:
	
	  SetWindowText("MyTitle");
	
	5. Press CTRL+F5 to build and run the project. Notice that the application has
	  no title bar, but an icon and the text you entered in the SetWindowText()
	  call appear on the taskbar button.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbEditor kbide _IK920 kbVC600bug kbDSupport kbGrpDSTools 
	Technology        : kbVCsearch kbAudDeveloper kbVC500 kbVC600 kbVC32bitSearch kbVC500Search
	Version           : winnt:5.0,6.0
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
