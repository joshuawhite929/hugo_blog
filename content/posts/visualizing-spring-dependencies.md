+++
linktitle = "Leveraging Graphviz to visualize Spring Dependencies"
title = "Visualizing Spring Dependencies"
date = 2017-03-04
draft = false
tags = []
categories = ["spring", "graphviz", "kotlin"]
+++

Over the last couple of months, I have been playing with [Kotlin](https://kotlinlang.org) in my spare time.  To get a better feel for the language, I decided to implement a small program that reads through a POM file and diagrams all of its dependencies using [Graphviz](http://www.graphviz.org) and dot.

With the exception of one, the dependencies in the images below only include [Spring](https://spring.io) dependencies (com.springframework.\*, io.spring.\*).  The "unfiltered" example below is included only to show what this looks like.  This has helped me better visualize how the various projects reference each other.  For example, these diagrams changed how I thought the [Spring IO Platform](http://platform.spring.io/platform/) was used.  Instead of having projects like [Spring Boot](http://projects.spring.io/spring-boot/) align with a specific version of the [Spring IO Platform](http://platform.spring.io/platform/), you can see from the diagram below that [Spring Boot](http://projects.spring.io/spring-boot/) drives the [Spring IO Platform](http://platform.spring.io/platform/).

As you can imagine, I now have a whole new appreciation for the shenanigans that maven/gradle need to go through to derive dependencies.

_Note:_ Click the images below for a larger version.

_**Legend:**_

* __Fill Color__
    * _Green_ - This node is where the graph starts
    * _Orange_ - This is a regular Project Object Model (POM) file
    * _Blue_ - This is a Bill of Materials (BOM) file
* __Arrows__
    * _Solid Line, Open Arrow_ - This arrow points to a given POM files parent
    * _Dashed Line, Solid Arrow_ - This arrow indicates a "dependency" relationship
    * _Dotted Line, Inverse Arrow_ - This arrow indicates that a POM was imported into the Dependency Management section of another POM
* __Label__
    * _Normal Text Label_ - This indicates the POM's artifactId
    * _[Bracketed Text Label]_ - If this artifactId is dependency managed, this value indicates where this is specified


### Spring IO Platform
[![Spring IO Platform](/images/visualizing-spring-dependencies/io.spring.platform_platform-bom_Brussels-RELEASE.png)](/images/visualizing-spring-dependencies/io.spring.platform_platform-bom_Brussels-RELEASE.png)

### spring-boot-starter-parent
[![spring-boot-starter-parent](/images/visualizing-spring-dependencies/org.springframework.boot_spring-boot-starter-parent_1.5.1.RELEASE.png)](/images/visualizing-spring-dependencies/org.springframework.boot_spring-boot-starter-parent_1.5.1.RELEASE.png)

### spring-boot-starter-web
[![spring-boot-starter-web](/images/visualizing-spring-dependencies/org.springframework.boot_spring-boot-starter-web_1.5.1.RELEASE.png)](/images/visualizing-spring-dependencies/org.springframework.boot_spring-boot-starter-web_1.5.1.RELEASE.png)

### spring-boot-starter-web (unfiltered)
[![spring-boot-starter-web (unfiltered)](/images/visualizing-spring-dependencies/org.springframework.boot_spring-boot-starter-web_1.5.1.RELEASE_unfiltered.png)](/images/visualizing-spring-dependencies/org.springframework.boot_spring-boot-starter-web_1.5.1.RELEASE_unfiltered.png)

### Spring Cloud
[![Spring Cloud](/images/visualizing-spring-dependencies/org.springframework.cloud_spring-cloud-dependencies_Camden.SR5.png)](/images/visualizing-spring-dependencies/org.springframework.cloud_spring-cloud-dependencies_Camden.SR5.png)

### Spring Cloud Netflix
[![Spring Cloud Netflix](/images/visualizing-spring-dependencies/org.springframework.cloud_spring-cloud-netflix_1.2.4.RELEASE.png)](/images/visualizing-spring-dependencies/org.springframework.cloud_spring-cloud-netflix_1.2.4.RELEASE.png)

### Spring Framework
[![Spring Framework](/images/visualizing-spring-dependencies/org.springframework_spring-context_4.3.6.RELEASE.png)](/images/visualizing-spring-dependencies/org.springframework_spring-context_4.3.6.RELEASE.png)