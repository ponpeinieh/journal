---
layout: post
title:  "第一次使用Jekyll"
date:   2017-03-20
categories: github
---
上一篇的[契子]({{site.baseurl}}{% post_url 2017-03-21-github-page-jekyll %})一文中, 提及的Jekyll這套blog網頁產生工具, 這裡進一步來其中的玄妙

## _config.yml

`_config.yml`是Jekyll的主要設定檔, 預設內容如下:
{% highlight yaml linenos %}
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
# you will see them accessed via {{ site.title }}, {{ site.email }}, and so on.
# You can create any custom variable you would like, and they will be accessible
# in the templates via {{ site.myvariable }}.
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

其中比較重要的設定:
- `theme: minima` : `minima`是jekyll的預設主題, 它安裝的路徑可以利用`bundle show minima`指令取得. 
檢視minima安裝路徑下的`_layouts/`目錄, 可以看到它包含了四個定義好的layouts: `default, home, page, post`. 
(原本我在GitHub page中選擇的theme是`jekyll-theme-midnight`, 它下面的layout只有default一項. 為了方便, 還是繼續用minima)
default layout是最基本的layout, 其他三個layouts都是架構在這個上面, 然後做一些改變. 
home用在入口網頁index.md, page用在一般的html檔案(利入about.md), post則用在所寫的post上.
Jekyll產生出來的網頁, footer的部份, 預設設計將blog title重複顯示, 因為我的title用的是一句詩詞, 
感覺過於重複與顯眼, 所以我改寫了footer.html(位在minima安裝路徑下的`_includes`目錄下)

曾經嘗試要將theme換成`jekyll-theme-midnight`, 但是如上段文章所說, 因為這個theme只有一個default layout, 
所以除非將minima中的home,page, post等layouts, 複製到我的blog site檔案根目錄, 否則會有錯誤. 所以避免麻煩,
我還是沿用minima theme. 不過這裡也提一下更換theme的幾個步驟:
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

最後, 將project中的檔案deploy到GitHub page去, 注意還有一個設定要改變: 在Gemfile中做以下兩個更新:
-移除`gem "jekyll"`
-加上`gem 'github-pages'`
最後執行 `bundle update github-pages`


:sweat_smile:


