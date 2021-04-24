---
title: Learnig GitHub Pages
---

## Setup

### Jekyll 設定

以下の設定は Widnows で実施しています。

前提条件: Rubyはインストール済み。

1. 必要なものをインストールする

    ```
    gem install jekyll bundler
    ```

1. 既存のプロジェクトを Jekyll 対応にする場合:

    ```
    jekyll new --force .
    ```

1. 以下のファイルができる

    * `Gemfile`
    * `Gemfile.lock`
    * `_config.yml`
    * `about.markdown`
    * `index.markdown`

1. [GitHub Pages のガイドライン]() に従って、`Gemfile` を編集する：

    1. `gem "jekyll", "~> 4.*.*"` の部分をコメントアウト
    1. `gem "github-pages", group: :jekyll_plugins` の部分を有効にする。

1. Bundle 設定に従って更新する

    ```
    bundle udpate
    ```

1. お試し

    ```
    bundle exec jekyll server
    ```

    * エラーが出る:

    ```
    C:/Ruby30-x64/lib/ruby/gems/3.0.0/gems/jekyll-3.9.0/lib/jekyll/commands/serve/servlet.rb:3:in `require': cannot load such file -- webrick (LoadError)
    ```

    * `gem "webrick"` を Gemfile に追加する


## Docker を使う場合の Setup

### Windows 10 Home で Docker を使う

基本参考文献: [Install Docker Desktop on Windows](https://docs.docker.com/docker-for-windows/install/)

1. Windows 10 Home で WSL2 を有効にする:
    * [Windows Subsystem for Linux Installation Guide for Windows 10](https://docs.microsoft.com/en-us/windows/wsl/install-win10) を参考に WSL2 を有効にする。
        1. `dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart`
        2. `dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart`
        3. Download the Linux kernel update package
1. Docker をインストールする
    * 問題:
        1. Virturization Technologyがないと言われる -- BIOSを設定してVirturizationをONにする。
            * 対策: 利用しているASUSのPCの場合、以下の設定が必要（VMS ONだけだとブートしなくなった）
                * VMS Technology: ON (Default OFF)
                * Frame Buffer Size: Auto (Defaultは512だった)
            * 参考文献:
                * 
        1. 通常ユーザ（※私は普段、管理者権限がないユーザでログインしている）でログインした際に、
            以下のようなポップアップが表示されるが、Windows 10 Home の場合、グループポリシーのGUIが無い。

            > You are not allowed to use Docker, You must be in the "docker-users" group.

            * 対策: `net localgroup` コマンドを利用してユーザを追加する。
                
                1. コマンド実行: `net localgroup docker-users YOUR_ID`
                1. ログオフ
                1. ログオン

            * 参考文献:
                * Qiita > [Docker for Windowsで起動時に「Docker for Windows - Access denied」と表示される場合の対処法](https://qiita.com/toro_ponz/items/d75706a3039f00ba1205)
                * Windowsコマンド虎の巻 > [net localgroup](https://windows.command-ref.com/cmd-net-localgroup.html) 

## Know How

### index.html は何から生成されるか？

* GitHub Pages では [jekyll-readme-index](https://github.com/benbalter/jekyll-readme-index) が有効になっているので、`README.md` が `index.html` に変換される。この仕様は GitHub の性質に合致している。
    * index.md / index.html がレポジトリにある場合は、 `README.md` は無視されることになる。
    * GitHub Pages で有効になっているプラグインは、以下を参照:
        * About GitHub Pages and Jekyll > [Pugins](https://docs.github.com/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll#plugins)


## 参考文献

* [GitHub Pagesのアクセス管理](https://github.blog/jp/2021-01-25-access-control-for-github-page/)

* [Bundler](https://bundler.io/)
