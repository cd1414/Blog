# General Coding

## CheckList

Could find the complete CheckList in the next Link [Programming - CheckList](https://docs.google.com/spreadsheets/d/1fQ-e5abke8Up_YwNcPGYCsGztR2sUwCrS7A_VE5LjuU/edit?usp=sharing)

## Code Snippets

Here you could found some snippets created thinking on the [Traverse developer Snippets](https://osas.aurainteractiva.com/mod/resource/view.php?id=521).

If you have some doubt about how import snippets here a useful [Microsoft Snippets](https://docs.microsoft.com/en-us/visualstudio/ide/walkthrough-creating-a-code-snippet?view=vs-2019)

## Code regions

* Using directives
* Fields
* Constructors
* Overrides
* Public
* Protected
* Private
* Internal
* Static
* Events
* Properties

## Using directives

* Do not use fully qualified namespaces in the code. Declare the namespaces at the top with “using” statement.
  * Group System/Microsoft and TRAVERSE \(project\) namespaces separately.
    * You can use the right click option for ‘Remove and Sort’ using statements.

![](https://github.com/cd1414/OSI-Document-Site/tree/7d1efa9595ae663ba258c75b3cd3235404afd5bf/Programming-Resources/.gitbook/assets/image%20%282%29.png)

## Add folder for each function

![](https://github.com/cd1414/OSI-Document-Site/tree/7d1efa9595ae663ba258c75b3cd3235404afd5bf/Programming-Resources/.gitbook/assets/image.png)

## Events

* When creating an event, provide one private and one public method and keep those together in the ‘Event Region’ 

```csharp
void ParentForm_Shown(object sender, EventArgs e)
{
    try
    {
        this.OnParentForm_Shown(e);
    }
    catch (Exception exception)
    {
        ClientContext.HandleError(exception, this);
    }
}
public virtual void OnParentForm_Shown(EventArgs e)
{
    this.SetProdTypeDescr();
}
```

![Preferences files created](https://github.com/cd1414/OSI-Document-Site/tree/7d1efa9595ae663ba258c75b3cd3235404afd5bf/Programming-Resources/.gitbook/assets/image%20%2811%29.png)

## Comments

* Provide in-line comments when necessary

// TODO: Reference to comment guide

## Design Studio file

DesignRoot and InitExtension members go in a partial class with a file name suffix of “ds.cs”. This is to keep Design Studio related methods separate

![](https://github.com/cd1414/OSI-Document-Site/tree/7d1efa9595ae663ba258c75b3cd3235404afd5bf/Programming-Resources/.gitbook/assets/image%20%2812%29.png)

## Simple Grid Maintenance

For simple grid – only functions, having a TravLayoutControl is unnecessary. The Grid should be placed on the Split Panel base Control \(We need to update the CheckList to remove everything that mentions a LayoutControl\).

Implement the event Load to the Grid Control in order to update the position of the BindingSource instead of filtering the data on the OnLoad Event.

```csharp
this.dgvExtLocationType.Load += new EventHandler(DGvExtLocationType_Load);
void DGvExtLocationType_Load(object sender, EventArgs e)
{
    try
    {
        this.OnDgvExtLocationTypeLoad(e);
    }
    catch (Exception ex)
    {
        ClientContext.HandleError(ex, this);
    }
}
public virtual void OnDgvExtLocationTypeLoad(EventArgs e)
{
    this.gvExtLocationType.UnselectRow(0);
    if (this.HasFindKey())
    {
        int id;
        if (Int32.TryParse(this.GetFindKeyValues<string>()[0], out id))
            this.BindingSource.Position = this.BindingSource.Find(ExtLocationTypeBase.Columns.Id.ToString(), id);
    }
}
```

## Layout.SetFont\(\)

* No longer required for Global 2

## Set Controls Methods \(R&D\)

When you need to customize a base maintenance include separate methods for your project , in this way could be easy to customize and easy to identify.

The name for this methods must include the project name

E.g.

SetFlexPackControls\(\)

## Binding Sources

* Use BindingSource for binding to objects
  * Handle AddingNew event to create new objects
  * Attach binding source to errorProviderBase and TravNavigator

## Try-catch

* Use try-catch blocks to handle exceptions
  * In all data related calls and methods
  * Remember that exceptions do bubble-up
  * Call ClientContext.HandleError\(\) method to show error messages

## Overrides

* Can close method

```csharp
public override bool CanClose()
{
    if (this._provider.Items.IsDirty)
    {
        return (TravMessageBox.Show("canclose", TRAVERSE.Client.Localizer.GetLocalizedString("canclose"), MessageBoxButtons.YesNo) == DialogResult.Yes);
    }
    return base.CanClose();
}
```

* Dispose method to release any added events

```csharp
protected override void Dispose(bool disposing)
{
    if (disposing)
    {
        if (this._btnRunRates != null)
        {
            this.btnRunRates.Click -= new EventHandler(btnRunRates_Click);
            this._btnRunRates.Dispose();
            this._btnRunRates = null;
        }
    }
    base.Dispose(disposing);
}
```

* Save settings and Load Settings methods when creating screen with a grid view to allow user to be able to save their screen preferences

```csharp
/*
*Create a GUID or Function ID with VS (Tools  Create GUID  GUID Format 3 and then Copy.
*/
this._guid = "{6F0FD515-E6A2-4864-8177-515B84359233}";


public override void SaveSettings()
{
  this.dgvTransClient.SaveLayout(this._guid, this.gvMain);
  base.SaveSettings();
}

public override void LoadSettings()
{
  this.dgvTransClient.RestoreLayout(this._guid, this.gvMain);
  base.LoadSettings();
}
/*
* The File created by the settings is stored here C:\Users\[Windows User]\AppData\Roaming\Open Sys6tems, Inc\TRAVERSE\[TRAVERSE User]\[Company]. 
 * AppData is a hidden folder.
*/
```

* Design Root

```csharp
public override object DesignRoot
{
  get
  {
    return this.layoutControlGroup1; 
    //provide the maint layout control or grid control as necessary for the function
  }
}
```

* Init Extension

```csharp
protected override void InitExtension()
{
  this.EntityName = TicketBase.TableName;  
    //name of the entity for the function
    this.Extension.Root = this.layoutControlGroup1; 
    //main layout or grid control
    this.Extension.LayoutRoot = this.travLayoutControl1; 
    //main layout control if any
    //this.Extension.LayoutTabRoot = this.tabbedControlGroup1; 
    //main tab container of the layout control if any
    this.Extension.Navigator = this.travNavigator1; 
    //navigator
}
```

## Creating screens

### New Controls

When creating a brand new screen, add the new control to the project to the project as a **UserControl** and not as a new class. It will create a separate file for all designer code. **Only for new controls,** for customizations use a new class.

![](https://github.com/cd1414/OSI-Document-Site/tree/7d1efa9595ae663ba258c75b3cd3235404afd5bf/Programming-Resources/.gitbook/assets/new_control.png)

![](https://github.com/cd1414/OSI-Document-Site/tree/7d1efa9595ae663ba258c75b3cd3235404afd5bf/Programming-Resources/.gitbook/assets/image%20%283%29.png)

Example for adding code to a new screen \(to make it work with Design Studio\)

* In the constructor, add a section to check wheter user is in Design Studio

```csharp
try
{
  this.InitializeComponent();
  if (DevEnvironment.InVSDesigner) //add this for Design Studio
      return;

  //code for bindingsource, adding events, etc here
  [LayoutControlName].SetFont();
  BindingSource = this.binSrc[ParentEntityName];     
}
catch (Exception ex)
{
  ClientContext.HandleError(ex, this);
}
```

### Customized controls

* Don't change anything in the screen layout using design mode from VS.
* Do not open a customized control in design mode. If, for any reason you need to open it in design mode dure development, be sure the .resx file 'InitializeComponent\(\)' code that will be generated, got deleted.

![](https://github.com/cd1414/OSI-Document-Site/tree/7d1efa9595ae663ba258c75b3cd3235404afd5bf/Programming-Resources/.gitbook/assets/image%20%281%29.png)

## Auto generated IDs

Ensure that the constructors supress entitty events before assigning ID values, use the IdGen.GetLongId\(\) when generating a value for int64/long ID value. It returns a more granular value that is less likely to be duplicated.

```csharp
if(!this.SupressEntityEvent)
    this.Id = Id.Gen.GetLongId(null);
```

## Provider Child classes

The access modifier of child entity providers should be internal. This prevents the parent/child relationship from be bypassed.

## TRAVERSE Utilities

To compare values use the TRAVERSE core utitlities: AreEqual, IsLessThen, IsLessThenOrEqual for TRAVERSE.Core.

```csharp
StringHelper.AreEqual(string1, string2);
StringHelper.IsLessThen(string1, string2);
StringHelper.IsLessThenOrEqual(string1, string2);
StringHelper.Truncate(string1, length);
```

## List Factory

Avoid using cached copies of secondary object references. There are many older examples that use a cached copy, but it can cause issues with stale/outdated information. Instead of using the EntityProvider.GetEntity to retrieve the object and holding it in a variable, please use a ListFactory to retrieve the object each time it is needed. The ListFactory objects are updated by the base providers when a process the current session makes a change to an entity. The performance cost of retrieving the object from the cached list in the ListFactory is minimal.

* Retrieve all the data for cache 

```csharp
ListFactory.CreateList<Entity, EntityProvider>(CompanyId);
```

* Use Linq to filter the results

```csharp
ListFactory.CreateList<Entity, EntityProvider>(CompanyId).find(filter);
```

## Rounding numeric properties

It is necessary to apply rounding to the BL properties, in addition to the formatting that is applied in the UI, to ensure that appropriately rounded values are written to the database. Add overrides for numeric values that we would typically round \(such as Amounts, Rates, Percentages, Quantities, etc.\).

```csharp
/// <summary>
/// Gets or sets the Salary property.
/// Overrides base to implement rounding
/// </summary>
public override decimal Salary 
{
    get 
    {
        Return Rounding.Round (base.Salary, Rounding.RoundingType.Amount);
    }
    set 
    {
        base.Salary = value;
    }
}

/// <summary>
/// Gets or sets the HourlyRate property.
/// Overrides base to implement rounding
/// </summary>
public override decimal HourlyRate 
{
    get 
    {
        ReturnRounding.Round (base.HourlyRate, Rounding.RoundingType.Rate);
    }
    set 
    {
        base.HourlyRate = value;
    }
}
```

