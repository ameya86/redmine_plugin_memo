# メニュー項目

init.rb の Redmine::Plugin.register メソッド内で menu メソッドを呼び出して追加する。

メニューの種別

|種別             |説明|
|-----------------|----|
|:top_menu        |左上のメニュー。ホームなどがある箇所。全体に影響がある項目向け。|
|:account_menu    |右上のメニュー。ログイン、ログアウトなどがある箇所。ユーザに関した項目向け。|
|:project_menu    |プロジェクトで表示されるメニュー。概要やチケットなど。プロジェクトごとに分けられる項目向け。|
|:application_menu|プロジェクトが選択されていない時に表示されるメニュー。デフォルトでは空なので、用例は不明。|

## 追加

種別、メニュー名、リンク先、オプション（見出し、位置）を引数に指定する。

`lib/redmine.rb` で呼び出している `Redmine::MenuManager.map` が
Redmine標準のメニュー定義なので、そこが参考になる。

~~~
menu(menu, item, url, options={})

menu :project_menu, :plugin_example, { :controller => 'example', :action => 'say_hello' }, :caption => 'Sample'
~~~

|オプション|説明                                |例|
|----------|------------------------------------|---|
|:caption  |見出し。シンボルの場合は翻訳される。|:label_issue|
|:first    |メニューの一番左に追加する。        |:first => true|
|:last     |メニューの一番右に追加する。        |:last => true|
|:before   |指定項目の左に追加する。            |:before => :issues|
|:after    |指定項目の右に追加する。            |:after => :new_issue|

:last や :before が他のプラグインなどと競合した場合の挙動は不明。
（呼び出し順で処理される？）

## 削除

削除も可能。独自機能に差し替えたり、使わせたくない機能を隠すのに向いているか？

~~~
delete_menu_item(menu, item)

# トップメニューからヘルプリンクを削除する
delete_menu_item :top_menu, :help
# リンク先をRedmine.JPさんにしたヘルプを追加する
menu :top_menu, :help, 'http://redmine.jp/', {:last => true}
~~~
