---
layout: page
title: "Q137182: PRB: List Box Shows .F. from an Empty Array"
permalink: /kb/137/Q137182/
---

## Q137182: PRB: List Box Shows .F. from an Empty Array

{% raw %}

	Article: Q137182
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 12-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A list box on a form displays .F. when the RowSource property is set to a
	dimensioned array, as opposed to an array initialized from an SQL statement, a
	view, or a remote view.
	
	Furthermore, when your redimension the array and pass a value to the new element,
	the list box does not reflect the new value.
	
	CAUSE
	=====
	
	Arrays, by nature, have a default logical (.F.) data type. If the list box is
	not properly refreshed, it will not reflect the current values in the array.
	
	RESOLUTION
	==========
	
	In the Init event for the form, change the data type to match the data being
	passed to it. For example, if you are passing a character string to the first
	element of the array, issue this command:
	
	     thisform.test(1)=""   && No spaces between the quotation marks
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	Make the array a property of the form. Open your form in the Form Designer. On
	the Form menu, click New Property. Then type the name of the array, and make
	sure you give it at least one element or row as in this example:
	
	     test(1)
	
	Then add the following code to the Load event:
	
	     thisform.test(1)=""   && This assigns the data type to character.
	
	If you run the form at this time, you will observe that the list box is blank. If
	you had not set the data type to character in this example, you would have seen
	the familiar .F. value displayed.
	
	You can test this without a form by dimensioning an array from the Command
	window:
	
	     DIMENSION test(1)    && The parenthesis are necessary as well as at
	                             least a length of 1.
	
	Open the Debug window (on the Tools menu, click Debug Window). In the left
	partition of the Debug window, type the following lines in order:
	
	     test(1)
	     ALEN(test)
	     EMPTY(test)
	
	The values for these are .F., 1, and .T. respectively. The first line shows you
	the default data type. The second shows you the length or number of elements (or
	number of rows in a single-column array) in the array. The third shows you the
	results from the evaluation of whether the element is empty or not.
	
	In the Command window, type:
	
	     test(1)=""
	
	The value in the debug window for test(1) changes to "". This tells you that it
	is now a character data type with no string assigned to it. Now you can apply
	this to a form in Visual FoxPro.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a form. Accept the default form and object names (form1, text1, list1,
	  and so on).
	
	2. Add a text box, a list box, and a command group to the form. The order they
	  are added is not important.
	
	3. On the Form menu, click New Property. Then type test(1) in the Name field,
	  and then click OK. This makes the array a property of the form.
	
	4. Right-click the form, and click Properties.
	
	  a. In the Properties window, click Methods, and then double-click Init.
	
	  b. In the open window, type:
	
	  " thisform.test(1)="" && To assign the data type to character."
	  (without the quotation marks)
	
	5. Select the list box from the Object menu in the Properties window.
	
	  a. Click the Data tab.
	
	  b. Type "thisform.test" (without the quotation marks) as the RowSource to
	     establish the source for the data for each row in the list box.
	
	  c. Set the RowSource Type to 5 - Array. This establishes the type of source
	     for the values in the list box.
	
	6. On the Object menu in the Properties window, click Commandgroup1. Click the
	  All tab, and change the ButtonCount to 3 from the default of 2.
	
	  a. Click the form. Then select the Commandgroup1 object on the form, and
	     stretch the object vertically to reveal all three buttons.
	
	  b. From the Object menu in the Properties window, select Command1 under
	     Commandgroup1.
	
	  c. In the Properties window, click the All tab, and select the Caption
	     property. Type "UPDATE" (without the quotation marks), and press ENTER.
	
	  d. Click the Methods tab, double-click the Click event, and enter this code:
	
	        IF EMPTY(thisform.test(1))
	           thisform.test(1)=thisform.text1.value
	        ELSE
	           x=ALEN(thisform.test)
	           x=x+1
	           DIMENSION thisform.test(x)
	           thisform.test(x)=thisform.text1.value
	           thisform.list1.requery
	        ENDIF
	        thisform.text1.value=""
	        thisform.text1.setfocus
	
	     This code checks for a value in test(1). If it is empty, the code passes
	     the value from text1 to test(1), the first element of the array.
	     Otherwise, it gets the length of the array, adds 1 to it, redimensions the
	     array to the new length, and passes the value of text1 to it. To refresh
	     the array, it uses the requery method in the list1 box. Finally, it sets
	     the value in text to "" (blank) and returns to text1.
	
	7. On the Object menu in the Properties window, click Command2 under
	  Commandgroup1.
	
	  a. Click the All tab, and type "SORT" (without the quotation marks) in the
	     Caption property.
	
	  b. Click the Methods tab, double-click the Click event, and enter this code:
	
	         =ASORT(thisform.test)    && Sorts the values in the array
	        thisform.text1.value=""  && Sets the value of text1 to ""
	        thisform.text1.setfocus  && Puts the cursor back in text1
	        thisform.list1.refresh   && Refreshes the list box
	
	8. On the Object menu in the Properties window, click Command3 under
	  Commandgroup1.
	
	  a. Click the All tab, and type "EXIT" (without the quotation marks) in the
	     Caption property.
	
	  b. Click the Methods tab, double-click the Click event, and enter this code:
	
	        thisform.release   && Clears the form from memory and the screen
	
	9. Click the red exclamation mark on the Standard toolbar to run the form. Click
	  Yes if prompted to save changes.
	
	  NOTE: When the form came up on the screen, the list box was blank. If you had
	  not put the line test(1)="" in the Init event of the form, you would see a
	  .F. in the list box.
	
	10. Enter your last name in the Text1 box, and click UPDATE. Your last name
	  should appear as the first item in the list box.
	
	11. Enter your first name in the Text1 box, and click UPDATE. Your first name
	  should appear as the first item in the list box.
	
	12. Enter your middle name in the Text1 box, and click UPDATE. Your middle name
	  should appear as the first item in the list box.
	
	13. Click the SORT button. You will see the names sorted in alphabetical order.
	
	14. When you are finished, click EXIT. Your form will disappear.
	
	Additional query words: VFoxWin
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300
	Version           : WINDOWS:3.0
	
	=============================================================================
	

{% endraw %}
