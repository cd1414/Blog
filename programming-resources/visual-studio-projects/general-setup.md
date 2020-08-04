# General Setup

## Traverse Standard version

* Visual Studio 2008.
* Microsoft SQL Server 2016 or higher.
* Business Intelligence 2005.

## Traverse Global version

* Visual Studio 2012 or higher.
* Microsoft SQL Server 2016 or higher.

## Project setup

* Create one solution containing all customizations being done for a specific project.
* If a customization is to modify an existing process / screen / report, follow standard TRAVERSE groupings of projects.

**Examples**

* New projects to add custom fields to Packing Slip, Packing List and Invoice
  * One solution
  * Projects for each of the following
    * Sales Order Transaction override \(TRAVERSE.Client.SalesOrder\).
    * Report print override \(TRAVERSE.Client.SOPrinting\).
    * History Invoice printing override \(TRAVERSE.Client.ARHistory\).
* If the customization requires modifying multiple tiers \(data, business. client\) of the object, create a new project for each tier modified.
* Build folder \(in the properties of the project\) should be set to bin/debug. This will result in the built dll being created in the bin/debug or release folder of the project you are working in.

