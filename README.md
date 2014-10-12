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

With version 1.1 the pom supports mixed java/scale projects using the scala-maven-plugin and the scala library.

To activate scala support for your project you'll have to

* create src/test/scala and src/main/scala
* in your project properties, set 

```
<plugin.compiler.phase>none</plugin.compiler.phase> 
```
to deactivate the default java compiler

* Include scala in your dependencies

```xml
<dependencies>
        <dependency>
            <groupId>org.scala-lang</groupId>
            <artifactId>scala-library</artifactId>
        </dependency>
    </dependencies>
```

* activate the scala plugin

```
<build>
        <plugins>
            <plugin>
                <groupId>net.alchim31.maven</groupId>
                <artifactId>scala-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>
```

everything else is preconfigured in the parent poms dependencyManagement section.
