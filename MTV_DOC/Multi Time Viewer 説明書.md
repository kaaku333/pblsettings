# Multi Time Viewer 説明書

目次

[TOC]

## Multi Time Viewer とは

Multi Time Viewer は任意のイベントまでの時間を表示する Pebble アプリです。  
Pebble Time, Pebble Time Round, Pebble 2 で使えます。

以下のようないろいろな時間を一覧表示するのに使えます。

- 毎日同じ時間に繰り返すルーティンの時間  
  家を出る時間、昼食の時間など
- 特定の日からの日数、特定の日までの日数  
  誕生日からの日数、将来のイベントまでの日数など
- Googleカレンダーの次のイベントまでの時間  
  プライベートな予定までの時間など
- Outlookの次の予定までの時間  
  仕事の予定までの時間など
- 次の電車までの時間  
  よく使う駅の時刻表の時間など
- 世界時計  
  任意の国の時刻など

現在時刻もいつも表示しているので 時計としても使えます。


## 基本的な使い方

1. Pebble に Multi Time Viewer アプリをインストールする
2. Pebble App から Multi Time Viewer の設定画面を開いて、**予定時刻ファイル**がある URL を入力する
3. 設定画面の SAVE ボタンを押し、イベント時刻設定ファイルを Multi Time Viewer にダウンロードする
4. Pebble でUp/Downボタンを押して、イベントを切り替え表示する


## 利用可能な予定時刻ファイル

以下の予定時刻ファイルをネットから読み込むことができます。
認証が必要がなく URL で直接ダウンロードできる場所に置いておく必要があります。

- Time List フォーマット(拡張子.txt)  
  Multi TIme Viewer 専用フォーマットのイベント定義テキストファイル。  
  １行１イベントでテキストエディタで簡易に作成することができます。
  + [定期的な予定(毎日)](MTVdailySample.txt)
  + [定期的な予定(毎週、毎月)](MTVmonthSample.txt)
  + [特定の日](MTVyearSample.txt)
  + [現時刻からの任意の時間オフセットした時間(現地時間およびUTC時間)](MTVworldSample.txt)
  + [他のフォーマットのファイルの読み込み](MTVdailySample2.txt)


- iCalendar フォーマット(拡張子.ics)  
  一般的な予定表アプリで使われる共通フォーマットデータ。  
  例えば下記のようなデータを利用できます。
  + Google カレンダーの非公開リンク URL
  + Outlook で保存した iCalendar ファイルを dropbox上に置いた公開リンク URL

- Next Train フォーマット(拡張子.tbl)  
  次の電車までの時間を表示するためのアプリでよく使われる時刻表データ。  
  本家のアプリ開発は終了してますが、データフォーマットとしては継続して使われてます。 
  + 本家 [NextTrain on the Web](http://office.toyolab.com/nexttrain/)
  + 時刻表変換サイト [えきから時刻表→NextTrainデータ](http://toshi-u.sakura.ne.jp/tt2tbl/ej2tbl.html)


## 付加機能

- アラーム機能   
  個々のアイテムには時間が来たら振動するアラームをTime Listデータもしくはメニューで個別に設定できます。  
  アラーム時間が来たら自動的に 本アプリを起動させることも出来ます。  
  現在時刻からちょっと先にアラームを追加したり、任意のイベント前後にアラームを追加したり出来ます。  
  全アイテムのアラームを一括On/Offしたり、デフォルトの設定に戻したり出来ます。  
  iCalendar の予定をロードするときに一括してアラームOnにする事も出来ます。

- スマホ切断振動機能
  Watchface によくある、スマホ Pebble App との接続が切れたときに振動する機能です。


## 通常画面の表示内容と操作方法

  + 先頭行表示  
    現在時刻、月日、スマホ接続状態
  + リスト表示  
    タイトル一覧、アイテム一覧の順に連続して並んでいます
    * タイトル一覧  
      ロードした予定時刻ファイルのタイトルの一覧。最大５タイトルまで保持できます
    * アイテム一覧  
      ロードした予定時刻ファイルのアイテムの一覧。最大４０アイテムまで保持できます
  + 操作  
    - Enter  
      タイトルで押したときはタイトルメニュー表示。アイテムで押したときは一般メニュー表示
    - Enter 長押し  
      一般メニューの長押し設定で設定したメニュー項目を直接実行する
    - Up  
       リストを上にスクロールする
    - Down  
       リストを下にスクロールする
    - Back  
       本アプリを終了する


## タイトルメニュー  

通常画面のいずれかのタイトルで ENTER ボタンを押すと表示されるメニュー。  

- LOAD  
  該当予定時刻ファイルを再度ロードします。

- DELETE  
  Pebble上から該当予定時刻ファイルを削除します。  
  元の予定時刻ファイルは消えません。

- NextTrain Holiday  
  Next Train フォーマットをロードするときに祝祭日指定するかどうかを設定する。
  + Holiday ... 今日を祝祭日として読み込む
  + Off ... 今日を通常日（祝祭日ではない）として読み込む

- iCalendar Alarm  
  iCalendar フォーマットをロードするときにアラームデータとするか設定する。
  + Alarm On ... アラームデータとして読み込む
  + Alarm Off ... 通常データ（アラームデータではない）として読み込む

## 一般メニュー  

通常画面のいずれかのアイテムで ENTER ボタンを押すと表示されるメニュー。  
並び順はスマホ上の設定画面で並び替えができます。

- Item Information  
  アイテム情報を表示する
- Goto Next Item  
  現在時刻に一番近い時間のアイテムに移動する  
  ソート順を時間にしておくこと
- Goto Top Item  
  先頭のアイテムに移動する
  タイトルに移動したい時にも使う
- Push Timeline  
  該当アイテムをPebbleのタイムラインに登録する
  うまく動かないこともあります
- Toggle Alarm  
  該当アイテムのアラームのOn/Offを切り替える
- Alarm Mode  
  アラームを一括On/Off/プリセット値に戻すを実行する
- Days Format  
  経過日時の表示形式を切り替える
- Periodic Time  
  定期的なイベントの時刻を超えた後に直ぐ未来の予定として扱うか半周期まで過去のイベントとして扱うか切り替える
- Sort Items  
  アイテムの並び替え順を時間順、名前順、並び替え無しから選ぶ。通常は時間順にしておく
- Display Second  
  秒表示On/Off を切り替える
- --- More Menu ---  
  ここから下は拡張メニュー
- Add Alarm item  
  該当アイテム前後にアラームアイテムを追加する
- Add Now Alarm  
  現在時刻の近くにアラームアイテムを追加する
- Delete Item  
  アイテムを削除する。通常は動的に追加したアラームアイテムの削除に使う
- Wakeup by Alarm  
  アラームによって Multi Time Viewer を起動するかどうか設定する
- Highlight Font  
  ハイライト表示しているフォントの大きさを調整する
- Color Theme  
  カラーテーマを切り替える
- Assign Long Push  
  Enter 長押し時の動作をメニュー項目の中から選ぶ
- Date Format  
  年月日の並び順を設定する
- Time Type  
  12時間24時間表示を切り替える
- DisConnect Vibe  
  スマホApp切断時に振動するかどうか切り替える
- Reload items  
  現在のタイトルのアイテムを読み込み直す
- Three Lines Display  
  ２行表示(タイトルと経過時間のみ表示)、３行表示(アイテムのオリジナル時間表示付き)を切り替える

## 設定画面 

スマホの Pebble App の Apps の Multi Time Viewer を選んで表示する設定画面。


### LOAD TIMELIST
 + TimeList URL  
   ロードしたい予定時刻ファイルが置いてある URL を入力する。
   その後 SAVE を押すと Pebble に該当予定時刻ファイルがダウンロードされる。
 + History  
   過去にロードした予定時刻ファイルの履歴。再度ロードしたいときに選ぶ。５個以上覚えておける。
 + What is TimeList  
   予定時刻ファイルの簡単な説明。
 + TimeList Sample  
   TimeList のサンプル。Put URL で TimeList URL に URL 入力。 Show File でサンプルテキストを表示。
 + How to add TimeList  
   TimeList の登録方法の手順例。

### DELETE TIMELIST
 + Delete Selected History  
   History でタイトルを選んでチェックしてから SAVE を押すと、該当のタイトルが履歴から削除される。
 + Delete All History  
   チェックしてから SAVE を押すと、History の履歴を全削除する。
 + Delete Loal added items in Pebble  
   Pebble で直接追加したアラームアイテムを全て削除する。
 + Delete All in Pebble  
   Pebble 上のタイトルとアイテムを全て削除する。

### SORT MENU ITEMS
 + Menu Items  
   一般メニューの項目の並びをドラッグアンドドロップで変更して SAVE を押すと、Pebbleの一般メニューの並びに反映される。
 + Reset Item Sorting  
   Reset を押すと、一般メニューの項目の並び順を初期状態に戻す。

## メッセージ

表示されるメッセージの意味です。

- Data Loaded  
  データが正常にロードできました
- Data Loaded but overflowed  
  データはロードできましたが、アイテム数が多すぎて後ろの方のアイテムはカットしました
- All Title Deleted  
  全タイトルを削除しました
- Local Alarm item Deleted  
  Pebbleで直接追加したアラームアイテムを削除しました
- Server Timeout
- File not found
- Server error  
  サーバーからデータロードできませんでした。リトライしてみてください

## 注意事項

- 一度にメモリ上に保持できるアイテム数は最大40個です。  
  多すぎてアラームアイテムを追加できない場合は、不要なアイテムを Delete Item で削除してください。
- iCalender データでロードできるアイテムは、半日前から２週間後までです。
- Next Train データでロードできるアイテムは、今から１時間後までです。


以上
