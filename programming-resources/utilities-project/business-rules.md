---
description: >-
  This class should have also static methods for all business rules, so they can
  be used in all project.
---

# Business Rules

* Create a static class called BusinessRuleValue.cs
* New Rules should follow TRAVERSE naming conventions
  * “Get” + `<RuleName>` \(eg: GetPrecQty\)
* Only the method \(with a 'CompId' parameter\) is needed

  ```csharp
  namespace OSI.FlexPack.Business.Utilities
  {
    public static class BusinessRuleValue
    {
        public static int GetPrecPerc(string compId)
        {
            return ConfigurationValueProvider.GetRule<int>(AppId.SM, ConfigurationValue.PrecPercent, compId);
        }

        public static int GetPrecQty(string compId)
        {
            return ConfigurationValue.GetRule<int>(AppId.SM, ConfigurationValue.PrecQty, compId);
        }

        public static int GetPrecUnitPrice(string compId)
        {
            return ConfigurationValue.GetRule<int>(AppId.SM, ConfigurationValue.PrecUPrice);
        }
    }
  }
  ```

