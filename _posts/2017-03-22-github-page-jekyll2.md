---
layout: post
title:  "第一次使用Jekyll"
date:   2017-03-22
categories: github
---
上一篇的[契子]({{site.baseurl}}{% post_url 2017-03-21-github-page-jekyll %})一文中, 提及的Jekyll這套blog網頁產生工具, 這裡進一步來看其中的玄妙

## Jekyll專案設定檔

`_config.yml`是每一個Jekyll project的主要設定檔, 預設內容如下:
{% highlight yaml %}
# Welcome to Jekyll!
#
# This config file is meant for settings that affect your whole blog, values
# which you are expected to set up once and rarely edit after that. If you find
# yourself editing this file very often, consider using Jekyll's data files
# feature for the data you need to update frequently.
#
# For technical reasons, this file is *NOT* reloaded automatically when you use
# 'bundle exec jekyll serve'. If you change this file, please restart the server process.

# Site settings
# These are used to personalize your new site. If you look in the HTML files,
# you will see them accessed via {% raw %} {{ site.title }}, {{ site.email }} {% endraw %}, and so on.
# You can create any custom variable you would like, and they will be accessible
# in the templates via {% raw %}{{ site.myvariable }} {% endraw %}.
title: Your awesome title
email: your-email@domain.com
description: > # this means to ignore newlines until "baseurl:"
  Write an awesome description for your new site here. You can edit this
  line in _config.yml. It will appear in your document head meta (for
  Google search results) and in your feed.xml site description.
baseurl: "" # the subpath of your site, e.g. /blog
url: "" # the base hostname & protocol for your site, e.g. http://example.com
twitter_username: jekyllrb
GitHub_username:  jekyll

# Build settings
markdown: kramdown
theme: minima
gems:
  - jekyll-feed
exclude:
  - Gemfile
  - Gemfile.lock

{% endhighlight %}

其中比較重要的設定是`theme` 

## Jekyll 主題（theme)

`minima`是Jekyll project的預設主題, 它安裝的路徑可以利用`bundle show minima`指令取得. 
檢視minima安裝路徑下的`_layouts/`目錄, 可以看到它包含了四個預設的layouts: `default, home, page, post`. 
(原本我的project在GitHub page中選擇的theme是`jekyll-theme-midnight`, 但是它包含的layout只有default一項. 為了方便, 還是繼續用minima)

- default layout 是最基本的layout, 其他三個layouts都是架構在這個上面, 然後做一些改變
- home layout 用在入口網頁上, 如index.md
- page layout 用在一般的html page, 例如about.md
- post layout 用在所撰寫的post上

## 客製化project內容或template

Jekyll產生器所產生的網頁, 每一頁底的footer的部份, 預設設計將project title重複顯示, 因為我的project title用的是一句詩詞, 
感覺過於重複與顯眼, 所以想改變其內容. 如何客製化這個footer呢? 可以將相關的檔案(footer.html, 位在minima安裝路徑下的`_includes`目錄下)
複製到project的目錄下, 一樣放在_includes目錄中, 然後隨你要的方式去改變其內容. 

曾經嘗試要將theme換成`jekyll-theme-midnight`, 但是如上段文章所說, 因為這個theme只有一個default layout, 
所以除非將minima中的home,page, post等layouts, 複製到我的project目錄中, 
否則index.md, about.md等檔案會因為找不到相關的layouts而有錯誤. 可能還有_includes中的一些檔案也要複製才行. 因此為了避免麻煩,
我還是沿用minima theme. 

## 更換Jekyll theme

不過這裡還是提一下, 若要更換theme可採以下步驟:
1. 將新的theme加入到Gemfile檔案:
```
gem "jekyll-theme-awesome"
```
1. 安裝theme:
```
bundle install
```
1. 更新_config.yml以啟用該theme:
```
theme: jekyll-theme-awesome
```
1. 重新build site:
```
bundle exec jekyll serve
```

## Deploy project到GitHub page
將project中的檔案deploy到GitHub page去, 須更改Gemfile中的設定:
- 移除`gem "jekyll"`
- 加上`gem 'github-pages'`

存檔後, 執行 `bundle update github-pages`

## 使用emoji 

Jekyll page中可以使用Emoji圖示, 設定如下:
1. 在_config.yml設定檔中加入
```
gems:
  - jemoji
```
1. Gemfil中加入:
```
gem 'jemoji'
```
1. emoji的格式為`:<code>:`, 例如 :sweat_smile: 

請參考[emoji cheat sheet](https://www.webpagefx.com/tools/emoji-cheat-sheet/)


