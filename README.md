# Blazor-MySql-MariaDB-.Net-5
Guide donkeys to create a Blazor application with identityframerkok with .Net 5 and MariaDB or Mysql database

Brief description of the steps to be carried out
The objective is to create an application in an empty database, using Net 5, and taking as a template the template created by Blazor server that is automatically created from visual studio 2019

### Develop Enviroment
- Visual Studio 2019
- MariaDb or MySql
- HeidySql


### Previous knowledge
- Using Visual Studio 2019
- Use of MySql or MariaDB
- Development using C # language
- Using HeidySQL

### Packages 
- Pomelo.IdentityFrameworkCore.MySql v 5 (Now in Apha version)

### Steeps
I have splited the donkey guide in seven steeps, whit a well done test at end of each of them 

1. Create empty database in Mysql or MariaDB.
In this example "bbdd-test-identity"
2. Create a Blazor Server application with individual user accounts.
In this example "AppBlazorMariaDB"
3. Install and uninstall Nuget packages
Remove the MS SqlServer libraries and put the MySql ones
4. Modify the appsettings.json configuration file
5. Modify Startup.cs file
6. Create IdentityFramewok migration files for MySql
7. Create tables in database bbdd-test-identity

## 1. Create empty database in Mysql or MariaDB.

### Need
- Database server like MariaDB or MySql
- HeidiSql or similar for use as Database Manager, i Use HeidiSql in this guide

#### 1.1 Create database for testing

I assume that you have MariaDB or MySql installed. If not, download and install it before continuing

here his links
-MariaDB Foundation - MariaDB.org https://mariadb.org/
-MySql - https://www.mysql.com/


![HeidiSql Connec](https://github.com/vniclos/Blazor-MySql-MariaDB-.Net-5/blob/main/Images/01-MariaDBConnection.jpg?raw=true)
