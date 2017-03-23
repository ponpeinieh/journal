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

### Sun不提供ASF他們想要的授權
Google在2007年11月發布Android SDK, 其中包含了Apache Harmony這套open source的Java APIs. 但是早在當年的4月, Apache Software Foundation(ASF)就已經針對Sun Microsystems(後文簡稱Sun)遲遲無法提供給他們關於Java SE 5的Technology Compatibility Kit(TCK)的授權, 提出過一封公開信給當時的Sun CEO, Jonathan Schwartz. 但是卻得不到Sun的回應. 

這邊先解釋什麼是[Technology Compatibility Kit(TCK)](https://en.wikipedia.org/wiki/Technology_Compatibility_Kit). TCK是一組測試軟體相容性的軟件, 專指Java上用來檢核針對某一Java Specification Request(JSR)所開發出來的API的實作(implementations)是否與JSR的規格相符合. 因此這是一組很重要的工具, 有了它才能夠用來驗證並且通過相容性測試. 

Sun當時為何不提供給ASF他們想要的授權呢? 原因在於早在2006年, Sun就已經開始進行一套open source版本的Java的開發, 稱為OpenJDK. 它採用的授權方式為GNU General Public License(GNU GPL) with linking exception. 先來說說這個授權方式.

### GPL授權方式
GPL授權的特點是採用所謂的[Copyleft](https://zh.wikipedia.org/wiki/Copyleft)的概念, Copyleft延伸自Copyright(版權)這個字, 一個是右(right), 一個是左(left), 因此Copyleft要來挑戰當時版權法的一些作為. 它主要是允許個人無限制的使用, 更改, 散布自由軟體, 但是使用者所作的更改後的結果, 也必須採用同樣的授權方式貢獻出來回饋給open source社群. 最成功的Copyleft的自由軟體就是Linux作業系統.

因此Sun採用GPL授權方式的如意算盤就是一方面藉由open source社群的力量, 壯大Java的內容與應用範圍. 另一方面, 也限制可能的競爭對手利用Java技術來與自己競爭.

### ASL授權方式
而ASF的Harmony project所使用的授權方式[Apache software license(ASL)](https://en.wikipedia.org/wiki/Apache_License)則與GPL不同. 雖然也是開放軟體的授權, 但是它不像Copyleft, 它不需要更改過後的軟體延續ASL的授權方式, 可以變換成其他授權方式. 因此對於使用ASL授權方式軟體的公司來說, 就有更大的彈性與誘因, 因為這些公司可以使用open source software來發展專屬版權的軟體. 

### OpenJDK, Apache Harmony
接著Sun在2007年5月, 正式發布以OpenJDK, 以及TCK工具的授權, 但是這個TCK授權僅允許以OpenJDK為基礎所衍生出來的其他implementation(在GPL授權方式之下)來使用.

於是在2010年12月, ASF整個退出Java Community Process(JCP)的主要執行委員會, 以表示對這個授權方式的抗議, 因為它已經違反了當初JCP運作的規則. 接著在2011年11月, Apache Harmony project正式宣告退役. 

### Oracle告上Google

Oracle在2010年1月完成Sun的收購, 接手Java的所有權. 這期間雖然Google有與Sun或Oracle談判關於Java的授權, 但都沒有進展. 因此Oracle在2010年8月展開對於Google在Android系統上使用Java的侵權官司. 這個官司牽涉到兩項的專利與API著作權兩個部份. 

在2012年5月的地方法院的宣判結果, 首先關於兩項專利的侵權部份, 認為Google沒有侵犯Oracle的專利. 接著關於APIs的著作權的部份, 認定APIs並不能宣告著作權, 也是Google勝訴.

後來Oracle上訴到了聯邦法院, 於2014年5月宣判, 認定APIs可以作為著作權的範圍. 但是要求將整個案件退回到地方法院, 針對Google侵犯著作權的部份, 是否屬於合理使用(fair use)的範疇做重新審理. 

在2016年5月, 地方法院針對Google重新實作37組Java APIs的部份做出判決, 認定是合理使用, 應該受到保護. Oracle又再度上訴.

:sweat_smile:



