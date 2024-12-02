# LaTeXで論文を書くためのテンプレート

[![Test Docker Image](https://github.com/being24/latex-template-ja/actions/workflows/test.yml/badge.svg)](https://github.com/being24/latex-template-ja/actions/workflows/test.yml)
[![License: CC0-1.0](https://img.shields.io/badge/License-CC0_1.0-lightgrey.svg)](http://creativecommons.org/publicdomain/zero/1.0/)

このLaTeXテンプレートは，[こちら](https://github.com/being24/latex-template-ja)のテンプレートを参考に，本研究室向けに内容を改良したものです．

## Release note

* 2024/10/22 README.mdを増強，トラブルシューティング
* 2024/10/21 各種TeXファイルを作成

## Function

* 個人環境にLaTeX workshopを構築せず、dockerでビルドします
* GitHub Actionsを使用してtextlintを実行します
* github上にreleaseします
* 論文のテンプレートを持ちます

## Environment

* Windows 10 or later
* macOS 10.14 or later
* Ubuntu 18.04 LTS or later

Docker環境が必要です．

* Docker Desktop for Mac 2.1 or later
* Docker 18.06 or later
* Docker Desktop for Windows

windowsの場合は，[こちら](https://docs.docker.com/desktop/install/windows-install/)からDocker Desktop on Windowsをインストールしておいてください．環境変数PATHが正しく設定されていることを確認してください．確認するためには，コマンドプロンプトを開いて
```
docker
```
と入力します．コマンドの説明が出てきたらインストールできています．
あとで[こちらのリポジトリ](https://github.com/being24/latex-docker)のghcr.io/being24/latex-docker を使用します．詳しくは後ほど説明します．

VSCodeが必要です．[こちら](https://code.visualstudio.com/)からインストールしておいてください．

Gitも必要です．[こちら](https://git-scm.com/downloads)からインストールしておいてください．環境変数PATHが正しく設定されていることを確認してください．確認するためには，コマンドプロンプトを開いて
```
git
```
と入力します．コマンドの説明が出てきたらインストールできています．

## How to use

ここでは，windowsを例としてdocker imageの入手からテンプレートの出力までを[こちら](https://zenn.dev/being/articles/how-to-use-my-latex)の元記事を参考にもう少し詳しく説明します．Ubuntu版は作成中です．

### Pull the docker image

Docker Desktop on Windowsがダウンロードされており，起動＆新規登録済みであることを確認してください．

はじめに，コマンドプロンプトを起動し，以下のコマンドを入力してください．
```
docker pull ghcr.io/being24/latex-docker:latest
```

(ハードウェア側で仮想環境を使えない設定にしている場合，上手くpullできないそうです．その場合は，BIOSから仮想環境の設定をenableにしてください．使っているPCによってBIOSの設定画面は異なるので，ネット等で調べてください)

次に，以下のコマンドを入力してください．
```
docker images
```

レポジトリの欄に`ghcr.io/being24/latex-docker`があれば，成功しています．コマンドプロンプトは起動したままにしておいてください．

### Create new repository

Gitがインストール済みであり，環境変数PATHが正しく通っていることを確認してください．

はじめに，[こちら](https://github.com/tuatikukolab/latex_template)を開きます．

次に，右上にある`Use this templete`から，`Create new repository`を選択します．これにより，論文のテンプレートを丸ごとコピーした自分のリポジトリを作成できます．

設定は下の画像を参考にしてください．

![newrepo](https://github.com/user-attachments/assets/d45612aa-9861-4540-9af5-7a8d935f03eb)

最後に`Create repository`をクリックしてください．今後はこのリポジトリを使ってcloneおよび編集を行います．

### Clone the templete

はじめに，先ほど作成した自分のリポジトリの右上にある`<> Code`をクリックし，表示されているURLをコピーしてください．

![clonerepo](https://github.com/user-attachments/assets/8041c4db-edc1-4ed7-9a3d-623f300ec0f3)

次に，先ほど起動したままにしておいたコマンドプロンプトを使って，LaTeXのテンプレートをダウンロードしたいディレクトリに移動してください．

次に，以下のコマンドを入力してください(<>の部分は適宜書き換えてください．<>は入力する必要ありません)．
```
git clone <ここにGithubからコピーしたURL>
```
途中でログインを求められるので，ログインしてください．
done.が出てきたら，成功しています．
(Ubuntuの場合，httpsではcloneできないそうです．sshを使用してください．)

また，gitを使うことで複数のコンピュータでの論文執筆が可能になります(めちゃくちゃ使いやすいGoogle Driveのイメージです)．[こちら](how_to_use_git.md)にgitのコマンドの使い方をまとめたので参考にしてください．

### Use the template

はじめに，vscodeを開きFlie->Open Folder...から先ほどダウンロードしたフォルダを開いてください．
このとき，拡張機能のインストール画面やバナーが出てきた場合はいったん全てインストールしてください．
また，もしインストール済みでなければ，左側の「Extensions」アイコンから**LaTeX workshop**および**Remote Development**を検索してインストールしてください．
(LaTeX workshopはふたつあるそうです．James Yuさんが作成した方をインストールしてください．)

次に，左側のメニューから「TeX」アイコンをクリックし，COMMANDSから「Build LaTeX project」→「Recipe: compile」の順にクリックしてTeXファイルのコンパイルをしてください．
TeXファイルを表示している場合はウィンドウ右上の緑の矢印をクリックしても同様にコンパイルできます．

最後に，COMMANDSから「View LeTeX PDF」をクリックしてください．pdfファイルが出力されたら，成功しています．

### When start VSCode again

2回目以降に起動する場合は，はじめにDocker desktopを起動してからVSCodeを起動してください．

## Config

`.vscode/settings.json`は，[こちら](https://github.com/being24/latex-template-ja)のテンプレートにあったものを引用しています．
VSCodeはこの設定を自動で読み込むため，設定を変更する必要は無いそうです．

## About the template

先輩から代々受け継がれているテンプレートをもとに，体裁を整えたものを載せています．1章ではLaTeXの使用経験があまりない学生を対象に初歩的な使用法をまとめています．誤りがあった場合や，新たに加えてほしい内容がありましたら教えていただけると幸いです．  
実際の使用時は，1章に載せた使用法は消してください．

また，コンパイルの際にデフォルトで2点のcautionが出ます(caption.styおよびmain.tex)が，気にしないでください．

## Contact

dockerやgithubまわりのエラーは，斎藤雅史君か江﨑郁磨君に聞いてください．

LaTeXまわりのエラーは穂苅彩音(hokaria.tuat@gmail.com)に聞いてください．

## 参考URL

<https://github.com/being24/latex-template-ja>

<https://poyo.hatenablog.jp/entry/2020/12/05/110000>
