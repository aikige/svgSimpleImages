---
layout: post
title: Learning GitHub Pages
---

# Learnig GitHub Pages

## 基本方針

1. ローカルの検証に便利そうなので、Jekyll の実行環境を整える。
1. ローカルの環境は Docker を使うと取り回しが楽そうなので Docker を使う。Docker Image は公式のもの [jekyll/jekyll](https://hub.docker.com/r/jekyll/jekyll) を利用する。 
    * 参考: [JekyllをDokcer上で動かしてGitHub Pagesのローカル環境での確認を楽する](https://qiita.com/shifumin/items/8d5d26dfa18d4b62d873)

## Setup

### Windows 10 Home で Docker を使う

基本参考文献: [Install Docker Desktop on Windows](https://docs.docker.com/docker-for-windows/install/)

1. Windows 10 Home で WSL2 を有効にする:
    * [Windows Subsystem for Linux Installation Guide for Windows 10](https://docs.microsoft.com/en-us/windows/wsl/install-win10) を参考に WSL2 を有効にする。
1. Docker をインストールする

## Know How

### index.html は何から生成されるか？

* GitHub Pages では [jekyll-readme-index](https://github.com/benbalter/jekyll-readme-index) が有効になっているので、`README.md` が `index.html` に変換される。この仕様は GitHub の性質に合致している。
    * index.md / index.html がレポジトリにある場合は、 `README.md` は無視されることになる。
    * GitHub Pages で有効になっているプラグインは、以下を参照:
        * About GitHub Pages and Jekyll > [Pugins](https://docs.github.com/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll#plugins)


## 参考文献

* [GitHub Pagesのアクセス管理](https://github.blog/jp/2021-01-25-access-control-for-github-page/)
