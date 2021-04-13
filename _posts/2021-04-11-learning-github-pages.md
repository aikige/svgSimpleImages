# Learnig GitHub Pages

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
