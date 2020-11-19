---
layout: post
title: "Just a Blog Post"
author: "Maxim"
categories: android
tags: [kotlin,android]
image: cutting.jpg
---

"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."

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

"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
