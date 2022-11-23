# Compilation issue example

When Apollo plugin is applied in afterEvaluate

```kotlin
project.afterEvaluate {
    pluginManager.apply("com.apollographql.apollo3")
    extensions.configure(com.apollographql.apollo3.gradle.api.ApolloExtension::class.java) {
        service("MyService") {
            packageName.set("com.example.rocketreserver")
        }
    }
}
```
then compilation passes on `3.6.2` Apollo version, but fails with `3.7.1` version.


When configuration is changed to

```kotlin
project.afterEvaluate {
    pluginManager.apply("com.apollographql.apollo3")
    extensions.configure(com.apollographql.apollo3.gradle.api.ApolloExtension::class.java) {
        packageName.set("com.example.rocketreserver")
    }
}

```
then compilation passes on `3.6.2` and `3.7.1`


When Apollo plugin is configured right away, but using `service`
```kotlin
plugins {
    id("com.apollographql.apollo3").version("3.7.1")
}

apollo {
    service("MyService") {
        packageName.set("com.example.rocketreserver")
    }
}

```

then compilation passes on `3.6.2` and `3.7.1`.

# Apollo Kotlin Tutorial

This is the tutorial application for working with the [Apollo Kotlin SDK](https://github.com/apollographql/apollo-kotlin).

The tutorial is available through our documentation site: [Android Tutorial](https://www.apollographql.com/docs/kotlin/tutorial/00-introduction/).

For copy errors in the tutorial, please file bugs against the main [`apollo-android` repo](https://github.com/apollographql/apollo-kotlin). For broken code, please file issues on this repo.

This repo has two branches:

* [main](https://github.com/apollographql/apollo-kotlin-tutorial/tree/main) is the final state of the application with all functionality
* [initial](https://github.com/apollographql/apollo-kotlin-tutorial/tree/initial) is the starter project with the boilerplate and UI code already written but no Apollo Kotlin code.
