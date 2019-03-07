# ZCとは
  2019年2月下旬にリリースされた、最新版のPracticeCode
  
  今までのPracticeCodeとは構造が変更され、セーブファイルにチートコードを内包して汎用性を強化したもの
  
  セーブファイルが変わる為、本来のファイルと区別するために専用のrom(wad)ファイルの作成が必要になった
  
  日本だと導入方法が少し複雑の為、以下で解説
  
  **以下の項目は全て自己責任の上で使用してください**
  
# 必要なもの
  - HBCを導入したwii
  - [gecko OS](https://wiibrew.org/wiki/Gecko_OS)
  - [WiiMOD](http://revowii.blog.fc2.com/blog-entry-25.html)等wadインストール用ツール
  - 北米版ムジュラの仮面wadファイル
    - 日本版wadは使用できない **(日本版を作る場合でも北米版が必要)**
    - [Yet Another Bluedump mod](https://wiidatabase.de/downloads/wii-tools/yet-another-bluedump-mod/)等でリージョン解除したものを推奨
  - [zc用パッチファイル・セーブファイル](https://zc.zeldacodes.org/)
    - 使用したい言語verを「console」から選択、Patch「0.1」はCSカット等が含まれている
    - 準備が出来たら「Patch」からupsファイルを、「Save Data」からセーブデータをダウンロードする
  - [tsukuyomi UPS](https://www.romhacking.net/utilities/519/) or [NUPS](https://www.romhacking.net/utilities/606/)
    - 本来ならzcサイト内の「Patcher」からパッチを当てるのだが、吸い出したwadではハッシュが一致しないため使えない
    - そのためupsのパッチを当てるプログラムを別途用意する。本項では後者(NUPS)を使用

# 手順
  - ファイルを用意したらNUPS.exeを起動
    - パッチしたファイルは上書きされるので、wadファイルはバックアップを必ず用意する
  - 「Apply an UPS patch to a file」を選択
  - 「File to patch」でwadファイルを、「UPS patch」でDLした.upsファイルを選択
  - 「If file is invalid」を**「Abort」以外に選択する**
    - upsファイルはチェックサムを用いて誤パッチを防止しているが、今回は回避したいのそのための選択肢
  - 全て選択したら「Patch」ボタンでパッチする
    - Ignore以外だとハッシュ違うぞとポップアップで言われるがyesを選択
  - 完成したwadファイルをSDカードの適当な所に入れる
  - セーブファイル(data.bin)を、SDカード内「private￥wii￥title￥NZCJ」フォルダに入れる
  - SDカードをwiiに差し込み、wadをインストールする
  - セーブデータ管理からSDカード内のセーブデータを本体にコピーする
  - HBC経由でgeckoを起動し、ZC-x(xx)(xは言語ver(ZC-j(JP) or ZC-U(US))からゲームを起動
  
  - 以上の手順でwadがインストールできない場合、wadをUnpackして以下のファイルのバイナリを書き換えてパックする
    - wadのパック方法はここでは解説しない
    - .cert
      - NANDからcert.sysを抜き出して置き換え
    - .tik
      - 0x0-0x13f 全て00
      - 0x180-0x1bb 全て00
      - 0x1bf-0x1ce 9d e2 00 cc e4 bb 6d 04 e1 da e4 de 36 33 17 5c
      - 0x1d0-0x1db 00 01 ac e5 e3 8e 4c 68 00 00 00 00
      - 0x1f1-0x1f2 a8 00
      - 0x221 00
    - .tmd
      - 0x4-0x13f 全て00
      - 0x1d4-0x1d5 9a 01
      - 0x1e2-0x1e3 00 00
     
 
