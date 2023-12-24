[main](../..)
## 프로젝트 생성
**사전 준비물**
- Java 17 설치
- IDE: IntelliJ 또는 Eclipse 설치

**스프링 부트 스타터 사이트로 이동해서 스프링 프로젝트 생성**<br>
https://start.spring.io

- 프로젝트 선택
    - Project: Gradle - Groovy
    - Spring Boot: 3.2.1
    - Language: Java
    - Packaging: Jar
    - Java 17
- Project Metadata
    - groupId: hello
    - artifactId: hello-spring
- Dependencies: Spring Web, Thymeleaf

**Gradle 전체 설정**
`build.gradle`
```groovy
plugins {
	id 'java'
	id 'org.springframework.boot' version '3.2.1'
	id 'io.spring.dependency-management' version '1.1.4'
}

group = 'hello'
version = '0.0.1-SNAPSHOT'

java {
	sourceCompatibility = '17'
}

repositories {
	mavenCentral()
}

dependencies {
	implementation 'org.springframework.boot:spring-boot-starter-thymeleaf'
	implementation 'org.springframework.boot:spring-boot-starter-web'
	testImplementation 'org.springframework.boot:spring-boot-starter-test'
}

tasks.named('test') {
	useJUnitPlatform()
}
```