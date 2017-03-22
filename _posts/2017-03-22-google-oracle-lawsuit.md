---
layout: post
title:  "Google與Oracle的官司"
date:   2017-03-22
categories: android
---

上週開始的Java新班課程, 在介紹一些Java的過去的歷史, 提到Oracle與Google針對Android作業系統的官司.
雖然提到了整個官司的發展及現狀, 但是針對整件官司的癥結自己也說不上真正了解. 於是又在這個事件上做了一些探究.
也利用這個機會, 深入去了解開放原始碼的幾種授權方式. 

先整理一下這場官司的演進.

Google在2007年11月發布Android SDK, 其中包含了Apache Harmony這套open source的Java APIs. 但是早在當年的4月, Apache Software Foundation(ASF)就已經針對Sun Microsystems(後文簡稱Sun)遲遲無法提供給它們關於Java SE 5的Technology Compatibility Kit(TCK)的授權, 提出過一封公開信給當時的Sun CEO, Jonathan Schwartz. 但是卻得不到Sun的回應. 

這邊先解釋什麼是[Technology Compatibility Kit(TCK)](https://en.wikipedia.org/wiki/Technology_Compatibility_Kit). TCK是一組測試軟體相容性的軟件, 專指Java上用來檢核針對某一Java Specification Request(JSR)所開發出來的API的實作(implementations)是否與JSR的規格相符合. 因此這是一組很重要的工具, 有了它才能夠用來驗證並且通過相容性測試. 

Sun當時為何不提供給ASF他們想要的授權呢? 原因在於早在2006年, Sun就已經開始進行一套open source版本的Java的開發, 稱為OpenJDK. 它採用的授權方式為GNU General Public License(GNU GPL) with linking exception. 先來說說這個授權方式.

GPL授權的特點是採用所謂的[Copyleft](https://zh.wikipedia.org/wiki/Copyleft)的概念, Copyleft延伸自Copyright(版權)這個字, 一個是右(right), 一個是左(left), 因此Copyleft要來挑戰當時版權法的一些作為. 它主要是允許個人無限制的使用, 更改, 散布自由軟體, 但是使用者所作的更改後的結果, 也必須採用同樣的授權方式貢獻出來回饋給open source社群. 最成功的Copyleft的自由軟體就是Linux作業系統.

因此Sun採用GPL授權方式的如意算盤就是一方面藉由open source社群的力量, 壯大Java的內容與應用範圍. 另一方面, 也限制可能的競爭對手利用Java技術來與自己競爭.

而ASF的Harmony project所使用的授權方式[Apache software license(ASL)](https://en.wikipedia.org/wiki/Apache_License)則與GPL不同. 雖然也是開放軟體的授權, 但是它僅僅要求維持ASL的版權宣告. ASL不像Copyleft的授權方式, 它不需要更改過後的軟體延續ASL的授權方式, 因此對於使用ASL授權方式軟體的公司來說, 有更大的彈性與誘因, 因為這些公司可以使用open source software來發展磚有的軟體. 
