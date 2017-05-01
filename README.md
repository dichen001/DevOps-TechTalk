# DevOps-TechTalk
DevOps-TechTalk


# Provides a high level report about tool (10 points)
[http://tiny.cc/techtalk_ci](http://tiny.cc/techtalk_ci)

# Provides setup instructions (sample code, configuration files, install scripts) 20 points

## II. Create Continuous Integration Build
  
### Under `Build` hub, create a new empty `Definition`
 Use HOL Master branch for CI

----
### Add Build steps:
#### Utilities: **PowerShell**
  - Name: `dotnet restore, build, test and publish`
  - Path: `build.ps1`
  - Arguments: `$(BuildConfiguration) $(build.stagingDirectory)`

#### Test: **Publish Test Results**
  - Test Result Format to `XUnit`
  - Test Results File to `**/testresults.xml`

#### Utilities: **Copy and Publish Build Artifacts**
  - Copy Root: `$(build.stagingDirectory)`
  - Contents: `**\*.zip`
  - Artifact Name: `drop`
  - Artifact Type: `Server`
  

**Note**: The build.ps1 script contains commands using the dotnet.exe executable used by .Net Core. The build script does the following: restore, build, test, publish, and produce an MSDeploy zip package.

----
### Add Variables
Create a new variable that will be used by the `build.ps1` PowerShell script;

**BuildConfiguration**: `release`

----
### Modify Triggers
- Check **Continuous integration (CI)** option 
- Uncheck **Batch Changes**
- Filter includes **master**

----
### Save the definition.


# Provides a screencast or demo environment (e.g. virtual machine) using tool on a sample task (20 points).
https://youtu.be/wROwykC8GSQ
