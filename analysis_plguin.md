# プラグインの解析

ダウンロードしたプラグインの解析とか。

基本的に、個人、有志による作成のため、
バグや考慮漏れによる脆弱性が含まれていることがある。

## init.rb

設定ファイル。

メニューやモジュールの追加は基本的に init.rb 内で行うので、
このファイルを見れば大まかな全容が把握できる、はず。

## db/migrate

テーブルを追加、削除、操作するプラグインの場合
db/migrate ディレクトリにファイルが存在するので、
大まかに何をしているか見ておくとよい。

Redmine Backlogs などはかなり複雑な定義になっているので読むのは厳しい。
~~昔、Backlogsのmigrateがバグっていて
チケットの履歴を消し飛ばされたことがあるのでできれば要確認･･･~~

## config/locales

言語ファイル。

ここに各言語に対応した翻訳データが入っている。
日本語は `ja.yml` 。

無い場合は、 `en.yml` あたりを `ja.yml` としてコピーし、
大まかに翻訳すれば一応は日本語で表示できるようになるはず。

## test

テストディレクトリ。
テストが作成されているなら中身がある。

無い場合は動作保証度が薄いということになる。

プラグインのテストは rake redmine:plugins:test で実行できる。
（要RAILS_ENV=testでのmigrate）

rspecなどでテストを作っている場合もある？

## app/controllers/\*.rb、app/models/\*.rb

データの保存、加工時にエスケープ漏れなどが無いか見ておいたほうが良い。
SQLインジェクションなど。

保存時にモデルの attributes に params をそのまま代入している場合は
mass assignment脆弱性の疑いもあるか。

### 参考

github の mass assignment 脆弱性が突かれた件
http://blog.sorah.jp/2012/03/05/mass-assignment-vulnerability-in-github

## app/views/\*/\*

表示する際にクロスサイトスクリプティングの脆弱性をしていないかを見ておくと良い。
