# InvalidProgramException
## Prerequisites
After the MySQL connection has successfully been opened, the MySQL driver configures itself based on capabilities provided by the server.
It is at this stage the application crashes with an `InvalidProgramException`. To reproduce this issue, one will have to have a working MySQL installation. For this repro, MariaDB version 10.1.16-MariaDB was used.

## Observed behavior
```
Server Error in '/' Application.
Configuration Error
Description: An error occurred during the processing of a configuration file required to service this request. Please review the specific error details below and modify your configuration file appropriately.

Parser Error Message: Common Language Runtime detected an invalid program.

Source Error:


Line 9:        <providers>
Line 10:         <clear />
Line 11:         <add name="MySQLRoleProvider" writeExceptionsToEventLog="true" type="MySql.Web.Security.MySQLRoleProvider, MySql.Web" connectionStringName="app" applicationName="LoginControl" />
Line 12:       </providers>
Line 13:     </roleManager>

Source File: C:\inetpub\InvalidProgramCrash\web.config    Line: 11


Click here to show additional error information:

Exception Details: System.InvalidProgramException: Common Language Runtime detected an invalid program.

Source Error:

An unhandled exception was generated during the execution of the current web request. Information regarding the origin and location of the exception can be identified using the exception stack trace below.

Stack Trace:


[InvalidProgramException: Common Language Runtime detected an invalid program.]
   MySql.Data.MySqlClient.Driver.Configure(MySqlConnection connection) +0
   MySql.Data.MySqlClient.MySqlConnection.Open() +752
   MySql.Web.Common.SchemaManager.GetSchemaVersion(String connectionString) +66
   MySql.Web.Common.SchemaManager.CheckSchema(String connectionString, NameValueCollection config) +31
   MySql.Web.Security.MySQLRoleProvider.Initialize(String name, NameValueCollection config) +465
   System.Web.Configuration.ProvidersHelper.InstantiateProvider(ProviderSettings providerSettings, Type providerType) +693

Version Information: Microsoft .NET Framework Version:4.0.30319; ASP.NET Version:4.8.4001.0
```