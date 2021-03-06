---
layout: page
title: "Q130864: PRB: Form with One-to-Many View Does Not Update Parent Records"
permalink: /kb/130/Q130864/
---

## Q130864: PRB: Form with One-to-Many View Does Not Update Parent Records

{% raw %}

	Article: Q130864
	Product(s): Microsoft FoxPro
	Version(s): 3.00 5.00 |3.00b
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 5.0, 6.0 
	- Microsoft Visual FoxPro for Macintosh, version 3.0b 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A form with one-to-many data that is based on a view may not refresh properly
	when the data in a parent record changes. The correct data displays in the
	record where the data was changed, but other child records for the parent show
	the old version of the data. This behavior occurs even if a TABLEUPDATE() or a
	ThisForm.Show command is issued.
	
	CAUSE
	=====
	
	This is by design. The data in the view is the result of a query that was
	performed when the form was initially loaded. The query creates a cursor in
	memory with a copy of the data from the source tables. During the form load, a
	thermometer bar appears demonstrating the progress of this query.
	
	When a TABLEUPDATE() command is issued, the changes are sent to the source
	tables. The child records in the view are not updated because there is no
	dynamic link between the view and the source table. These records do not display
	the new information until the query is run again.
	
	RESOLUTION
	==========
	
	Here are two possible solutions:
	
	- Base the form on the source tables instead of a view. This is possible only
	  if the view is completely comprised of local tables.
	
	  -or-
	
	- Issue a REQUERY() function after each TABLEUPDATE().
	
	Choose the best solution for your situation by weighing the advantages of using a
	view with the performance hit caused by the REQUERY() function.
	
	You can place the REQUERY() function in the show or refresh event of the form.
	This causes the query to be performed each time a Form.Show or Form.Refresh is
	issued, so the most recent data is always displayed. Alternately, you can place
	the REQUERY() function in all events that use a TABLEUPDATE() command, such as
	the InteractiveChange event of a grid or the Click event of a command button.
	
	MORE INFORMATION
	================
	
	When using Visual FoxPro for the Macintosh 3.0b the expression "right- click"
	means pressing the Control button on the keyboard while clicking.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Issue the following command to open the Tastrade database:
	
	     OPEN DATABASE c:\vfp\samples\mainsamp\data\tastrade
	     MODIFY DATABASE
	
	2. Right-click the gray background of the Database Designer. Choose New Local
	  View. Click the New View button.
	
	3. When the "Add Table or View" dialog box opens, select the customer Table and
	  then click the Add button to add the table to the view. Similarly, add the
	  Orders and Order_Line_Items tables to the view. Close the dialog box.
	
	4. In the Fields tab, add the following fields to the view:
	
	     Customer.Customer_id, Customer.company_name, Orders.customer_id,
	     Orders.order_id, Orders.order_date, Order_line_items.order_id,
	     Order_line_items.quantity.
	
	5. In the Update Criteria tab, click the Send SQL Updates box. Make sure all
	  tables are selected from the Table list box. Click in the key column to
	  select the key fields for each table. Make sure that only the key column
	  (Customer.customer_id, Orders.customer_id, and Order_Line_Items.order_id)
	  fields are selected as key fields. Click the Update column, to select all
	  other fields. Click the SQL WHERE clause "Key Fields Only" and the Update
	  using "SQL Update" buttons.
	
	6. Save the view as MyView.
	
	7. Create a new form. From the View menu, choose Data Environment. Use a
	  right-click to select Add Table. In the "Add Table or View" dialog box,
	  select to display Views and select the Add the view you created in step 6.
	  Click the ADD button to add the table to the Data Environment of the Form and
	  then close the dialog box.
	
	8. In the Data Environment of the Form, select the view you just added.
	  Right-click, and select Properties.
	
	9. Set the BufferModeOverride property to 3 - Optimistic Row Buffering.
	
	10. Click the title of the view in the data environment, and drag it onto the
	  form. A grid should appear.
	
	11. Add a command button with the following code in the click event:
	
	      =TABLEUPDATE()
	
	12. Save and run the form. Change the company name for one of the companies that
	  has more than one record. Click the command button.
	
	13. Close the form and reopen it in the Forms Designer. Add the following line
	  of code after the =TABLEUPDATE() in the command button created in step 11:
	
	      =REQUERY()
	
	14. Rerun the form and change the company name back to its original value. The
	  updated data should show for all records after the command button is
	  clicked.
	
	REFERENCES
	==========
	
	For more information, please see Chapter 8 of the Microsoft Visual FoxPro
	Developer's Guide.
	
	Additional query words: vFoxMac VFoxWin
	
	======================================================================
	Keywords          :  
	Technology        : kbHWMAC kbOSMAC kbVFPsearch kbAudDeveloper kbVFP300bMac kbVFP300 kbVFP500 kbVFP600
	Version           : 3.00 5.00 |3.00b
	
	=============================================================================
	

{% endraw %}
