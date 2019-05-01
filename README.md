# Regression in maven-javadoc-plugin 3.1.0

With `maven-javadoc-plugin:3.1.0`, it's not possible to generate an aggregated Javadoc artifact (JAR) of Maven sub-modules inside a project of type "pom".

The info message emitted by Maven is:

> Not executing Javadoc as the project is not a Java classpath-capable package


`maven-javadoc-plugin:3.0.1` and `maven-javadoc-plugin:2.10.4` are working as expected. 

## maven-javadoc-plugin 3.1.0

```
# ./mvnw -P javadoc-3-1 clean javadoc:aggregate-jar
[INFO] Scanning for projects...
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Build Order:
[INFO] 
[INFO] parent                                                             [pom]
[INFO] a                                                                  [jar]
[INFO] b                                                                  [jar]
[INFO] 
[INFO] -------------------< com.github.joschi.maven:parent >-------------------
[INFO] Building parent 1.0.0-SNAPSHOT                                     [1/3]
[INFO] --------------------------------[ pom ]---------------------------------
[INFO] 
[INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ parent ---
[INFO] Deleting /Users/joschi/src/maven-javadoc-aggregate-jar/target
[INFO] 
[INFO] ---------------------< com.github.joschi.maven:a >----------------------
[INFO] Building a 1.0.0-SNAPSHOT                                          [2/3]
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ a ---
[INFO] 
[INFO] ---------------------< com.github.joschi.maven:b >----------------------
[INFO] Building b 1.0.0-SNAPSHOT                                          [3/3]
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ b ---
[INFO] 
[INFO] -------------------< com.github.joschi.maven:parent >-------------------
[INFO] Building parent 1.0.0-SNAPSHOT                                     [4/3]
[INFO] --------------------------------[ pom ]---------------------------------
[INFO] 
[INFO] >>> maven-javadoc-plugin:3.1.0:aggregate-jar (default-cli) > compile @ parent >>>
[INFO] 
[INFO] >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
[INFO] Forking a 1.0.0-SNAPSHOT
[INFO] >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
[INFO] 
[INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ a ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] skip non existing resourceDirectory /Users/joschi/src/maven-javadoc-aggregate-jar/a/src/main/resources
[INFO] 
[INFO] --- maven-compiler-plugin:3.1:compile (default-compile) @ a ---
[INFO] Changes detected - recompiling the module!
[INFO] Compiling 1 source file to /Users/joschi/src/maven-javadoc-aggregate-jar/a/target/classes
[INFO] 
[INFO] >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
[INFO] Forking b 1.0.0-SNAPSHOT
[INFO] >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
[INFO] 
[INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ b ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] skip non existing resourceDirectory /Users/joschi/src/maven-javadoc-aggregate-jar/b/src/main/resources
[INFO] 
[INFO] --- maven-compiler-plugin:3.1:compile (default-compile) @ b ---
[INFO] Changes detected - recompiling the module!
[INFO] Compiling 1 source file to /Users/joschi/src/maven-javadoc-aggregate-jar/b/target/classes
[INFO] 
[INFO] <<< maven-javadoc-plugin:3.1.0:aggregate-jar (default-cli) < compile @ parent <<<
[INFO] 
[INFO] 
[INFO] --- maven-javadoc-plugin:3.1.0:aggregate-jar (default-cli) @ parent ---
[INFO] Not executing Javadoc as the project is not a Java classpath-capable package
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Summary for parent 1.0.0-SNAPSHOT:
[INFO] 
[INFO] parent ............................................. SUCCESS [  1.094 s]
[INFO] a .................................................. SUCCESS [  0.004 s]
[INFO] b .................................................. SUCCESS [  0.004 s]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  1.639 s
[INFO] Finished at: 2019-05-01T12:09:47+02:00
[INFO] ------------------------------------------------------------------------
# ls target/*.jar
cannot access 'target/*.jar': No such file or directory (os error 2)
```

## maven-javadoc-plugin 3.0.1

```
# ./mvnw -P javadoc-3-0 clean javadoc:aggregate-jar
[INFO] Scanning for projects...
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Build Order:
[INFO] 
[INFO] parent                                                             [pom]
[INFO] a                                                                  [jar]
[INFO] b                                                                  [jar]
[INFO] 
[INFO] -------------------< com.github.joschi.maven:parent >-------------------
[INFO] Building parent 1.0.0-SNAPSHOT                                     [1/3]
[INFO] --------------------------------[ pom ]---------------------------------
[INFO] 
[INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ parent ---
[INFO] 
[INFO] ---------------------< com.github.joschi.maven:a >----------------------
[INFO] Building a 1.0.0-SNAPSHOT                                          [2/3]
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ a ---
[INFO] Deleting /Users/joschi/src/maven-javadoc-aggregate-jar/a/target
[INFO] 
[INFO] ---------------------< com.github.joschi.maven:b >----------------------
[INFO] Building b 1.0.0-SNAPSHOT                                          [3/3]
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ b ---
[INFO] Deleting /Users/joschi/src/maven-javadoc-aggregate-jar/b/target
[INFO] 
[INFO] -------------------< com.github.joschi.maven:parent >-------------------
[INFO] Building parent 1.0.0-SNAPSHOT                                     [4/3]
[INFO] --------------------------------[ pom ]---------------------------------
[INFO] 
[INFO] >>> maven-javadoc-plugin:3.0.1:aggregate-jar (default-cli) > compile @ parent >>>
[INFO] 
[INFO] >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
[INFO] Forking a 1.0.0-SNAPSHOT
[INFO] >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
[INFO] 
[INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ a ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] skip non existing resourceDirectory /Users/joschi/src/maven-javadoc-aggregate-jar/a/src/main/resources
[INFO] 
[INFO] --- maven-compiler-plugin:3.1:compile (default-compile) @ a ---
[INFO] Changes detected - recompiling the module!
[INFO] Compiling 1 source file to /Users/joschi/src/maven-javadoc-aggregate-jar/a/target/classes
[INFO] 
[INFO] >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
[INFO] Forking b 1.0.0-SNAPSHOT
[INFO] >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
[INFO] 
[INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ b ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] skip non existing resourceDirectory /Users/joschi/src/maven-javadoc-aggregate-jar/b/src/main/resources
[INFO] 
[INFO] --- maven-compiler-plugin:3.1:compile (default-compile) @ b ---
[INFO] Changes detected - recompiling the module!
[INFO] Compiling 1 source file to /Users/joschi/src/maven-javadoc-aggregate-jar/b/target/classes
[INFO] 
[INFO] <<< maven-javadoc-plugin:3.0.1:aggregate-jar (default-cli) < compile @ parent <<<
[INFO] 
[INFO] 
[INFO] --- maven-javadoc-plugin:3.0.1:aggregate-jar (default-cli) @ parent ---
[ERROR] no module descriptor for com.github.joschi.maven:parent
[ERROR] no module descriptor for com.github.joschi.maven:a
[ERROR] no module descriptor for com.github.joschi.maven:b
[INFO] 
Loading source files for package com.github.joschi.maven...
Constructing Javadoc information...
Standard Doclet version 1.8.0_201
Building tree for all the packages and classes...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/com/github/joschi/maven/MainA.html...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/com/github/joschi/maven/MainB.html...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/com/github/joschi/maven/package-frame.html...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/com/github/joschi/maven/package-summary.html...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/com/github/joschi/maven/package-tree.html...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/constant-values.html...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/com/github/joschi/maven/class-use/MainB.html...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/com/github/joschi/maven/class-use/MainA.html...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/com/github/joschi/maven/package-use.html...
Building index for all the packages and classes...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/overview-tree.html...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/index-all.html...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/deprecated-list.html...
Building index for all classes...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/allclasses-frame.html...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/allclasses-noframe.html...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/index.html...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/help-doc.html...
[INFO] Building jar: /Users/joschi/src/maven-javadoc-aggregate-jar/target/parent-1.0.0-SNAPSHOT-javadoc.jar
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Summary for parent 1.0.0-SNAPSHOT:
[INFO] 
[INFO] parent ............................................. SUCCESS [  2.056 s]
[INFO] a .................................................. SUCCESS [  0.007 s]
[INFO] b .................................................. SUCCESS [  0.005 s]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  2.601 s
[INFO] Finished at: 2019-05-01T12:09:51+02:00
[INFO] ------------------------------------------------------------------------
# ls target/*.jar
parent-1.0.0-SNAPSHOT-javadoc.jar
```

## maven-javadoc-plugin 2.10.4

```
# ./mvnw -P javadoc-2-10 clean javadoc:aggregate-jar
[INFO] Scanning for projects...
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Build Order:
[INFO] 
[INFO] parent                                                             [pom]
[INFO] a                                                                  [jar]
[INFO] b                                                                  [jar]
[INFO] 
[INFO] -------------------< com.github.joschi.maven:parent >-------------------
[INFO] Building parent 1.0.0-SNAPSHOT                                     [1/3]
[INFO] --------------------------------[ pom ]---------------------------------
[INFO] 
[INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ parent ---
[INFO] Deleting /Users/joschi/src/maven-javadoc-aggregate-jar/target
[INFO] 
[INFO] ---------------------< com.github.joschi.maven:a >----------------------
[INFO] Building a 1.0.0-SNAPSHOT                                          [2/3]
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ a ---
[INFO] Deleting /Users/joschi/src/maven-javadoc-aggregate-jar/a/target
[INFO] 
[INFO] ---------------------< com.github.joschi.maven:b >----------------------
[INFO] Building b 1.0.0-SNAPSHOT                                          [3/3]
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ b ---
[INFO] Deleting /Users/joschi/src/maven-javadoc-aggregate-jar/b/target
[INFO] 
[INFO] -------------------< com.github.joschi.maven:parent >-------------------
[INFO] Building parent 1.0.0-SNAPSHOT                                     [4/3]
[INFO] --------------------------------[ pom ]---------------------------------
[INFO] 
[INFO] --- maven-javadoc-plugin:2.10.4:aggregate-jar (default-cli) @ parent ---
[INFO] 
Loading source files for package com.github.joschi.maven...
Constructing Javadoc information...
Standard Doclet version 1.8.0_201
Building tree for all the packages and classes...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/com/github/joschi/maven/MainA.html...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/com/github/joschi/maven/MainB.html...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/com/github/joschi/maven/package-frame.html...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/com/github/joschi/maven/package-summary.html...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/com/github/joschi/maven/package-tree.html...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/constant-values.html...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/com/github/joschi/maven/class-use/MainB.html...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/com/github/joschi/maven/class-use/MainA.html...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/com/github/joschi/maven/package-use.html...
Building index for all the packages and classes...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/overview-tree.html...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/index-all.html...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/deprecated-list.html...
Building index for all classes...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/allclasses-frame.html...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/allclasses-noframe.html...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/index.html...
Generating /Users/joschi/src/maven-javadoc-aggregate-jar/target/apidocs/help-doc.html...
[INFO] Building jar: /Users/joschi/src/maven-javadoc-aggregate-jar/target/parent-1.0.0-SNAPSHOT-javadoc.jar
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Summary for parent 1.0.0-SNAPSHOT:
[INFO] 
[INFO] parent ............................................. SUCCESS [  1.496 s]
[INFO] a .................................................. SUCCESS [  0.006 s]
[INFO] b .................................................. SUCCESS [  0.006 s]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  2.070 s
[INFO] Finished at: 2019-05-01T12:09:54+02:00
[INFO] ------------------------------------------------------------------------
# ls target/*.jar
parent-1.0.0-SNAPSHOT-javadoc.jar
```