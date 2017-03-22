---
layout: post
title:  "契子"
date:   2017-03-21
categories: github
---

自二月底開始, 在公司教幾位高中學生Python語言. 算一算自己從2010年開始自學這套語言與相關技術, 也已經七年.
當然自學, 自用, 跟拿來教人是兩件迥然不同的方式. 所以開始真正整理一些資料, 然後再次深入一些應用, 因為之前也只是用在
web應用, 或者數據收集分析. 其實這個語言這幾年一直在[TIOBE網站](https://www.tiobe.com/tiobe-index/)的熱門排名上, 位在前五名, 也是因為它的應用十分廣泛. 
這次就找了一套GUI套件[appJar](http://appjar.info/)以及遊戲套件[pygame](https://www.pygame.org), 希望能夠帶領這首批的學生們進入這個程式設計的領域, 並引起他們後續自我學習的動力.

除了製作教學相關的spreadsheets, 也應用了[cloud9](https://c9.io)這套雲端的IDE系統來撰寫Python程式, 這套系統的使用也值得寫一篇文章來介紹, 這暫且先放著. 

上週某一天, 想起還是要把教學的內容寫到一個blog去, 於是網路上找了一會兒, 發現github page這套, 很快, 熟悉一下markdown的語法, 就陸續將pygame
的介紹, appJar的介紹文發布出來, 只是還在納悶要怎麼方便製作一個完整的blog網站, 總要有一個index頁面的入口吧!
於是昨日開始, 將[Jekyll](https://jekyllrb.com/)下載安裝, 這套就是github page後台用來將原始檔案, 轉換產生整個靜態網頁的一套工具. 以下就紀錄一下昨天開始所進行的一些安裝與設定步驟:

Jekyll是以Ruby所寫的, 因此需要先安裝Ruby及RubyGems, 所以在我的Ubuntu 16.04系統上我進行了:

## 安裝Ruby並upgrade RubyGems
```
sudo apt-get install ruby-full
sudo gem update --system
```

## 安裝Jekyll
```
sudo gem install jekyll bundler
```

## 建立Jekyll site, 例如 myblog
```
jekyll new myblog
```

## 建置並啟用preview server
```
cd myblog
bundle exec jekyll serve
```

接下來可以用brower打開http://localhost:4000

:sweat_smile:


