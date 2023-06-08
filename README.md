# Installation

## For Server Owners

## For Developers

How to Add MagmaKT to your Gradle Project

### Add MagmaKT via GitHub (Recommended)

{% hint style="info" %}
Make sure that the environment variables of your system are set correctly.
{% endhint %}

```gradle
// Add Kotlin and Kapt for Annotation Processing
plugins {
    id "org.jetbrains.kotlin.jvm" version "1.8.20"
    id "org.jetbrains.kotlin.kapt" version "1.8.20"
}
```

```gradle
// Add the Github and the Jitpack Maven repository
repositories {
    maven {
        url = uri("https://maven.pkg.github.com/JaLuMu/MagmaKT")
        credentials {
            username = project.findProperty("gpr.user") ?: System.getenv("USERNAME")
            password = project.findProperty("gpr.key") ?: System.getenv("TOKEN")
        }
   }
   
    maven { url 'https://jitpack.io' }
   
}
```

Replace \<version> with the latest listed on Github

```gradle
// Add the dependency
dependencies {
    // Crossplatform Magma-Api
    compileOnly 'de.jalumu.magma:magma-api:<version>'
    
    // Add Platform specific code
    compileOnly 'de.jalumu.magma:magma-platform-bukkit:<version>'
    compileOnly 'de.jalumu.magma:magma-platform-bungee:<version>'
    
    // Add Annotations
    compileOnly 'de.jalumu.magma:magma-annotations-bukkit-platform:<version>'
    compileOnly 'de.jalumu.magma:magma-annotations-bungee-platform:<version>'
    
    // Add Annotation Processor
    kapt 'de.jalumu.magma:magma-annotations-bukkit-platform:<version>'
    kapt 'de.jalumu.magma:magma-annotations-bungee-platform:<version>'
}
```

### Add MagmaKT via Jitpack

```gradle
// Add Jitpack repository
repositories {
    maven { url 'https://jitpack.io' }
}
```

```gradle
// Add dependency
dependencies {
    compileOnly 'de.jalumu:MagmaKT:main-SNAPSHOT'
}
```
