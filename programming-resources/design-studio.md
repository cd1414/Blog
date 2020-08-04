# Design Studio

* **R&D CRI**
  * New and overridden views or lookups should have the same name with “`<Project Abbreviation>`” appended:
    * “ViewName” + `<Project Abbreviation>` \(eg: ARDepositHistoryFood\)
    * “LookupName” + `<Project Abbreviation>` \(eg: ARTransFood\)
  * We will try to avoid replacing existing interactive views and lookup, instead of using “replace Id” field into the new object, we will call the new view or lookup directly from the C\# class by changing “ViewDefinitionId” or “LookupDefinitionId” properties.
    * Exception: If need to change a lookup that is used in a lot of screens in TRAVERSE, we will keep using “replace id” field.
  * Business Rules: When creating a new business rules, the ConfigRef value should follow the following numbering:

    * AWMS: 4000-4099.
    * CreditCard: 4100-4199.
    * SO Quoting: 4200-4299.
    * Configurator: 4300-4399
    * EDI: 4400-4499
    * Unused: 4500-4999
    * ShopFloor: 5000-5099.
    * Food Base: 5100-5199 – no longer a vertical, but has been given to services.
    * PO Deposit: 5200-5299 – base solution, can probably re-use these menú ids
    * Printing Integration: 5300-5399
    * Tax Integration: 5400-5499
    * FlexPack: 5500-5999.
    * Service Repair \(ACS Master\): 6000-6499.
    * WM Portal: 6000-6099
    * WM Portal-ProcessPro: 6100-6199
    * Mobile Web Projects: 7000-7999 
    * Base Mobile Web \(Mobile\): 7000-7099
    * Service Tech \(Mobile\): 7100-7199    
    * ShopFloor Master\(Mobile\): 7200-7299
    * InstallerX: 10000-10499 

    This numbering will be used also for SysTables and SysColumns entries.
* **Custom Solutions**
  * When creating new Menus for customizations, the script should first check to see if the menu id exists.  If it exists, delete the menu id and recreate using the information in the latest script.  Because we delete the menu, we should try to use menus ending in the 90 sequence.  For example, adding a menu to SO Interactive views should be in the 1250191 – 1250199 range.
  * When creating customized views in Design Studio, the script should first check to see if the view exists by Id.  If it exists, delete the id and recreate using the information in the latest script.  Naming conventions for customized views should contain the base view name followed by “\_custom”.
  * When creating new views in Design Studio, the script should first check to see if the view exists by Id.  If it exists, delete the id and recreate using the information in the latest script.  Naming conventions for new views should follow the base TRAVERSE naming conventions.
  * `<AppId>` + `<Description>` \(eg: ArSampleView\)

