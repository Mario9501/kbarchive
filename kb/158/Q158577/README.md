---
layout: page
title: "Q158577: STL Sample for the set::max_size Function"
permalink: /kb/158/Q158577/
---

## Q158577: STL Sample for the set::max_size Function

{% raw %}

	Article: Q158577
	Product(s): Microsoft C Compiler
	Version(s): winnt:4.2,5.0,6.0
	Operating System(s): 
	Keyword(s): kbcode kbVC420 kbVC500 kbVC600 kbDSupport
	Last Modified: 07-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, versions 4.2, 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Professional Edition, versions 4.2, 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following sample code illustrates how to use the set::max_size STL function
	in Visual C++.
	
	MORE INFORMATION
	================
	
	Required Header
	---------------
	
	     <set>
	
	Prototype
	---------
	
	     template<class _K, class _Pr, class _A>
	     class set {
	     public:
	     // Function 1:
	
	        size_type max_size() const;
	
	     }
	
	NOTE: The class/parameter names in the prototype may not match the version in the
	header file. Some have been modified to improve readability.
	
	Description
	-----------
	
	The max_size function is used to determine the maximum number of elements the
	controlled sequence can contain.
	
	Sample Code
	-----------
	
	  ////////////////////////////////////////////////////////////////////// 
	  // 
	  // Compile options needed: -GX
	  // 
	  // SetMax_size.cpp:
	  //      Illustrates how to use the max_size function to determine how
	  //      many elements the controlled sequence can contain.
	  // 
	  // Functions:
	  // 
	  //    max_size     Returns the maximum number of elements the controlled
	  //                 sequence can contain.
	  // 
	  // Written by Derek Jamison
	  // of Microsoft Technical Support,
	  // Copyright (c) 1996 Microsoft Corporation. All rights reserved.
	  ////////////////////////////////////////////////////////////////////// 
	
	  #pragma warning(disable:4786)
	
	  #include <set>
	  #include <iostream>
	  #include <assert.h>
	  using namespace std;
	
	  #if _MSC_VER > 1020   // if VC++ version is > 4.2
	     using namespace std;  // std c++ libs implemented in std
	     #endif
	
	  typedef set<int,less<int>,allocator<int> > SET_INT;
	
	  void main() {
	
	    SET_INT s1;
	
	    cout << "s1.max_size() returned ";
	    cout << s1.max_size() << endl;  // 1073741823 [value may vary]
	    for (int x=0;(x<1000 && x<s1.max_size());x++)
	
	     assert(s1.insert(x).second);
	
	    cout << "s1.size() returned ";
	    cout << s1.size() << endl; // 1000
	  }
	
	Program Output
	--------------
	
	  s1.max_size() returned 1073741823
	  s1.size() returned 1000
	
	REFERENCES
	==========
	
	Visual C++ Books Online: Visual C++ Books; C/C++; Standard C++ Library Reference
	
	Additional query words: STL STLSample max_size string
	
	======================================================================
	Keywords          : kbcode kbVC420 kbVC500 kbVC600 kbDSupport 
	Technology        : kbVCsearch kbAudDeveloper kbVC420 kbVC500 kbVC600 kbVC32bitSearch kbVC500Search
	Version           : winnt:4.2,5.0,6.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
