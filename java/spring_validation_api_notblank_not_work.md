# Spring validation_api NotBlank not work
> **Lien Chen** *2021-03-23*

Seems annotation NotBlank is use to check variable is not null and have at least none space symbol.
Add validation_api to pom.xml doesn't work successfully.

Validation Starter no longer included in web starters

Using spring-boot-starter-validation to solve this proplem

* Solution
    * Gradle
        * `implementation 'org.springframework.boot:spring-boot-starter-validation'`
    * Maven
        * `<dependency><groupId>org.springframework.boot</groupId> <artifactId>spring-boot-starter-validation</artifactId></dependency>`

[reference_github_wiki](https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-2.3-Release-Notes#validation-starter-no-longer-included-in-web-starters)
[reference_stackoverflow](https://stackoverflow.com/questions/48614773/spring-boot-validation-annotations-valid-and-notblank-not-working)