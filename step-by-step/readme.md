# Sonar Cube For Local Development

## Prerequisite

```
docker-compose -v
docker -v
java -version
```

## Run first time 

<https://docs.sonarqube.org/latest/setup/install-server/>
https://blog.setapp.pl/sonarscanner-msbuild-tutorial

```
docker-compose up
```

### Install sonar scanner

<https://docs.sonarqube.org/latest/analysis/scan/sonarscanner-for-msbuild/>

```
dotnet tool install --global dotnet-sonarscanner --version x.x.x
```

path is %USERPROFILE%\.dotnet\tools

### Run tool

#### Template

```
dotnet sonarscanner begin /k:"project-key"
dotnet build <path to solution.sln>
dotnet sonarscanner end
```

#### Customised script

```
dotnet sonarscanner begin /k:"fractal-api" /d:sonar.verbose=true
dotnet build ./Fractal.Api.csproj
dotnet sonarscanner end
```

Run the very fist time and look the exact location for global configuration file: SonarQube.Analysis.xml
In my case it is

```
Default properties file was found at C:\Users\sshabalin\.dotnet\tools\.store\dotnet-sonarscanner\5.0.4\dotnet-sonarscanner\5.0.4\tools\net5.0\any\SonarQube.Analysis.xml
```

#### Run results

```
sshabalin@SSHABALIN-NB Fractal.Api > dotnet sonarscanner begin /k:"fractal-api"
SonarScanner for MSBuild 5.0.4
Using the .NET Core version of the Scanner for MSBuild
Pre-processing started.
Preparing working directories...
12:42:26.176  Updating build integration targets...
12:42:26.534  Fetching analysis configuration settings...
12:42:27.988  Provisioning analyzer assemblies for cs...
12:42:27.989  Installing required Roslyn analyzers...
12:42:28.856  Provisioning analyzer assemblies for vbnet...
12:42:28.857  Installing required Roslyn analyzers...
12:42:28.877  Pre-processing succeeded.
```

```
sshabalin@SSHABALIN-NB Fractal.Api > dotnet build ./Fractal.Api.csproj
Microsoft (R) Build Engine version 16.8.0+126527ff1 for .NET
Copyright (C) Microsoft Corporation. All rights reserved.

  Determining projects to restore...
  All projects are up-to-date for restore.
C:\git\Fractal\Fractal.Api\Controllers\WeatherForecastController.cs(19,61): warning S4487: Remove this unread private field '_logger' or refactor the code to use its value. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\Api.cs(1,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\Api.cs(5,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\Api.cs(6,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\Api.cs(7,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\Api.cs(13,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\ServiceEventSource.cs(48,21): warning S4136: All 'Message' method overloads should be adjacent. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\Controllers\WeatherForecastController.cs(6,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\Controllers\WeatherForecastController.cs(29,23): warning S2245: Make sure that using this pseudorandom number generator is safe here. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\ServiceEventSource.cs(2,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\ServiceEventSource.cs(5,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\ServiceEventSource.cs(6,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\ServiceEventSource.cs(8,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\Startup.cs(3,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\Startup.cs(7,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\Startup.cs(8,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\Startup.cs(9,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\Startup.cs(10,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\Startup.cs(11,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\ServiceEventSource.cs(95,28): warning S107: Method has 8 parameters, which is greater than the 7 authorized. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
  Fractal.Api -> C:\git\Fractal\Fractal.Api\bin\Debug\netcoreapp3.1\win7-x64\Fractal.Api.dll
  Sonar: (Fractal.Api.csproj) Project processed successfully

Build succeeded.

C:\git\Fractal\Fractal.Api\Controllers\WeatherForecastController.cs(19,61): warning S4487: Remove this unread private field '_logger' or refactor the code to use its value. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\Api.cs(1,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\Api.cs(5,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\Api.cs(6,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\Api.cs(7,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\Api.cs(13,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\ServiceEventSource.cs(48,21): warning S4136: All 'Message' method overloads should be adjacent. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\Controllers\WeatherForecastController.cs(6,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\Controllers\WeatherForecastController.cs(29,23): warning S2245: Make sure that using this pseudorandom number generator is safe here. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\ServiceEventSource.cs(2,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\ServiceEventSource.cs(5,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\ServiceEventSource.cs(6,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\ServiceEventSource.cs(8,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\Startup.cs(3,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\Startup.cs(7,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\Startup.cs(8,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\Startup.cs(9,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\Startup.cs(10,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\Startup.cs(11,1): warning S1128: Remove this unnecessary 'using'. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
C:\git\Fractal\Fractal.Api\ServiceEventSource.cs(95,28): warning S107: Method has 8 parameters, which is greater than the 7 authorized. [C:\git\Fractal\Fractal.Api\Fractal.Api.csproj]
    20 Warning(s)
    0 Error(s)
```

```
sshabalin@SSHABALIN-NB Fractal.Api > dotnet sonarscanner end
SonarScanner for MSBuild 5.0.4
Using the .NET Core version of the Scanner for MSBuild
Post-processing started.
Calling the SonarScanner CLI...
INFO: Scanner configuration file: C:\Users\sshabalin\.dotnet\tools\.store\dotnet-sonarscanner\5.0.4\dotnet-sonarscanner\5.0.4\tools\net5.0\any\sonar-scanner-4.4.0.2170\bin\..\conf\sonar-scanner.properties
INFO: Project root configuration file: C:\git\Fractal\Fractal.Api\.sonarqube\out\sonar-project.properties
INFO: SonarScanner 4.4.0.2170
INFO: Java 15.0.1 Oracle Corporation (64-bit)
INFO: Windows 10 10.0 amd64
INFO: User cache: C:\Users\sshabalin\.sonar\cache
INFO: Scanner configuration file: C:\Users\sshabalin\.dotnet\tools\.store\dotnet-sonarscanner\5.0.4\dotnet-sonarscanner\5.0.4\tools\net5.0\any\sonar-scanner-4.4.0.2170\bin\..\conf\sonar-scanner.properties
INFO: Project root configuration file: C:\git\Fractal\Fractal.Api\.sonarqube\out\sonar-project.properties
INFO: Analyzing on SonarQube server 8.6.0
INFO: Default locale: "en_US", source code encoding: "windows-1252" (analysis is platform dependent)
INFO: Load global settings
INFO: Load global settings (done) | time=289ms
INFO: Server id: BF41A1F2-AXauAE0QzOr-VwAOfPCu
INFO: User cache: C:\Users\sshabalin\.sonar\cache
INFO: Load/download plugins
INFO: Load plugins index
INFO: Load plugins index (done) | time=265ms
INFO: Load/download plugins (done) | time=318ms
INFO: Process project properties
INFO: Process project properties (done) | time=7ms
INFO: Execute project builders
INFO: Execute project builders (done) | time=21ms
INFO: Project key: fractal-api
INFO: Base dir: C:\git\Fractal\Fractal.Api
INFO: Working dir: C:\git\Fractal\Fractal.Api\.sonarqube\out\.sonar
INFO: Load project settings for component key: 'fractal-api'
INFO: Load project settings for component key: 'fractal-api' (done) | time=257ms
INFO: Load quality profiles
INFO: Load quality profiles (done) | time=265ms
INFO: Load active rules
INFO: Load active rules (done) | time=4659ms
WARN: SCM provider autodetection failed. Please use "sonar.scm.provider" to define SCM of your project, or disable the SCM Sensor in the project settings.
INFO: Indexing files...
INFO: Project configuration:
INFO: Indexing files of module 'Fractal.Api'
INFO:   Base dir: C:\git\Fractal\Fractal.Api
INFO:   Source paths: Api.cs, Controllers/WeatherForecastController.cs, Program.cs,...
INFO: Load project repositories
INFO: Load project repositories (done) | time=260ms
INFO: Indexing files of module 'fractal-api'
INFO:   Base dir: C:\git\Fractal\Fractal.Api
INFO: 11 files indexed
INFO: Quality profile for cs: Sonar way
INFO: Quality profile for xml: Sonar way
INFO: ------------- Run sensors on module Fractal.Api
INFO: Load metrics repository
INFO: Load metrics repository (done) | time=258ms
INFO: Sensor CSS Rules [cssfamily]
INFO: No CSS, PHP, HTML or VueJS files are found in the project. CSS analysis is skipped.
INFO: Sensor CSS Rules [cssfamily] (done) | time=1ms
INFO: Sensor JaCoCo XML Report Importer [jacoco]
INFO: 'sonar.coverage.jacoco.xmlReportPaths' is not defined. Using default locations: target/site/jacoco/jacoco.xml,target/site/jacoco-it/jacoco.xml,build/reports/jacoco/test/jacocoTestReport.xml
INFO: No report imported, no coverage information will be imported by JaCoCo XML Report Importer
INFO: Sensor JaCoCo XML Report Importer [jacoco] (done) | time=2ms
INFO: Sensor C# Properties [csharp]
INFO: Sensor C# Properties [csharp] (done) | time=2ms
INFO: Sensor JavaXmlSensor [java]
INFO: 2 source files to be analyzed
INFO: Sensor JavaXmlSensor [java] (done) | time=115ms
INFO: Sensor HTML [web]
INFO: 2/2 source files have been analyzed
INFO: Sensor HTML [web] (done) | time=3ms
INFO: Sensor XML Sensor [xml]
INFO: 2 source files to be analyzed
INFO: Sensor XML Sensor [xml] (done) | time=107ms
INFO: 2/2 source files have been analyzed
INFO: Sensor VB.NET Properties [vbnet]
INFO: Sensor VB.NET Properties [vbnet] (done) | time=1ms
INFO: ------------- Run sensors on module fractal-api
INFO: Sensor CSS Rules [cssfamily]
INFO: No CSS, PHP, HTML or VueJS files are found in the project. CSS analysis is skipped.
INFO: Sensor CSS Rules [cssfamily] (done) | time=0ms
INFO: Sensor JaCoCo XML Report Importer [jacoco]
INFO: 'sonar.coverage.jacoco.xmlReportPaths' is not defined. Using default locations: target/site/jacoco/jacoco.xml,target/site/jacoco-it/jacoco.xml,build/reports/jacoco/test/jacocoTestReport.xml
INFO: No report imported, no coverage information will be imported by JaCoCo XML Report Importer
INFO: Sensor JaCoCo XML Report Importer [jacoco] (done) | time=0ms
INFO: Sensor C# Properties [csharp]
INFO: Sensor C# Properties [csharp] (done) | time=1ms
INFO: Sensor JavaXmlSensor [java]
INFO: Sensor JavaXmlSensor [java] (done) | time=0ms
INFO: Sensor VB.NET Properties [vbnet]
INFO: Sensor VB.NET Properties [vbnet] (done) | time=0ms
INFO: ------------- Run sensors on project
INFO: Sensor C# [csharp]
INFO: Importing results from 5 proto files in 'C:\git\Fractal\Fractal.Api\.sonarqube\out\0\output-cs'
INFO: Importing 1 Roslyn report
INFO: Sensor C# [csharp] (done) | time=106ms
INFO: Sensor Zero Coverage Sensor
INFO: Sensor Zero Coverage Sensor (done) | time=7ms
INFO: SCM Publisher No SCM system was detected. You can use the 'sonar.scm.provider' property to explicitly specify it.
INFO: CPD Executor Calculating CPD for 6 files
INFO: CPD Executor CPD calculation finished (done) | time=8ms
INFO: Analysis report generated in 41ms, dir size=115 KB
INFO: Analysis report compressed in 45ms, zip size=29 KB
INFO: Analysis report uploaded in 255ms
INFO: ANALYSIS SUCCESSFUL, you can browse http://localhost:9900/dashboard?id=fractal-api
INFO: Note that you will be able to access the updated dashboard once the server has processed the submitted analysis report
INFO: More about the report processing at http://localhost:9900/api/ce/task?id=AXauT-q3zOr-VwAOfT5q
INFO: Analysis total time: 7.619 s
INFO: ------------------------------------------------------------------------
INFO: EXECUTION SUCCESS
INFO: ------------------------------------------------------------------------
INFO: Total time: 8.823s
INFO: Final Memory: 7M/28M
INFO: ------------------------------------------------------------------------
The SonarScanner CLI has finished
12:44:01.957  Post-processing succeeded.
```

#### Look the results

http://localhost:9900/dashboard?id=fractal-api

### Test Coverage

#### Required params 

```
  <Property Name="sonar.cs.vscoveragexml.reportsPaths">TestResults/VisualStudio.coveragexml</Property>
```

#### Generate coverage file


```
rm -r $pwd/TestResults

dotnet sonarscanner begin /k:"fractal-api" /d:sonar.verbose=true

dotnet build ./Fractal.Api/Fractal.Api.csproj

dotnet test --results-directory:$pwd/TestResults --collect:"Code Coverage"

$coverageFileName=(gci .\TestResults\*\*.coverage | Select FullName -First 1).FullName

C:/Users/sshabalin/.nuget/packages/microsoft.codecoverage/16.5.0/build/netstandard1.0/CodeCoverage/CodeCoverage.exe analyze /output:"$(pwd)/TestResults/VisualStudio.coveragexml" $coverageFileName

dotnet sonarscanner end
```

#### Check result 

http://localhost:9900/component_measures?id=fractal-api&metric=coverage&view=list

