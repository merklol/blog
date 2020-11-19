---
layout: post
title: "Test MaximCode Blog Post"
author: "Maxim"
categories: android
tags: [kotlin,android]
image: cutting.jpg
related: 
---

Lagrange is a minimalist Jekyll theme. The purpose of this theme is to provide a simple, clean, content-focused blogging platform for your personal site or blog. Below you can find everything you need to get started.

Getting Started

Getting Started: getting started with installing Lagrange, whether you are completely new to using Jekyll, or simply just migrating to a new Jekyll theme.

```kotlin
class ConsolePrinter(override val rule: Rule = DebugRule()): Printer {
    override val tag: Tag
        get() = KLoggerTag(mutableListOf(
        ConsolePrinter::class.java.name,
        KLogger::class.java.name,
        KLoggerTag::class.java.name,
        String::class.java.name,
        StringBuilder::class.java.name
    ), BaseTemplate())

    override fun log(
        priority: Int, message: String?, throwable: Throwable?) {
        when (priority) {
            KLogger.VERBOSE -> 
                print("V/$tag", message, throwable, Color.BLACK)
            KLogger.DEBUG -> 
                print("D/$tag", message, throwable, Color.BLACK)
            KLogger.INFO -> 
                print("I/$tag", message, throwable, Color.BLACK)
            KLogger.WARN -> 
                print("W/$tag", message, throwable, Color.BLUE)
            KLogger.ERROR -> 
                print("E/$tag", message, throwable, Color.RED)
            KLogger.ASSERT -> 
                print("A/$tag", message, throwable, Color.RED)
        }
    }

    private fun print(stringTag: String, message: String?, 
        t: Throwable?, color: Color) {
        when {
            message.isNullOrBlank() ->
                println("$stringTag: ${t!!.toStackTraceString()}".colorize(color.code))
            throwable.isNull() ->
                println("$stringTag: $message".colorize(color.code))
            else ->
                println(
                    "$stringTag: $message\n${t!!.toStackTraceString()}".colorize(color.code))
        }
    }
}
```
