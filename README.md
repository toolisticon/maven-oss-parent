[<img src="https://www.holisticon.de/wp-content/uploads/2013/05/holisticon-logo-hamburg.gif" align="right" />](https://server.holisticon.de/jenkins/job/holisticon-oss-parent/)


# holisticon-oss-parent

[![Maven Central](https://maven-badges.herokuapp.com/maven-central/de.holisticon.maven/holisticon-oss-parent/badge.svg)](https://maven-badges.herokuapp.com/maven-central/de.holisticon.maven/holisticon-oss-parent)


Common parent pom.xml for holistic FOSS projects.

## Usage

This parent pom is release on maven central so it is sufficient to use it directly as parent in your project pom.xml:

```xml
<parent>
  <groupId>de.holisticon.maven</groupId>
  <artifactId>holisticon-oss-parent</artifactId>
  <version>...</version>
  <relativePath />
</parent>
```

* current development version: 2-SNAPSHOT
* latest released version: 1.1

# Plugins

## Included

<dl>
  <dt>[maven-versions-plugin](http://mojo.codehaus.org/versions-maven-plugin/index.html)</dt>
  <dd>helps to set/change versions and (more importantly) can find updates of dependencies and plugins.</dd>
  
  <dt>[scala-maven-plugin](http://davidb.github.io/scala-maven-plugin/plugin-info.html)
</dl>

## Not Included

We use the sonatype oss-parent, version 9 as parent pom. It defines some plugins and profiles related to releasing
on maven-central. We should not mix configurations, so the following plugins should not be configured in this pom:

* maven-enforcer-plugin#1.2 - assure maven versions
* maven-release-plugin#2.1 - activate the sonatype release profile
* maven-source-plugin#2.1.2 - attach sources.jar to the release
* maven-javadoc-plugin#2.7 - attach javadoc to the release
* maven-gpg-plugin#1.1 - sign the artifacts to release

## Content:

- extends sonatype oss parent 9
- set UTF-8 properties
- define compile, release, deploy plugin

# Profiles

## scala/java mixed compiler

With version 1.1 the pom supports mixed java/scala projects using the scala-maven-plugin and the scala library.
The configured profile is activated automatically if a src/main/scala directory is found.

## Angular/Grunt support for mixed applications

With 1.2 the pom supports creation of mixed applications containing of a web application (WAR) delivering an 
AngularJS front-end build by a yeoman generator. The profile for this is "yo-mixed-mode". The default location for the yo sources is "yo" and can be overwritten by the yeomanProjectDirectory property. If using default yo-generator, it creates a Grunt file with an option not matching the latest version of a used component. To fix it, please remove "options" from "wiredep" target.

###Options

- yeomanProjectDirectory source directory of the yeoman generated site (defaults to yo)
- yeomanTargetDirectory target where to copy the resulted code (defaults to ${basedir}/target/${artifactId}-${version})
- yo.build.skip skip the yo build (defaults to false)
- yo.test.skip skip the test run (defaults to false)
- yo.skip skip all (defaults to false)

## Testing

Testing is activated automatically once a src/test directory is present.

It contains the following plugins:
 
 <dl>
    <dt>[maven-surefire-plugin](http://maven.apache.org/surefire/maven-surefire-plugin/)
    <dd>runs all tests with junit except classes matching the itest pattern (*ITest.java) or inside a package named itest</dd>
    
    <dt>[maven-failsafe-plugin](http://maven.apache.org/surefire/maven-failsafe-plugin/)
    <dd>runs integration tests (mvn integration-test). All tests not matching the itest pattern or inside an itest package are skipped.</dd>
    <dd>running itests must be activated by enabling the integration-test profile (mvn clean install -Pintegration-test)</dd>
    
    
 </dl>


