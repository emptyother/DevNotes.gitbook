# Troubleshooting

## CultureNotFoundException

I have migrated my ASP.NET MVC 2 project to VS 2010 + .NET 4.0. Now when i start the application i get a lot of "CultureNotFoundException" in IntelliTrace and Output/Gebug window : A first chance exception of type 'System.Globalization.CultureNotFoundException' occurred in mscorlib.dll I know what "A first chance exception" means, but when i try to debug\(added "CultureNotFoundException" into Bebug/Exceptions\[Thrown\]\) why ex. is thrown i got this detailed exception text: System.Globalization.CultureNotFoundException occurred Message=Culture is not supported. Parameter name: name designer is an invalid culture identifier. Source=mscorlib ParamName=name InvalidCultureName=designer StackTrace: at System.Globalization.CultureInfo..ctor\(String name, Boolean useUserOverride\) InnerException: I wonder why .NET is trying to create CultureInfo with name "designer"?

Source: [http://stackoverflow.com/questions/2116821/net-4-0-culturenotfoundexception](http://stackoverflow.com/questions/2116821/net-4-0-culturenotfoundexception)

I had a similar issue with the CultureName "UserCache". To resolve this I deleted all the folders from in here: C:\Windows\Microsoft.NET\Framework\v4.0.30319\Temporary ASP.NET Files

Source: [http://stackoverflow.com/questions/2116821/net-4-0-culturenotfoundexception](http://stackoverflow.com/questions/2116821/net-4-0-culturenotfoundexception)

## No access to C:\Windows\Microsoft.NET\Framework\v4.0.30319\Temporary ASP.NET

IIS Express og Visual Studio kjører som din egen bruker og trenger tilgang. Gi din egen bruker skrive-tilgang til denne mappen.



