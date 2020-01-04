# ASP.NET

## RegisterClientScript vs. RegisterStartupScript

Source [http://stackoverflow.com/questions/666519/difference-between-registerstartupscript-and-registerclientscriptblock](http://stackoverflow.com/questions/666519/difference-between-registerstartupscript-and-registerclientscriptblock)

When you use RegisterStartupScript, it will render your script after all the elements in the page \(right before the form's end tag\). This enables the script to call or reference page elements without the possibility of it not finding them in the Page's DOM.

When you use RegisterClientScriptBlock, the script is rendered right after the Viewstate tag, but before any of the page elements. Since this is a direct script \(not a function that can be called, it will immediately be executed by the browser. But the browser does not find the label in the Page's DOM at this stage and hence you should receive an "Object not found" error.

## Troubleshooting

## CultureNotFoundException

I have migrated my ASP.NET MVC 2 project to VS 2010 + .NET 4.0. Now when i start the application i get a lot of "CultureNotFoundException" in IntelliTrace and Output/Gebug window : A first chance exception of type 'System.Globalization.CultureNotFoundException' occurred in mscorlib.dll I know what "A first chance exception" means, but when i try to debug\(added "CultureNotFoundException" into Bebug/Exceptions\[Thrown\]\) why ex. is thrown i got this detailed exception text: System.Globalization.CultureNotFoundException occurred Message=Culture is not supported. Parameter name: name designer is an invalid culture identifier. Source=mscorlib ParamName=name InvalidCultureName=designer StackTrace: at System.Globalization.CultureInfo..ctor\(String name, Boolean useUserOverride\) InnerException: I wonder why .NET is trying to create CultureInfo with name "designer"?

Fra [http://stackoverflow.com/questions/2116821/net-4-0-culturenotfoundexception](http://stackoverflow.com/questions/2116821/net-4-0-culturenotfoundexception)

I had a similar issue with the CultureName "UserCache". To resolve this I deleted all the folders from in here: C:\Windows\Microsoft.NET\Framework\v4.0.30319\Temporary ASP.NET Files

Fra [http://stackoverflow.com/questions/2116821/net-4-0-culturenotfoundexception](http://stackoverflow.com/questions/2116821/net-4-0-culturenotfoundexception)

