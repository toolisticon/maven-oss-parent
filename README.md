# holisticon-oss-parent

Common parent pom.xml for holistic FOSS projects.

## Usage

```xml
<parent>
  <groupId>de.holisticon.maven</groupId>
  <artifactId>holisticon-oss-parent</artifactId>
  <version>1.0</version>
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
