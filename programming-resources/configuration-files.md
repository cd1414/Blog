# Configuration Files

* Update TaskPane.config file when customizing a screen that has a Task Pane available \(currently Sales Order, Purchase Order, Accounts Receivable and Accounts Payable transactions\) to call the task pane from the custom assembly / plugin\(base uses TaskPaneMain.config\).
  * Example for revising config file to make base Task Pane work with custom Sales Order
    * **R&D CRI**
      * \`&lt;add key= "OSI..Client.SalesOrder. TransactionOrderFoodPlugin,

        OSI..Client.SalesOrder" value="TRAVERSE.TaskPane.SalesTaskPane, TRAVERSE.TaskPane.Transaction"&gt;&lt;/add&gt;\`
    * **Custom Solutions**
      * \`&lt;add key= "OSI..Client.SalesOrder.CustomTransactionOrderControlPlugin,

        OSI..Client.SalesOrder" value="TRAVERSE.TaskPane.SalesTaskPane, TRAVERSE.TaskPane.Transaction"&gt;&lt;/add&gt;\`
* Add code to include all overridden forms/screens and new forms/screens to DSTasks.config file\(base uses DSTasksMain.config\).
  * Example for adding a customized SO Transaction screen:
    * **R&D CRI**
      * `<add key=”SO Transaction - Food” value=” TransactionOrderFoodPlugin, OSI.<Project Abbreviation>.Client.SalesOrder.dll”></add>`
    * **Custom Solutions** 
      * `<add key=”SO Transaction - Custom” value=”CustomTransactionOrderControlPlugin, OSI.<Client Abbreviation>.Client.SalesOrder.dll”></add>`
  * Example for adding a customized SO Acknowledgement form:
    * **R&D CRI**
      * `<add key=”SO Acknowledgement-Food” value=”OrderAcknowledgementFoodPlugin, OSI.Project.Client.SOPrinting.dll”></add>`

