# DevExpress Reporting Projects

* General setup
  * Version standard is to use DXperience-8.1.1
* General coding
  * When creating or customize a report.
    * Override the CreateDataGenerator method   

```text
    Example:

  ```csharp
    protected override void CreateDataGenerator()
    {
        this.DataGenerator = Base.LoadDataGenerator<LocationData>(this.CompId);
    }
  ```
```

