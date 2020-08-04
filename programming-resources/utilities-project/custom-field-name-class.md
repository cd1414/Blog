---
description: >-
  It will provide access to all Custom Field names of the project. When need to
  use any CF just need to use the public property from here.
---

# Custom Field Name Class

Example:  
`this.CurrentRouting.FindCustomValue<[Type]>(CustomFieldNames.FORMULA_ID, string.Empty)`;

```csharp
namespace OSI.FlexPack.Business.Utilities
{
    public static class CustomFieldNames
    {
        public const string ASSEMBLY_ID = "Assembly ID";
        public const string BLIND_SHIP = "Blind Ship";
        public const string ESTIMATE = "Estimate #";
        public const string FINISHED = "Finished";
        public const string FORMULA_ID = "Formula ID";
        public const string PRODUCTION_WO_NUMBER = "Production WO Number";
        public const string RELEASE_ID = "Release ID";
        public const string RELEASE_NUMBER = "Release Number";
        public const string REVISION = "Revision";
    }
}
```

