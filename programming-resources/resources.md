---
description: >-
  To facilitate the translation process and optimize the source code, for big
  projects we use a resources file.
---

# Resources

It file should contain:

* All messages that can be reusable for other projects into solution.
* Business Rules Caption.
* New Applications.
* Labels for Reports.
* The field names for column error messages in case of new entities.
* Plugin Descriptions.

We try use methods that can be used in the future, to do this, we use parameters and string.Format structures.

Examples:

![Resources1.resx](https://github.com/cd1414/OSI-Document-Site/tree/7d1efa9595ae663ba258c75b3cd3235404afd5bf/Programming-Resources/.gitbook/assets/image%20%2815%29.png)

![Resources1.resx](https://github.com/cd1414/OSI-Document-Site/tree/7d1efa9595ae663ba258c75b3cd3235404afd5bf/Programming-Resources/.gitbook/assets/image%20%284%29.png)

**Appropriate way to call resources**

* If it called is from Entity Layer\(Business\), use Localization.GetLocalizedString\(\).
* If it called is from Client Layer, use Localizer.GetLocalizedString\(\).
* For messages, use TravMessageBox\(ID, text, …\), where you would pass the resource ID as the “ID” parameter, e.g. TravMessageBox.Show\(“ConfigExistsMessage”, ...\)

Other messages like: server queries or class own messages, should be in the resources file for the current project.

![Resources1.resx](https://github.com/cd1414/OSI-Document-Site/tree/7d1efa9595ae663ba258c75b3cd3235404afd5bf/Programming-Resources/.gitbook/assets/image%20%289%29.png)

New resources file steps:

* Create a new project for resources file, name guideline \(OSI..Resources\)
* Add new Resources File called “Resource1.resx”

![](https://github.com/cd1414/OSI-Document-Site/tree/7d1efa9595ae663ba258c75b3cd3235404afd5bf/Programming-Resources/.gitbook/assets/image%20%2810%29.png)

* In install files root create a new folder called “ResourceSet” \(Install\ResourceSet\), and put here the dll file for new resources project.

![Resources Folder](https://github.com/cd1414/OSI-Document-Site/tree/7d1efa9595ae663ba258c75b3cd3235404afd5bf/Programming-Resources/.gitbook/assets/image%20%2814%29.png)

* Appropriate way to call this resource is Resources.\[ResourceName\]

