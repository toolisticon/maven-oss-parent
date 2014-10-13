# holisticon-oss-parent

Common parent pom.xml for holistic FOSS projects.

## Usage

```xml
<parent>
  <groupId>de.holisticon.maven</groupId>
  <artifactId>holisticon-oss-parent</artifactId>
  <version>1.1</version>
  <relativePath />
</parent>
```

## Content:

- extends sonatype oss parent 9
- set UTF-8 properties
- define compile, release, deploy plugin

- help-plugin

## scala/java mixed compiler

With version 1.1 the pom supports mixed java/scala projects using the scala-maven-plugin and the scala library.
The configured profile is activated automatically if a src/main/scala directory is found.

## Angular/Grunt support for mixed applications

With 1.2 the pom supports creation of mixed applications contaning of a web application (WAR) delivering an 
AngularJS frontend build by a yeoman generator. The profile for this is "yo-mixed-mode". The default location for the yo sources is "yo" and can be overwritten by the yeomanProjectDirectory property. If using default yo-generator, it creates a Grunt file with an option not matching the latest version of a used component. To fix it, please remove "options" from "wiredep" target.

###Options

- yeomanProjectDirectory source directory of the yeoman generated site (defaults to yo)
- yeomanTargetDirectory target where to copy the resulted code (defaults to ${basedir}/target/${artifactId}-${version})
- yo.build.skip skip the yo build (defaults to false)
- yo.test.skip skip the test run (defaults to false)
- yo.skip skip all (defaults to false)
