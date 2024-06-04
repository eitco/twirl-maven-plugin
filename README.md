[![License](https://img.shields.io/github/license/eitco/twirl-maven-plugin.svg?style=for-the-badge)](https://opensource.org/license/apache-2-0)
[![Build status](https://img.shields.io/github/actions/workflow/status/eitco/twirl-maven-plugin/deploy.yaml?branch=main&style=for-the-badge&logo=github)](https://github.com/eitco/twirl-maven-plugin/actions/workflows/deploy.yaml)
[![Maven Central Version](https://img.shields.io/maven-central/v/de.eitco.cicd/twirl-maven-plugin?style=for-the-badge&logo=apachemaven)](https://central.sonatype.com/artifact/de.eitco.cicd/twirl-maven-plugin)

Twirl Maven Plugin
==================

A Maven plugin which compiles [Twirl templates][1] into Scala source files.

This fork of the original plugin is compatible with Scala 2.13 and uses Twirl version 2.0.5.

Twirl lets you write type-safe, compiled templates in Scala:
```scala
// Hello.scala.html
@(name: String)
<h1>Hello, @name!</h1>
```
which you then render in code:
```java
html.Hello.render("Jake")
```
to yield the final result:
```
<h1>Hello, Jake!</h1>
```



Usage
-----

Add the plugin in your `pom.xml`:

```xml
<plugin>
  <groupId>de.eitco.cicd</groupId>
  <artifactId>twirl-maven-plugin</artifactId>
  <version>1.3.0</version>
  <executions>
    <execution>
      <phase>generate-sources</phase>
      <goals>
        <goal>compile</goal>
      </goals>
    </execution>
  </executions>
</plugin>
```

and specify a dependency on the Twirl API:

```xml
<dependency>
  <groupId>org.playframework.twirl</groupId>
  <artifactId>twirl-api_2.13</artifactId>
  <version>2.0.5</version>
</dependency>
```

By default the plugin looks for templates in `src/main/twirl/` and compiles to
`target/generated-sources/twirl/`. The output folder is automatically added as a
source root on the project.

The generated code is a Scala source file for each template which still need
to be compiled using something like the [scala-maven-plugin][2].

Snapshots of the development version are available in [Sonatype's `snapshots` repository][snap].



License
-------

    Copyright 2014 Jake Wharton

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.



 [1]: https://github.com/playframework/twirl
 [2]: https://github.com/davidB/scala-maven-plugin
 [snap]: https://oss.sonatype.org/content/repositories/snapshots/
