# Initial gradle project with spring boot
================================

**Author**: Lien Chen  **Date**: 2024-01-16

Execute the following command to initialize a project
`gradle init`

During initialization, Gradle will ask you what type of project you wish to create. Here are some of the available options

* java-application: For standard Java applications.
* java-library: For Java library projects.
* groovy-application: For Groovy language applications.
* groovy-library: For Groovy library projects.
* scala-application: For Scala language applications.
* scala-library: For Scala library projects.
* kotlin-application: For Kotlin language applications.
* kotlin-library: For Kotlin library projects.
* basic: A very basic project without a predefined language or structure.


Add below content to add spring boot package
```gradle=
plugins {
    id 'org.springframework.boot' version '2.5.0' // choose fitable version
    id 'io.spring.dependency-management' version '1.0.11.RELEASE'
    id 'java'
}

dependencies {
    implementation 'org.springframework.boot:spring-boot-starter'

    testImplementation 'org.springframework.boot:spring-boot-starter-test'
    // other package ...
}

```
And then using `./gradlew build` to rebuild the project
