# Blazor-MySql-MariaDB-.Net-5
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
3. Install and uninstall Nuget packages
Remove the MS SqlServer libraries and put the MySql ones
4. Modify the appsettings.json configuration file
5. Modify Startup.cs file
6. Create IdentityFramewok migration files for MySql
7. Create tables in database bbdd-test-identity

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


