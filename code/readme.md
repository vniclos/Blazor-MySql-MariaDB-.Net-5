# Code example.

This code are based in Microsoft Blazor server template with individual user accounts. 

The code has maked all ajust of the tutorial. You can use without guarantie.

Yo need customizing configuration **appsettings.json** file  for connect to your MariaBB or MySqlServer, you need change:
 ServerName, UserName, Pasword, and Database
 
 You need download nuget package Pomelo.IdentityFrameworkCore.MySql version 5
 
 ```
 {
  "ConnectionStrings": {
    "DefaultConnection": "Server=ServerName;Database= bbdd-test-identity;Uid=UserName;Pwd=Pasword;Connection Timeout=30;Convert Zero Datetime=True ; Allow Zero Datetime=True"
  },
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  },
  "AllowedHosts": "*"
}

 '''
