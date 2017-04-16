---
layout: post
title:  Auto login for multiple github accounts and repositories
date:   2017-04-11
categories: github
---

因為老是會忘記這個動作要怎麼設定, 也許是人經歷的世事多了, 腦子混沌了. 

基本上就是我有多個github accounts, 每一個account內又有多個repositories. 每次做`git push origin master`, 最好是不要輸入github的帳號密碼.

## Multiple Accounts
首先是multiple accounts的設定, 假設我的兩個accounts分別為`john.github.com`及`andrew.github.com`:


1. 首先是替每一個account建立一組ssh keys: `ssh-keygen -t rsa -C "comments_here" -f "file_name_for_key_pair"`. 每一組public/private key會產生在`~/.ssh/`目錄下.

```
 ssh-keygen -t -rsa -C "john.github.com" -f "github-john"
 ssh-keygen -t -rsa -C "andrew.github.com" -f "github-andrew"
```

2. 在github內加入上述產生的public key. 可以參考GitHub docs [here](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/).

3. 在`~/.ssh/`下建立`config`一檔案, 輸入以下內容:

```
#john account
Host john.github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/github-john

#andrew account
Host andrew.github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/github-andrew
```

4. 對於每一個account下的repository, 設定git remote url. 可以先檢視目前的設定:`git remote -v`

```
git remote set-url origin git@john.github.com:john/<your-repo-name.git>
```

```
git remote set-url origin git@andrew.github.com:andrew/<your-repo-name.git>
```

## Multiple Repositories

再來看如果是multiple repositories, 假設我的account`john.github.com`下有兩個repositories `python`, `java`

1. 首先是替每一個repository建立一組ssh keys: `ssh-keygen -t rsa -C "comments_here" -f "file_name_for_key_pair"`. 每一組public/private key會產生在`~/.ssh/`目錄下

```
 ssh-keygen -t -rsa -C "john1.github.com" -f "github-john1"
 ssh-keygen -t -rsa -C "john2.github.com" -f "github-john2"
```

2. 在github的每一個repository內加入上述產生的public key. 可以參考GitHub docs [here](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/).

3. 在`~/.ssh/`下建立`config`一檔案, 輸入以下內容

```
#john1 repository
Host john1.github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/github-john1

#john1 repository
Host john2.github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/github-john2

```

4. 對於每一個repository, 設定`git remote url`. 可以先檢視目前的設定:`git remote -v`

```
git remote set-url origin git@john1.github.com:john/john1.git
```

```
git remote set-url origin git@john2.github.com:john/john2.git
```

備註: 
- 注意remote url的`@`與`:`之間的內容, 必須與`~/.git/config`中的設定的`Host`設定相同.
- `:`後面的是account名稱, 所以都是john


:sweat_smile:
