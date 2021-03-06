---
layout: page
title: "Q171849: FIX: Debugger Hangs When Very Long STL Symbol in Watch Window"
permalink: /kb/171/Q171849/
---

## Q171849: FIX: Debugger Hangs When Very Long STL Symbol in Watch Window

{% raw %}

	Article: Q171849
	Product(s): Microsoft C Compiler
	Version(s): 97
	Operating System(s): 
	Keyword(s): kbVS97sp2fix
	Last Modified: 17-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Integrated Debugger, included with:
	   - Microsoft Visual Studio 97 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The debugger hangs when an STL object with very long symbol name is viewed in
	the Watch Window and expanded. You have to close Developer Studio Task Manager
	and restart. The sample program in the MORE INFORMATION section demonstrates
	this behavior.
	
	CAUSE
	=====
	
	This behavior occurs because the debugger currently has a limit of 255
	characters for symbols.
	
	RESOLUTION
	==========
	
	Reduce the size of the mangled symbol names. You can do this by shortening the
	names of classes and class members. You can also shorten class names of classes
	by using #define.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug has been fixed in Visual Studio 97 Service
	Pack 2.
	
	For more information on the Visual Studio 97 Service Pack 2, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q170365 INFO: Visual Studio 97 Service Packs - What, Where, and Why
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	Build the following sample code as a Console application:
	
	     #include <windows.h>
	     #include <map>
	     #pragma warning (disable : 4786 )
	     using namespace std;
	     template<typename Type>
	     class SomeReallyLongSymbolName
	     {
	         public:
	           SomeReallyLongSymbolName(Type var){m_Type = var;}
	           SomeReallyLongSymbolName(){}
	           void func(Type var){m_Type = var;}
	           Type m_Type;
	     };
	     SomeReallyLongSymbolName<int> intObject(0);
	     typedef map< DWORD, SomeReallyLongSymbolName< DWORD> >
	     STLTypeWithLongName ;
	     STLTypeWithLongName  STLObjectWithLongName;
	     int main()
	     {
	        intObject.func(1);
	        return 0;
	     }
	
	After the build is complete, start the debugger by pressing the F10 key. In the
	Watch Window, enter the two variable names, intObject and STLObjectWithLongName.
	You will be able to expand the intObject variable. However, when you try to
	expand the STLObjectWithLongName variable, the Debugger will hang.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbVS97sp2fix 
	Technology        : kbVCsearch kbAudDeveloper kbIntegratedDebugger
	Version           : 97
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
