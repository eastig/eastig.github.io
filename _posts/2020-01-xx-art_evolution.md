---
published: false
layout: post
title: The Evolution of the Android Runtime (ART)
---
The history of the Android Runtime started with Dalvik in November, 2007. This is when the Android beta was publicly released. BTW, Dalvik is a village in Iceland. At that time devices powered by a battery had slow CPUs and little RAM. 

Android applications are mostly developed in Java and the system Java libraries are quite big. This means you need to do something with them to meet memory constraints. To do so Dalvik creators chose own format for apps code: DEX (Dalvik EXecutable). According to data they presented in 2008, the size of an app uncompressed dex file is less than the size of an app compressed jar file which is generally about half the size of app uncompressed Java class files. The size of an uncompress dex file is important because an uncompress dex file can be mapped into memory shared among apps, a technique used to save additional system memory.

Another solution to save more memory was the Zygote process. It starts when the Android boots and waits for requests to run an app. A request causes the Zygote process to create a copy of itself. As the Zygote process preloads libraries and precreates heap structures, all of them are shared among created copies. Not only read-only resources are shared, resources, that can be modified, are also shared. Modifications of such resources just cause copy-on-write actions. Of course such resources should not be too many because copy-on-write could be expensive.

Initially Dalvik did not have a just-in-time compiler, only an interpreter, because JIT consumes RAM and CPU. You also don't need JIT if you spend most of execution time in native code. This was the case for Android, a lot of native code.
