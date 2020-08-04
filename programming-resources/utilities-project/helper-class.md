---
description: >-
  This class contain public static methods that could be reusable in different
  places into the solution,it allows optimize the source code and facilitate the
  maintenance and access to them.
---

# Helper Class

```csharp
namespace OSI.FlexPack.Business.Utilities
{
    public static class Helper 
    {
        public static string GetEnumDescription(Enum enumeration)
        {
            DescriptionAttribute attribute = EntityHelper.GetAttribute<DescriptionAttribute>(enumeration);
            return (attribute != null) ? attribute.Description : Localization.GetLocalizedString(enumeration, enumeration.ToString());
        }

        public static string BuildKeyValuePair(params Enum[] enumeration)
        {
            if (enumeration == null || enumeration.Count() == 0)
            {
                return string.Empty;
            }
            return string.Join(";", (from x in enumeration
            select string.Join(";", new string[2]
            {
                x.ToString("D"),
                GetEnumDescription(x)
            })).ToArray());
        }
    }
}
```

