# Naming Conventions

## **R&D CRI**

* Solutions
  * &lt; **Project Abbreviation** &gt; + Code.sln \(All non-reporting service projects\)
  * &lt; **Project Abbreviation** &gt; + Report.sln.
* Projects/Assemblies
  * Client: TRAVERSE.&lt; **Project Abbreviation** &gt; + .Client + .&lt; **Description** &gt;
  * Business: TRAVERSE. &lt; **Project Abbreviation** &gt; + .Business + .&lt; **Description** &gt;
  * Data: TRAVERSE. &lt; **Project** **Abbreviation** &gt; + .Data _\*\*_+ .&lt; Description &gt;
* Namespace
  * Client/Business: Same as Assembly Name for 
  * Data: TRAVERSE.Data
* Classes
  * New classes
    * Plugin: &lt; **ClassName** &gt; + Plugin \(eg. SamplePlugin\)
    * Control: &lt; **ClassName** &gt; + Control \(eg. SampleControl\)
  * Custom classes
    * Plugin: &lt; **ClassName** &gt; + &lt; **Project Abbreviation** &gt; + Plugin \(eg. SampleFoodPlugin\)
    * Controls: &lt; **ClassName** &gt; + &lt; **Project Abbreviation** &gt; + Control \(eg. SampleFoodControl\)

## **Custom Solutions**

* Solutions
  * &lt; **Custom** &gt; + Code.sln \(All non-reporting service projects\)
  * &lt; **Custom**  &gt; + Report.sln.
* Projects/Assemblies
  * Client: OSI.&lt; **Client Abbreviation** &gt; + .Client + .&lt; **Description** &gt;
  * Business: OSI. &lt; **Client Abbreviation**  &gt; + .Business + .&lt; **Description** &gt;
  * Data: OSI. &lt; **Client Abbreviation** &gt; + .Data+ .&lt; **Description** &gt;
* Namespace
  * Client/Business: Same as Assembly Name for 
  * Data: TRAVERSE.Data
* Classes
  * Plugin:  &lt; **Custom** &gt; + &lt; **ClassName** &gt; + Plugin \(eg. CustomCustomerPlugin\)
  * Control: &lt; **Custom** &gt; + &lt; **ClassName** &gt; + Control \(eg. CustomCustomerControl\)

