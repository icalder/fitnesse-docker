# FitNesse Dockerfile

This repository contains a Dockerfile for [FitNesse](http://www.fitnesse.org/) including the [FitSharp](https://github.com/jediwhale/fitsharp) Slim server to enable running dotnet test fixtures.

## Base Docker Image
 * [openjdk:8](https://github.com/docker-library/openjdk)

## Usage
    docker run -d --name fitnesse -p 9091:8080 -v$PWD/data:/opt/fitnesse icalder/fitnesse-docker

## Example Java Test Setup
```
!define TEST_SYSTEM {slim}
!path /opt/fitnesse/fixtures/*.jar

|Import|
|com.me.package|
```

## Example C# Test Setup
```
!define TEST_SYSTEM {slim}
!define COMMAND_PATTERN {%m -r fitSharp.Slim.Service.Runner,/opt/fitsharp/fitSharp.dll %p}
!define TEST_RUNNER {/opt/fitsharp/runner.sh}
 
!path /opt/fitnesse/fixtures/some.dll

|Import|
|my.namespace|
```

