[![Build Status](https://travis-ci.com/chrisgleissner/java-json-benchmark.svg?branch=master)](https://travis-ci.com/chrisgleissner/java-json-benchmark)

# Benchmark of Java JSON libraries

## Purpose

This project benchmarks the throughput performance of a variety of Java Json libraries using [JMH](http://openjdk.java.net/projects/code-tools/jmh/).
It covers the following libraries:

* [jackson](https://github.com/FasterXML/jackson)
* [yasson](https://github.com/eclipse-ee4j/yasson)

## Changes of this fork

The project is a fork of https://github.com/fabienrenaud/java-json-benchmark with the following changes:
* Updated versions of aforementioned frameworks
* Removed jsoniter references which no longer successfully test under JDK 11

## Results

The benchmarks are written with [JMH](http://openjdk.java.net/projects/code-tools/jmh/) and for Java 11.

The results here-below were computed on 15 January 2020 with the following libraries and versions, using Amazon Corretto JDK 11.0.5 on a Intel(R) Core(TM) i7-4700MQ CPU @ 2.40GHz and a 2GB heap.

Framworks tested:

| Library      | Version  |
|--------------|----------|
| jackson      | 2.10.1   |
| yasson       | 1.0.5    |

### Serialization 

```
./run ser --apis databind --libs yasson,jackson --datatype users

Benchmark                           Mode  Cnt       Score       Error  Units
Serialization.jackson              thrpt   20  779908.289 ± 30329.126  ops/s
Serialization.jackson_afterburner  thrpt   20  808370.633 ± 44998.978  ops/s
Serialization.yasson               thrpt   20  366559.302 ±  7086.764  ops/s
```

### Deserialization

```
./run deser --apis databind --libs yasson,jackson --datatype users

Benchmark                             Mode  Cnt       Score       Error  Units
Deserialization.jackson              thrpt   20  492959.325 ±  9840.536  ops/s
Deserialization.jackson_afterburner  thrpt   20  566521.215 ± 26231.949  ops/s
Deserialization.yasson               thrpt   20  129832.861 ±  6710.096  ops/s
```
