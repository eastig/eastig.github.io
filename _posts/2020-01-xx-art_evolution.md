---
published: false
layout: post
title: The Evolution of the Android Runtime (ART)
---
The history of the Android Runtime started with Dalvik in November, 2007. This is when the Android beta was publicly released. BTW, Dalvik is a village in Iceland. At that time devices powered by a battery had slow CPUs and little RAM. Android applications are mostly developed in Java and the system Java libraries are quite big. This means you need to do something with them to meet memory constraints. To do so Dalvik creators chose own format for apps code: DEX (Dalvik EXecutable). According to data they presented in 2008, the size of an app uncompressed dex file is less than the size of an app compressed jar file which is generally about half the size of app uncompressed Java class files.
