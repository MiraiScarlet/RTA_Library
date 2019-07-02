# ゼルダコレクション版ムジュラの仮面をWiiVC化する

北米版準拠の日本語版ムジュラだが、ゼルコレでやってるとどうにもフリーズするのでWiiVCに無理矢理移植するためにやった備忘録的なもの

行う場合は**自己責任で実行してください。**
ここに書いたことを行い不利益を被った場合、筆者は責任を負いかねます。

## 必要なもの

  - ゼルダコレクションから吸い出したムジュラの仮面の.n64ファイル
  
    - 吸出し方法は[ねこかぶさんのHPの記事を参照](http://nekokabu.s7.xrea.com/gchack/gchack4.html)
    
    - CleanRipで吸い出した場合、isoファイルをtgc扱いにしてぶち込めば解凍はできるはず
    
  - [GC版ゼルダ修正パッチ](https://krikzz.com/forum/index.php?topic=5161.0)
  
    - 今回はムジュラを使うので```Zelda no Densetsu - Mujura no Kamen (Japan) (GameCube Edition).z64```からパッチをダウンロード
    
    - 一部修正が入ってるので、今回の方法では厳密にゼルコレ版ムジュラを移植することはできない(VC移植のためのパッチが内包されている)
    
    - コレを使ってRTAをするのはおすすめしない(誰もやらないだろうけど)
    
  - [Floating IPS](http://www.smwcentral.net/?p=viewthread&t=78938)
  
    - 上記パッチを当てる為に必要
    
  - ムジュラの仮面(VC)のwadファイル
    
    - ムジュラであれば何でもいい(日本版、Randomizerのもので動作確認済)
    
    - [YetAnotherBlueDumpMod](https://wiidatabase.de/downloads/wii-tools/yet-another-bluedump-mod/)でtik/tmdを改変したものを推奨
    
  - u8tools等、appファイルを展開できるソフト

    - 今回は[Wii.cs Tools 0.3](https://code.google.com/archive/p/showmiiwads/downloads)の中にあるUltimateU8を使った
    
    - [Showmiiwads](https://wiibrew.org/wiki/ShowMiiWads)でもできるかもしれない
    
  - wadを展開(unpack)・梱包(pack)できるソフト
  
    - 今回は[ShowMiiwads](https://wiibrew.org/wiki/ShowMiiWads)を使った(GUIがあるから一番楽)
    
  - バイナリエディタ(Insertできるものならなんでもいい)
    
### 手順

  #### 1.wadの中身を展開する

    showmiiwadsでwadを展開し、各種appファイルを直接編集できるようにする
  
  #### 2.00000005.appをUltimateU8で展開(Unpack)する
  
    .appファイルを展開できるツールであればなんでもいい(はず)
    
  #### 3.n64ファイルにFloatingIPSを使ってパッチを当てる
  
  #### 4.パッチを当てたROMファイルに手を加え、romcとして保存する
  
    先頭に「08 00 00 00」を挿入する
    
    要らないかもしれないけど念の為
    
    変更したらファイル名を「romc」にして保存(拡張子は要らない)
    
  #### 5.romcファイルを置き換える
  
    先程展開した00000005.appファイルの中身に「romc」ファイルがあるので置き換える
    
  #### 6.UltimateU8で00000005.appを梱包(pack)する
  
  #### 7.前項で作った00000005.appを入れ替えてwad化する
  
    00000005.appを入れ替えてwad化するだけ
    
    showmiinandsでできる
    
  #### 8.wadファイルを弄る
  
    一応そのままでも入るが、タイトルID等を弄っておくっと重複せず入れられるはず
    
  #### 9.wadマネージャー等でWiiに入れて完了
  
    バグかどうか不明だが、CSやポーズ画面等が暗いままになることが多い
    
    ポーズバッファがだいぶ厳しい
