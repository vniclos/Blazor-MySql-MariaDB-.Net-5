# Blazor app  whith MySql or MariaDB and .Net 5 and IdentityFamework
(Excusemme, I'm writen this guide now)
Guide donkeys to create a Blazor application with identityframerkok with .Net 5 and MariaDB or Mysql database

Brief description of the steps to be carried out
The objective is to create an application in an empty database, using Net 5, and taking as a template the template created by Blazor server that is automatically created from visual studio 2019

### Develop Enviroment
- Visual Studio 2019
- MariaDb or MySql
- HeidySql
- Pomelo.EntityFrameworkSql.Mysql


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
3. Remove innecesiary files and and uninstall Nuget packages
Remove the MS SqlServer libraries and put the MySql ones
4. Modify the appsettings.json configuration file
5. Modify Startup.cs file
6. Create IdentityFramewok migration files for MySql
7. Create tables in database bbdd-test-identity
8. Testing application


## 1. Create empty database in Mysql or MariaDB.

### Need previous for this steep
- Database server like MariaDB or MySql
- HeidiSql or similar for use as Database Manager, i Use HeidiSql in this guide (When you instal MariaDB HeidiSql is auto installed)

I assume that you have MariaDB or MySql installed. If not, download and install it before continuing

Here his links
- MariaDB Foundation - MariaDB.org https://mariadb.org/
- MySql - https://www.mysql.com/
- HeidiSql- https://www.heidisql.com/


#### 1.1 Create database for testing

##### 1.1.1 Open HeidiSql and connect to your MariaDB or MySql server (From now on I will write only MariaDB to refer to both (MariaDB and MySql)


![HeidiSql Connec](https://github.com/vniclos/Blazor-MySql-MariaDB-.Net-5/blob/main/Images/01-MariaDBConnection.jpg?raw=true)

##### 1.1.2 Create database 
In this guide the datase mame are **"bbdd-test-identity"
Open HeidiSql tool, then pick in your server Name, right click in mouse, Create New> Database > Fill the name "bbdd-test-identity"> OK


![HeidiSql Create database](https://github.com/vniclos/Blazor-MySql-MariaDB-.Net-5/blob/main/Images/02-MariaDBCreate.jpg?raw=true)

#### 1.2 Testing welldone  this steep
On the right of HeidySql Screen your can show the database **"bbdd-test-identity" in the tree, if not put mouse cursor on server name, riggth  buttton and refresh

![HeidiSql Create database](https://github.com/vniclos/Blazor-MySql-MariaDB-.Net-5/blob/main/Images/03-MariaDBCreate.jpg)

Now yo can close HeidySql, but need remember Marria db Server Name, (May be localhost, IP addres,  or other), User and password for access to it.

## 2. Create a Blazor Server application with individual user accounts.

### Need previous for this steep
- Visual studio 2019

I assume that you have installed Visual Studio. If not, download and install  before continuing. Microsoft have  Visual studio Comunnity version free

Here his links
- Visual studio Comunnit - https://visualstudio.microsoft.com/es/vs/community/

### 2.1 Create Blazor application with individual user acount from standard template
Start visual studio 2010, 

### 2.1.1 select create new project, in the next scren, be sure select **Blazor Server app

![HeidiSql Create database](https://github.com/vniclos/Blazor-MySql-MariaDB-.Net-5/blob/main/Images/05%20create%20blazor%20server%20app.jpg?raw=true)
Click next
### 2.1.2 Config .net 5 and Indivisual user accounts

As you can show in next image

![HeidiSql Create database](https://github.com/vniclos/Blazor-MySql-MariaDB-.Net-5/blob/main/Images/07%20create%20app%20Net5.0%20.jpg?raw=true)

Click next

### 2.2 Testing weldone this steep

On the right screen you can show some like this 

**Warning". This template are configurated for work whit SqlServer Express, as you can show in next figure points 1 and 2. They are not necesare for us!. 
Not problem in next steeps we change it for MariaDB.

## 3. Remove innecesary files and Nuget packages, then install Necesary Nuget packet

![image]https://github.com/vniclos/Blazor-MySql-MariaDB-.Net-5/blob/main/Images/08%20create%20app%20Net5.0%20.jpg?raw=true)

### 3.1 Remove Migrations folder
On the right there are subfolder of Data folder named Migration, remove it 

![image](https://github.com/vniclos/Blazor-MySql-MariaDB-.Net-5/blob/main/Images/09%20delete%20migration%20folder.jpg?raw=true)

### 3.2 Remove nuget packet Microsft.EntityFrameworkCore.Sql
In visual studio. Menu: Tools > Nuget Pakage Manager > Manage Nuget Package  for solution, Select Installed, Find  MySql.EntityFrameworkCore.SQL   and unistal it


![image](https://github.com/vniclos/Blazor-MySql-MariaDB-.Net-5/blob/main/Images/10%20uninstall%20sqlserverpackage.jpg?raw=true)

### 3.3 Instal Nuguet Packet **"Pomelo.EntityFramworkCore.Sql v5"

In visual studio. Menu: Tools > Nuget Pakage Manager > Manage Nuget Package  for solution, select Browse, **Include prerelease**, Pomelo.EntityFrameworkColre.MySql 

Note: At this date 2021-March-27 the version are in prerelease Alfa)
 
![image](https://github.com/vniclos/Blazor-MySql-MariaDB-.Net-5/blob/main/Images/11--install-pomello-entityframeworkCore.MySql.jpg?raw=true)

### 3.4 Check welldone requisites 

In this steep, on the Solution explorer you need:

- show in packages, Pomelo.EntityFrameworkCore.MySql (5.0.0-alpha 1), not lest than this version, because we are runting aplicatoin .Bet 5
- Not Show in pacages Microsoft.EntityFrameworkCore.Sql
- In Data folder not show subfolder Migration.



![image](https://github.com/vniclos/Blazor-MySql-MariaDB-.Net-5/blob/main/Images/12-Check-prerequisites.jpg?raw=true)

## 4 Modify the appsettings.json configuration file

The appconfig.json file in root of project has string connection for do connection with MS SqlServer Expres,  similar to this.

"DefaultConnection": "Server=(localdb)\\mssqllocaldb;Database=aspnet-AppBlazorMariaDB-2A2FFB32-AB8F-467E-8741-225DD84906A6;Trusted_Connection=True;MultipleActiveResultSets=true"

We need to change it  to MariaDB string connection  like this

ConnectionStrings": {  "DefaultConnection": "Server=**ServerName**;Database= *bbdd-test-identity*;Uid=**UserName**;Pwd=**Password**;Connection Timeout=30;Convert Zero Datetime=True ; Allow Zero Datetime=True"

Remeber to change, ServerName, UserName and Password to your needs. I asume your database name has  name *bbdd-test-identity*, if not you need to change.

Save changes

## 5. Modify Startup.cs file
Startup file is builded for MS SqlServer whe need to do this moficifications

### 5.1 Add reference to pomelo 
Adding on the top the line “using Pomelo.EntityFrameworkCore;”

### 5.2 Modify one line in the function ConfigureServices
Changing the word **UseSqlServer** bya **UseMySql**

Then the origina line (For MS SqlServer )
services.AddDbContext<ApplicationDbContext>(options => options. **UseSqlServer**
(Configuration.GetConnectionString("DefaultConnection")));

Will be (For MariaDB)
services.AddDbContext<ApplicationDbContext>(options => options. **UseMySql** 
(Configuration.GetConnectionString("DefaultConnection")));

 
![image](https://github.com/vniclos/Blazor-MySql-MariaDB-.Net-5/blob/main/Images/20--Change-in-startup.cs.jpg?raw=true)


Save changes

## 6 Create IdentityFramewok migration files for MySql

Now compile application, and we will be ready for automatic build Migration folder and filesd for EntityFramework database code first.

6.1 Open window of Console Pakage Mananger.

If is closed, you can do: Menu> Tools > Nuget Package Manager > Console 

6.2 Clic en Nuget Console and write

PM> add-migration ‘identity’

Enter, If all is ok you can see some like next figure

![image](https://github.com/vniclos/Blazor-MySql-MariaDB-.Net-5/blob/main/Images/15--execute-add-migration-identity.jpg?raw=true)

6.3 Check if all is welldone

I project explore need show a new folder with the name **Migration**, inside it there are the  necesary files for build tables on MariaDB database

![image](https://github.com/vniclos/Blazor-MySql-MariaDB-.Net-5/blob/main/Images/16--New-Migration-folder.jpg?raw=true)


###7. Create tables in database bbdd-test-identity
Now we are use migration folder for build tables on database

##7.1 Build tables  on database

On the Package Manager console call comannd 

PM> Update-Database

Enter, if all is ok the console repply

Build started...

Build succeeded.

Done.

### 7.2 Check if all is welldone

Now open HeidiSql application and look at  BB-test-identity database, you need show the necesary tables for use in you aplication IdentityFramework. I the HeidiSql is openned before 7.1 steep, you need refresh view by click F5

https://github.com/vniclos/Blazor-MySql-MariaDB-.Net-5/blob/main/Images/22-%20SHow%20database.jpg?raw=true

## 8. Testing application
Now is time to test if ower application can add user, and if the user can loging

## 9 The app could be better
We could be modifiy user politicy in statup.cs file
We could be add email confirmation.
