# SQL Server Objects

* New Stored Procedures and Views should follow TRAVERSE naming conventions
  * **R&D CRI**
    * “trav\_”`<AppId>`+`<Description>`+`<Project Abbreviation>`”\_proc” \(eg: trav\_ApSampleFood\_proc\)
    * “trav\_”`<AppId>`+`<Description>`+`<Project Abbreviation>` “\_view” \(eg: trav\_ApSampleFood\_view\)
  * **Custom Solutions**
    * “trav\_”`<AppId>`+`<Description>`”\_proc” \(eg: trav\_ApSampleStoredProc\_proc\)
    * “trav\_”`<AppId>`+`<Description>`“\_view” \(eg: trav\_ApSampleView\_view\)
* **R&D CRI:** Custom Stored Procedures and Views should have the same name as the base TRAVERSE object with “” \(R&D CRI team\) or “Custom”\(Custom Solutions team\) appended to the Description.
  * **R&D CRI** eg: trav\_ApPreparePaymentFood\_proc
  * **Custom Solutions** eg: trav\_ApPreparePaymentCustom\_proc.
* Tables should follow base TRAVERSE naming conventions
  * “tbl”`<AppId>`+`<Description>` \(eg: tblApSampleTable\)
* When creating scripts to add data via a server update, the script should be named the same as the table where the data is being inserted \(eg: tblSmMenuCustom\)
* When creating sql objects should be based on “Script Templates.zip” , that can be found in the following link [https://osas.aurainteractiva.com/mod/resource/view.php?id=383](https://osas.aurainteractiva.com/mod/resource/view.php?id=383).
* General coding
  * Try to avoid defaults on SP parameters.  The calling process/data generator should provide the necessary default values when needed.  It's a necessity to use defaults when we implement a change and need to maintain backward compatibility, but having a default can cause difficulty when trying to debug an issue.
  * Non-Key Text \(nvarchar\) columns in temporary tables should be defined with a length of 255 to support user extensibility.  Users can modify the length of descriptions and other text based data columns.  Using the larger definition in the temporary tables prevents truncation errors from occurring when they choose to do so.
  * Avoid unused parameters in new procedures.  We cannot remove extra parameters once the SP is released as it would change the public signature and potentially break custom code implemented for customers.

