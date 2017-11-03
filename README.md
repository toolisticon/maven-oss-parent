

# maven-oss-parent

maven parent as a base for future oss projects

## Kotlin

Activation:

* `src/main/kotlin` is present.

Features:

* `kotlin-stdlib-jre8` and `kotlin-test`added to dependencies
* `kotlin-maven-plugin`  and `kotlin-maven-allopen`added to build

Version:

* `kotlin.version`=1.1.51, can be overwritten in child pom.

## Spring Boot

Activation: 

* `src/main/resources/application.yml` is present. Can be empty

Features:

* spring-boot-dependencies BOM added to dependencyManagement
* spring-boot-maven-plugin added to build.

Version:

* `spring-boot.version`=1.5.8.RELEASE, can be overwritten in child pom. 
