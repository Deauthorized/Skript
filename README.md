# Skript [![Build Status](https://travis-ci.org/SkriptLang/Skript.svg?branch=master)](https://travis-ci.org/SkriptLang/Skript)
Skript is a plugin for Bukkit/Spigot, which allows server owners and other people
to modify their servers without learning Java. It can also be useful if you
*do* know Java; some tasks are quicker to do with Skript, and so it can be used
for prototyping etc.

This Github fork of Skript is based on Mirreski's improvements which was built
on Njol's original Skript.

## Requirements
Skript requires **Spigot** to work. You heard it right, Bukkit does *not* work.
**Paper**, which is a fork of Spigot, is recommended; it is required for some
parts of Skript to be available.

Skript supports only the **latest** patch versions of Minecraft 1.9, 1.10, 1.11, 1.12 and 1.13.
For example, this means that 1.12.2 is supported, but 1.12.1 is *not*.
Testing with all old patch versions is not feasible for us.

Minecraft 1.8 and earlier are not, and will not be supported. New Minecraft
versions will be supported as soon as possible.

## Download
You can find the downloads for each version with their release notes in the [releases page](https://github.com/SkriptLang/Skript/releases).

## Documentation
Documentation is available [here](https://skriptlang.github.io/Skript) for the
latest version of Skript.

## Reporting Issues
Please see our [contribution guidelines](https://github.com/SkriptLang/Skript/blob/master/.github/CONTRIBUTING.md)
before reporting issues.

## A Note About Add-ons
We don't support add-ons here, even though some of Skript developers have also
developed their own add-ons.

## Compiling
Skript uses Gradle for compilation. Use your command prompt of preference and
navigate to Skript's source directory. Then you can just call Gradle to compile
and package Skript for you:

```bash
./gradlew clean build # on UNIX-based systems (mac, linux)
gradlew clean build # on Windows
```

You can get source code from the [releases page](https://github.com/SkriptLang/Skript/releases).
You may also clone this repository, but that code may or may not be stable.

### Compiling Modules
Parts of Skript are provided as Gradle subprojects. They require Skript, so
they are compiled *after* it has been built. For this reason, if you want them
embedded in Skript jar, you must re-package it after compiling once. For example:

```
./gradlew jar
```

Note that modules are not necessary for Skript to work. Currently, they are
only used to provide compatibility with old WorldGuard versions.

### Importing to Eclipse
With new Eclipse versions, there is integrated Gradle support, and it actually works now.
So, first get latest Eclipse, then import Skript as any Gradle project. Just
make sure to **keep** the configuration when the importer asks for that!

If you encounter strange issues, make sure you follow the instructions above and have
actually downloaded latest Eclipse or update your installation correctly. Skript's
new Gradle version (starting from dev26) does not work very well with older Eclipse
versions. Also, do *not* use Gradle STS; it is outdated.

### Importing to IDEA
You'll need to make sure that nullness annotations are working correctly. Also,
when sending pull requests, make sure not to change IDEA configuration files
that may have been stored in the repository.

### Releasing
```
./gradlew clean build
./gradlew <flavor>Release
```
Available flavors are github and spigot. Please do not abuse flavors by
compiling your own test builds as releases.

## Contributing
Please review our [contribution guidelines](https://github.com/SkriptLang/Skript/blob/master/.github/CONTRIBUTING.md).
In addition to that, if you are contributing Java code, check our
[coding conventions](https://github.com/SkriptLang/Skript/blob/master/CODING_CONVENTIONS.md).

## Maven Repository
If you use Skript as (soft) dependency for your plugin, and use maven or Gradle,
this is for you.

First, you need to add the JitPack repository at the **END** of all your repositories. Skript is not available in Maven Central.
```gradle
repositories {
    jcenter()
    ...
    maven {
        url 'https://jitpack.io'
    }
}
```

Or, if you use Maven:
```maven
<repositories>
    <repository>
        <id>jitpack.io</id>
        <url>https://jitpack.io</url>
    </repository>
</repositories>
```

For versions of Skript after dev37 you might need to add the paper-api repository to prevent build issues.

```gradle
maven {
    url 'https://repo.destroystokyo.com/repository/maven-public/'
}
```

Or, if you use Maven:
```maven
<repository>
    <id>destroystokyo-repo</id>
    <url>https://repo.destroystokyo.com/content/repositories/snapshots/</url>
</repository>
```

Then you will also need to add Skript as a dependency.
```gradle
dependencies {
    implementation 'com.github.SkriptLang:Skript:[versionTag]'
}
```

An example of the version tag would be ```dev37c```.

> Note: If Gradle isn't able to resolve Skript's dependencies, just [disable the resolution of transitive dependencies](https://docs.gradle.org/current/userguide/managing_transitive_dependencies.html#sub:disabling_resolution_transitive_dependencies) for Skript in your project.

Or, if you use Maven:
```
<dependency>
    <groupId>com.github.SkriptLang</groupId>
    <artifactId>Skript</artifactId>
    <version>[versionTag]</version>
</dependency>
```

## Relevant Links
* [skUnity forums](https://forums.skunity.com)
* [Add-on releases at skUnity](https://forums.skunity.com/forums/addon-releases)
* [Skript Chat Discord invite](https://discord.gg/0lx4QhQvwelCZbEX)
* [Skript Hub](https://skripthub.net)
* [Original Skript at Bukkit](https://dev.bukkit.org/bukkit-plugins/skript) (inactive)

Note that these resources are not maintained by Skript's developers. Don't
contact us about any problems you might have with them.

## Developers
Current team behind Skript:

* [bensku](https://github.com/bensku) (Skript maintainer/developer)
* [FranKusmiruk](https://github.com/FranKusmiruk) (Skript developer)
* [Pikachu920](https://github.com/Pikachu920) (Skript developer)
* [Nicofisi](https://github.com/Nicofisi) (Skript developer)
* [TheBentoBox](https://github.com/TheBentoBox) (issue tracker manager, aliases developer)

We should also thank [Njol](https://github.com/Njol) for creating
Skript and [Mirreski](https://github.com/Mirreski) for maintaining it for a
long time.

And of course, Skript has received lots of pull requests over time.
You can find all contributors [here](https://github.com/SkriptLang/Skript/graphs/contributors).

All code is owned by its writer, licensed for others under GPLv3 (see LICENSE)
unless otherwise specified.
