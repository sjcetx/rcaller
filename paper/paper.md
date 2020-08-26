---
title: 'RCaller: A Java package for interfacing R'
tags:
  - R
  - Java
  - statistics
  - data science
authors:
  - name: Mehmet Hakan Satman
    orcid: 0000-0002-9402-1982
    affiliation: 1
affiliations:
 - name: Department of Econometrics, Istanbul University
   index: 1
date: 24 August 2020
bibliography: paper.bib
---

# Summary
Nowadays, the interest on statistical computation and data analysis increased the popularity of some programming languages such as R, Python, and Julia. As a result of popularity, hundreds of packages are developed for these targeted languages. On the other side, many mainframe languages are adopted for more specific tasks in server-side or the general-purpose use in several platforms. Interaction between those languages became a major requirement due to the lack of modern statistical tools written in the general-purpose languages such as Java. Renjin [@renjin] is a great effort for interfacing R from within Java using a different persfective: Writing R from scratch in Java! GraalVM [@graalvm] is an other admirable attempt for interfacing Python and R in Java with its polyglot design. Many tools and software packages are developed for interfacing R and Java. Each one stands out with its different features including speed, installation procedures, learning speed, and ease of use. 


# Statement of need 
RCaller is a Java library for interfacing R from within Java [@satman2014rcaller]. R is a popular programming language and a programming environment with hundreds of packages written in C, C++, Fortran, and R itself [@rcoreteam]. These huge collection of computation tools are not directly accessible for the other languages, especially for Java. RCaller supplies a clean API for calling R functions, managing interactions, and transfering objects between languages. There are other options in the literature including Rserve [@urbanek2003fast] and rJava [@urbanek2009talk] which are based on TCP sockets and JNI (Java Native Interface), respectively. RCaller provides a set of easier calling schemes without any dependencies. Previous works showed that the performance of the library is suitable for more cases and studies with moderate datasets can be handled in reasonable times [@satmancurcean2016].


# Java scripting interface
RCaller also implements the scripting API of Java (JSR 223). In other words, the engine behaves like a Java implementation of R. Here is an example of sorting a Java array in R side and handling the result in 
Java:

```Java
ScriptEngineManager manager = new ScriptEngineManager();
ScriptEngine en = manager.getEngineByName("RCaller");
double[] a = new double[]{19.0, 17.0, 23.0};
engine.put("a", a);
engine.eval("a <- sort(a)");
double[] result = (double[]) engine.get("a");
```

RCaller, as a scripting engine in Java, creates an R process, encodes Java objects to XML, runs commands in R side, gets back the results as XML, and parses the result to Java objects. Since a single R process is created and used for consecutive calls, XML parsing is the only calculation overhead.

# Acknowledgements

We acknowledge contributions from Paul Curcean, Miroslav Batchkarov, Kopilov Aleksandr, Joel Wong, Kejo Starosta, Steven Sotelo, Edinei Piovesan, and others of this project.

# References
