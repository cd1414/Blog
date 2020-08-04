---
description: >-
  TRAVERSE Framework have some functionality that are used to handle Custom
  Fields.
---

# Handling Custom Fields in C\#

Here are some of those:

* Get value of Custom Field value from an entity:

  ```csharp
  this.CurrentDetail.FindCustomValue<int>(CustomFieldNames.ESTIMATE, 0);
  ```

* Assign custom field value to an entity:

  ```csharp
  this.CurrentDetail.AssignCustomValue(CustomFieldNames.PRODUCTION_WO_NUMBER, releases.OrderNo);
  ```

* And there is also an event that will be trigger when any custom field value is changed by the user \(it will be the equivalent of PropertyChanged event, but it is only for Custom Fields\):

  ```csharp
   this.CustomValueChanged += new EventHandler<CustomValueEventArgs>(this.ReceiptAWMSFPControl_CustomValueChanged);

   void ReceiptAWMSFPControl_CustomValueChanged(object sender, CustomValueEventArgs e)
        {
            try
            {
                this.OnReceiptAWMSFPControlCustomValueChanged(e);
            }
            catch (Exception)
            {
                ClientContext.HandleError(ex, this);
            }
        }

        public virtual void OnReceiptAWMSFPControlCustomValueChanged(CustomValueEventArgs e)
        {
            if (e.Field.Name.Equals(CustomFieldNames.ROLL_LENGTH))
            {
                if (this.CurrentReceipt.RcptKey == this.CurrentDetail.RcptKey)
                {
                    this.CurrentReceipt.AssignCustomValue(CustomFieldNames.ROLL_LENGTH, e.Value.ToString());
                }
            }
        }
  ```

* AssemblyListCustom.xml: Base XML file to use when building Server Update
* Document on Source Control branching procedures

