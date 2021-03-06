---
layout: page
title: "Q316011: HOW TO: Programmatically Add Meta Information to All Pages"
permalink: /kb/316/Q316011/
---

## Q316011: HOW TO: Programmatically Add Meta Information to All Pages

{% raw %}

	Article: Q316011
	Product(s): Word Front Page
	Version(s): 
	Operating System(s): 
	Keyword(s): kbHOWTOmaster
	Last Modified: 13-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FrontPage 2002 
	- Microsoft FrontPage 2000 
	-------------------------------------------------------------------------------
	
	IN THIS TASK
	------------
	
	- SUMMARY
	
	   - Step 1 - Add Custom META Properties to Your Web Settings
	- Step 2 - Add the Sample Macro to FrontPage
	- Step 3 - Run the Sample Macro in FrontPage
	
	- REFERENCES
	
	
	SUMMARY
	=======
	
	Use this step-by-step guide to programmatically standardize the META tags
	throughout your Web site. After you manually add parameters to your Web site,
	the sample Visual Basic for Applications macro examines your Web settings for
	the parameters and adds META tags to each page in your Web site.
	
	META tags help describe your Web site so that search engines, such as
	http://search.msn.com/, pull your pages when a search is performed. Description
	and keyword meta tags increase the likelihood that the search engine will index
	your Web site. For additional information, click the article number below to
	view the article in the Microsoft Knowledge Base:
	
	  Q205493 FP: How to Use the META Element with Web Spiders and Robots
	
	Step 1 - Add Custom META Properties to Your Web Settings
	--------------------------------------------------------
	
	The sample Visual Basic for Applications macro in Step 2 later in this article,
	looks for custom parameters that begin with the meta- prefix in your Web
	settings, and uses these parameters to add META tags to each page in your Web
	site.
	
	To begin this exercise, add the following custom parameters:
	
	- meta-description
	- meta-keywords
	
	Note that you can use the following procedure to add additional custom
	parameters, such as meta-author, meta-copyright, meta-robots and so on.
	
	To add the custom parameters, follow these steps:
	
	1. Start FrontPage and then open a Web.
	
	2. On the Tools menu, click Web Settings to open the Web Settings dialog box.
	
	3. In the Web Settings dialog box, click the Parameters tab.
	
	4. Click Add and then perform the following steps:
	
	  a. In the Name box, type "meta-description" (without the quotation marks).
	
	  b. In the Value box, type "This is my Web site" (without the quotation
	     marks).
	
	  c. Click OK.
	
	5. Click Add and then perform the following steps:
	
	  a. In the Name box, type "meta-keywords" (without the quotation marks).
	
	  b. In the Value box, type "Web, site, Internet" (without the quotation
	     marks).
	
	  c. Click OK.
	
	6. Click OK to close the Web Settings dialog box.
	
	Step 2 - Add the Sample Macro to FrontPage
	------------------------------------------
	
	Microsoft provides programming examples for illustration only, without warranty
	either expressed or implied, including, but not limited to, the implied
	warranties of merchantability and/or fitness for a particular purpose. This
	article assumes that you are familiar with the programming language being
	demonstrated and the tools used to create and debug procedures. Microsoft
	support professionals can help explain the functionality of a particular
	procedure, but they will not modify these examples to provide added
	functionality or construct procedures to meet your specific needs. If you have
	limited programming experience, you may want to contact a Microsoft Certified
	Partner or the Microsoft fee-based consulting line at (800) 936-5200. For more
	information about Microsoft Certified Partners, please visit the following
	Microsoft Web site:
	
	  http://www.microsoft.com/partner/referral/
	
	For more information about the support options that are available and about how
	to contact Microsoft, visit the following Microsoft Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	The following sample macro looks for the meta- prefix in the custom parameters
	you added in Step 1. Then, based on the parameters it finds, it adds META tags
	to each page in your Web site.
	
	To add this macro to FrontPage, follow these steps:
	
	1. Start the Visual Basic Editor. To do this, point to Macro on the Tools menu,
	  and then click Visual Basic Editor.
	
	2. Create a new module. To do this, right-click Microsoft_FrontPage, click
	  Insert, and then click Module.
	
	3. Type or paste the following Visual Basic code into the new module:
	
	  Option Explicit
	
	  Sub SetAllMetaTags()
	    On Error Resume Next
	    
	    ' Declare all variables.
	    Dim X As Integer
	    Dim Y As Integer
	    Dim objWebFolder As WebFolder
	    Dim objWebFile As WebFile
	    Dim varFolderTree As Variant
	    Dim varMetaProperties As Variant
	    Dim strExt As String
	    Dim strMetaTag As String
	      
	    With Application
	      
	      ' Check the caption of the application to see if a Web is open.
	      If .ActiveWebWindow.Caption = "Microsoft FrontPage" Then
	        ' If no Web is open, display an informational message.
	        MsgBox "Please open a Web before running this function.", vbCritical
	        ' End the macro.
	        Exit Sub
	      ' Check to make sure that no pages are open.
	      ElseIf .ActiveWeb.ActiveWebWindow.PageWindows.Count <> 0 Then
	        ' If any pages are open, display an informational message.
	        MsgBox "Please close all files before running this macro.", vbCritical
	        ' End the macro.
	        Exit Sub
	      End If
	      
	      ' Change the Web view to Folder view.
	      .ActiveWeb.ActiveWebWindow.ViewMode = fpWebViewFolders
	      
	      ' Get a list of folders in the Web.
	      varFolderTree = BuildFolderUrlTree
	      ' Get a list of custom META properties for the Web.
	      varMetaProperties = GetCustomMetaProperties
	      
	      ' Is the array populated?
	      If UBound(varMetaProperties) > 0 Then
	        ' If so, loop through the folders.
	        For X = 1 To UBound(varFolderTree)
	          ' Create a folder object.
	          Set objWebFolder = .ActiveWeb.LocateFolder(varFolderTree(X))
	          ' Loop through the files in the folder.
	          For Each objWebFile In objWebFolder.Files
	            ' Get the current file extension.
	            strExt = LCase(objWebFile.Extension)
	            ' Is it a Web page?
	            If strExt = "htm" Or strExt = "html" Or strExt = "asp" Then
	              ' If so, edit the page.
	              objWebFile.Edit
	              ' Loop through the custom properties.
	              For Y = 1 To UBound(varMetaProperties)
	                ' Set each property.
	                SetMetaTag varMetaProperties(Y, 1), varMetaProperties(Y, 2)
	              Next
	              ' Save and close the page.
	              .ActivePageWindow.Save
	              .ActivePageWindow.Close
	            End If
	          Next
	        Next
	      End If
	    End With
	    
	    ' Return a message that the META tags are updated.
	    MsgBox "Finished updating META tags!", vbInformation
	
	  End Sub
	
	  Private Function GetCustomMetaProperties() As Variant
	    On Error Resume Next
	    
	    ' Declare all variables.
	    Dim objProperty As Variant
	    Dim intMetaTags As Integer
	    Dim strMetaNames() As String
	    Dim strMetaContents() As String
	    Dim strMetaTags() As Variant
	    Dim X As Integer
	    
	    With Application
	      ' Loop through the Web properties.
	      For Each objProperty In .ActiveWeb.Properties
	        ' Did you find a property?
	        If Len(CStr(objProperty)) > 0 Then
	          ' Is it one of the custom properties?
	          If StrComp(Left(objProperty, 5), "meta-", vbTextCompare) = 0 Then
	            ' Update counter.
	            intMetaTags = intMetaTags + 1
	            ' Redimension storage arrays.
	            ReDim Preserve strMetaNames(intMetaTags)
	            ReDim Preserve strMetaContents(intMetaTags)
	            ' Store the META name.
	            strMetaNames(intMetaTags) = Mid(objProperty, 6)
	            ' Store the META content.
	            strMetaContents(intMetaTags) = .ActiveWeb.Properties(objProperty)
	          End If
	        End If
	      Next
	    End With
	    
	    ' See if there are any properties.
	    If intMetaTags = 0 Then
	      ' If there are no properties, return an empty array.
	      ReDim strMetaTags(0)
	    Else
	      ' Otherwise, create an array to hold the properties.
	      ReDim strMetaTags(intMetaTags, 2)
	      ' Loop through the properties and values and store them.
	      For X = 1 To intMetaTags
	        strMetaTags(X, 1) = strMetaNames(X)
	        strMetaTags(X, 2) = strMetaContents(X)
	      Next
	    End If
	    
	    ' Return the array.
	    GetCustomMetaProperties = strMetaTags
	
	  End Function
	
	  Private Sub SetMetaTag(strMetaName, strMetaContent)
	    On Error Resume Next
	    
	    ' Declare all variables.
	    Dim objMetaTag As FPHTMLMetaElement
	    Dim objHtmlTag As IHTMLElement
	    
	    With Application
	      ' Create an object for the META tag.
	      Set objMetaTag = .ActiveDocument.all.tags("meta").Item(strMetaName)
	      ' Set the tag's value.
	      objMetaTag.content = strMetaContent
	      ' If there is an error.
	      If Err.Number > 0 Then
	        ' Get an object for the document HEAD section.
	        Set objHtmlTag = .ActiveDocument.all.tags("HEAD").Item(0)
	        ' Add the META tag.
	        Call objHtmlTag.insertAdjacentHTML("BeforeEnd", "<meta name=""" & _
	          strMetaName & """ content=""" & strMetaContent & """>" & vbCrLf)
	      End If
	    End With
	    
	  End Sub
	
	  Private Function BuildFolderUrlTree() As Variant
	    On Error Resume Next
	    
	    ' Declare all variables.
	    Dim objWebFolder As WebFolder
	    Dim objFolder As WebFolder
	    Dim objSubFolder As WebFolder
	    Dim strBaseFolder As String
	    Dim lngFolderCount As Long
	    Dim lngBaseCount As Long
	       
	    With Application
	    
	      ' Check the caption of the application to see if a Web is open.
	      If .ActiveWebWindow.Caption = "Microsoft FrontPage" Then
	        ' If no Web is open, display an informational message.
	        MsgBox "Please open a Web before running this function.", vbCritical
	        ' End the macro.
	        Exit Function
	      End If
	    
	      ' Change the Web view to Folder view.
	      .ActiveWeb.ActiveWebWindow.ViewMode = fpWebViewFolders
	      ' Refresh the Web view and recalculate the Web.
	      .ActiveWeb.Refresh
	      
	      ' Define the initial values for the folder counters.
	      lngFolderCount = 1
	      lngBaseCount = 0
	    
	      ' Dimension an array to hold the folder names.
	      ReDim strFolders(1) As Variant
	    
	      ' Get the URL of the root folder for the Web.
	      strBaseFolder = .ActiveWeb.RootFolder.Url
	      ' Store the URL in the array.
	      strFolders(1) = strBaseFolder
	      
	      ' Loop while there are folders to process.
	      While lngFolderCount <> lngBaseCount
	        ' Set up a WebFolder object to a base folder.
	        Set objFolder = .ActiveWeb.LocateFolder(strBaseFolder)
	        ' Loop through the collection of subfolders for the base folder.
	        For Each objSubFolder In objFolder.Folders
	          ' Check to make sure that the subfolder is not a Web.
	          If objSubFolder.IsWeb = False Then
	            ' Increment the folder count.
	            lngFolderCount = lngFolderCount + 1
	            ' Increase the array size.
	            ReDim Preserve strFolders(lngFolderCount)
	            ' Store the folder name in the array.
	            strFolders(lngFolderCount) = objSubFolder.Url
	          End If
	        Next
	        ' Increment the base folder counter.
	        lngBaseCount = lngBaseCount + 1
	        ' Get the name of the next folder to process.
	        strBaseFolder = strFolders(lngBaseCount + 1)
	      Wend
	    End With
	
	    ' Return the array of folder names.
	    BuildFolderUrlTree = strFolders
	
	  End Function
	
	4. On the File menu, click Save.
	
	5. On the File menu, click "Close and Return to Microsoft FrontPage".
	
	Step 3 - Run the Sample Macro in FrontPage
	------------------------------------------
	
	Before you run the following Visual Basic macro, open a Web. To run the sample
	macro, follow these steps:
	
	1. In FrontPage, open your Web.
	
	2. On the Tools menu, point to Macro, and then click Macros.
	
	3. In the Macro name list, click SetAllMetaTags, and then click Run.
	
	4. When the macro is finished, a message telling you that the macro is finished
	  appears.
	
	REFERENCES
	==========
	
	For additional information about working with Web Spiders and Robots, click the
	article numbers below to view the articles in the Microsoft Knowledge Base:
	
	  Q205493 FP: How to Use the META Element with Web Spiders and Robots
	
	  Q217103 How to Write a Robots.txt File
	
	Additional query words:
	
	======================================================================
	Keywords          : kbHOWTOmaster 
	Technology        : kbFrontPageSearch kbFrontPage2002 kbFrontPage2000Search kbFrontPage2002Search kbZNotKeyword5
	Version           : :
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
