---
description: 'Recommendations to get a code: clean, easy to maintenance and customizable.'
---

# Clean Code

## //TODO: Add clean code meaning

## Meaningful Names

* Names should be self-descriptives.
* Avoid names without sense like  'a', 'b', 'x'.
* Need to be searcheable.

Bad examples

```csharp
public virtual decimal Salary(int x)
{
    //Do something
}

public virtual List<EmployeeGroups> Employeegroups(int i)
{
    //Do something
}
```

Good examples

```csharp
public virtual decimal GetSalaryByEmployeeId(int id)
{
    //Do something
}

public virtual List<EmployeeGroups> GetEmployeeGroups(int employeeId)
{
    //Do something
}
```

## Comments in Code

Comments in the code are a good thing, but applied in the incorrect way could convert it in a mess and have the contract result.

Good comments have to be

* Significant.
* Have a purpose
* Help to understand the reason of the code.

**Bad comments**

```csharp
/*
set the value of the age integer to 32
*/
int age = 32;
```

```csharp
//for(int i=0; i< 10; i++)
//{
    Products[0].Price = discountedPrice;
//}
```

## Visual Studio Task List \(TODOS\)

Visual studio offers a tag to be added to 'mark' parts of the code to be review later or need to be improved in some point of the process a type of 'TODO list' and this tool is called the [Task List](https://docs.microsoft.com/en-us/visualstudio/ide/using-the-task-list?view=vs-2017) and could be added in any place into your code, the idea of use this is check this task and Its available even in Visual Studio 2008, and you could easy found it in the menu View

```csharp
// TODO: Load state from previously suspended application
```

![Task List Menu](https://github.com/cd1414/OSI-Document-Site/tree/7d1efa9595ae663ba258c75b3cd3235404afd5bf/Programming-Resources/.gitbook/assets/image%20%285%29.png)

![Task List](https://github.com/cd1414/OSI-Document-Site/tree/7d1efa9595ae663ba258c75b3cd3235404afd5bf/Programming-Resources/.gitbook/assets/image%20%287%29.png)

## If statements

A bad practices about if statements is nested several in one statement, try to add all the unexpected values in the top and the expected results in the bottom. In this way the code is more easy to debug and try less bad paths.

Bad example

```csharp
public virtual CustomerShipTo GetCustomShipToInfo()
{
    if(this.currentOrder != null)
    {
        if(this.currentOrder.CustomerInfo != null)
        {
            if(this.currentOrder.CustomerInfo.ShipToInfo != null)
            {
                return this.currentOrder.CustomerInfo.ShipToInfo;
            }
        }

        else if(this.currentOrder.ShipToInfo != null)
        {
            return this.currentOrder.ShipToInfo;
        }
    }
    return null;
}
```

Good example

```csharp
public virtual CustomerShipTo GetCustomShipToInfo()
{
    if((this.currentOrder == null) || ((this.currentOrder.CustomerInfo == null) && (this.currentOrder.ShipToInfo == null)))
        return null;

    if(this.currentOrder.CustomerInfo != null)
        return this.currentOrder.CustomerInfo.ShipToInfo;

    return this.currentOrder.ShipToInfo;
}
```

## Segmented methods

Each method should only do one thing, if you need to add more functionalitites segmented this in several methods. This is more easy to maintenance and customize.

```csharp
public virtual void PrintItemLabel()
{
    try
    {
        if(this.CurrentItem == null)
            throw new exception("Nothing to print");

        if(!this.CurrentItem.IsActive)
            throw new exception("This item couldn't be printed");

        if(this.CurrentItem.CurrentLocation.LocId != this.CurrentCustomer.DefaultLocation.LocId)
            throw new exception("This item couldn't be printed from your location");

        // Add code to print label

        // Set status for the current order
        if(this.CurrentOrder.Status == "Not-printed")
            this.CurrentOrder.Status = "Printed";
        else
            CurrentOrder.Status = "Re-Printed";   
    }
    catch(Exception ex)
    {
        //manage exception
    }
}
```

If someone need to add some new status or avoid this assignment need to override to do copy past of almost all the code to change a simple line.

A better option could be like this, the PrintItemLabel do only one thing 'call to the rest of methods', each method did one part of the functionality an each one could be customized in an easy way.

```csharp
public virtual void PrintItemLabel()
{
    try
    {
        this.ItemValidToPrint();
        this.PrintLabel();
        this.UpdateOrderStatus();
    }
    catch(Exception ex)
    {
        //manage exception
    }
}

protected virtual void ItemValidToPrint()
{
    if(this.CurrentItem == null)
        throw new exception("Nothing to print");

    if(!this.CurrentItem.IsActive)
        throw new exception("This item couldn't be printed");

    if(this.CurrentItem.CurrentLocation.LocId != this.CurrentCustomer.DefaultLocation.LocId)
        throw new exception("This item couldn't be printed from your location");
}

protected virtual void UpdateOrderStatus()
{
    if(this.CurrentOrder== null)
        return;    
    if(this.CurrentOrder.Status == "Not-printed")
        this.CurrentOrder.Status = "Printed";
    else
        CurrentOrder.Status = "Re-Printed";  
}
```

