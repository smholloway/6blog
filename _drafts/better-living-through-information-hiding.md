---
layout: post
category: technology
tags: [java, ide]
title: Better Living Through Information Hiding
author: Seth and Nick
---
{% include JB/setup %}

Java has a lot of things going for it, but Java is ceremonial, to say the least. Scala sells the fact that Scala programs are shorter than equivalent Java programs. Rubyists love the fact that Ruby programs are significantly terser than Java. Functional people point to programs that are more concise thanks to map, reduce, function objects, and clojures.

To reduce the visual noise, I think we should apply classic information hiding techniques to Java code.

## Example

```java
public class Main
  public static void main (String... args) {
    // main
  }
}
```

```java
Main
  main (args) {
    // main
  }
}
```

In Java the [valid modifiers](http://docs.oracle.com/javase/tutorial/reflect/class/classModifiers.html) for a class are

  - Access modifiers: `public`, `protected`, and `private`
  - Modifier requiring override: `abstract`
  - Modifier restricting to one instance: `static`
  - Modifier prohibiting value modification: `final`
  - Modifier forcing strict floating point behavior: `strictfp`

There are 8 options, which could be encoded as colors.

There are 8 primitives, which could be considered numeric (byte, short, int, long, float, double), boolean, and string (char, and maybe String). In addition, there are custom classes and base Objects. All told, that's five options that could be encoded in color.

## How to Encode Extra Information

Encoding information in text is nothing new.

### Font

People are partial to their editor fonts, so I'm not sure how much room there is here. That being said, font could encode additional information. Perhaps comments could be serif while code maintains the familiar sans-serif.

### Style

Bold, italic, underline, and strikethrough. Smallcaps might also work.

### Color

Background and foreground colors. The [Railscasts theme](https://github.com/talltroym/sublime-theme-railscasts/blob/master/RailsCastsColorScheme.tmTheme) already has about 30 color definitions, so there is precedent for using color.

You could also hide type information like collapsed comments. On hover, reveal complete information.

## Notes

I'm not sure you could get around typing `public static void main(String... args)`, but I believe you could shorten the display to `main(args)` with simple information hiding.

I could see this working like collapsing/folding methods. Enter a key combination and your code is now concise--ideal for simply reading.
