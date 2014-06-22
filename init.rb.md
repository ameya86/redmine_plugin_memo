# init.rb

プラグインの基本設定及び、権限追加、メニュー追加、モジュール追加、実は削除も出来る･･･。
パッチ類のrequireもここで行うことが多い。

以下が初期状態

~~~
Redmine::Plugin.register :redmine_plugin do
  name 'Redmine plugin'
  author 'Author name'
  description 'This is a plugin for Redmine.'
  version '0.0.1'
  url 'http://example.com/path/to/plugin'
  author_url 'http://example.com/about'
end

~~~

以下は `lib/redmine/plugin.rb` を参考、引用。

## 基本設定

### Redmineのバージョン確認

特定バージョンやそれ以降を対象にしている場合は、
これを設定しておくことで保証できるバージョンを明示できる。

~~~
requires_redmine(arg)

# Redmineのバージョンが0.7.3以上
requires_redmine :version_or_higher => '0.7.3'
requires_redmine '0.7.3'

# Redmineのバージョンが0.7台
requires_redmine '0.7'

# 特定のRedmineバージョン
requires_redmine :version => '0.7.3'              # 0.7.3 only
requires_redmine :version => '0.7'                # 0.7.x
requires_redmine :version => ['0.7.3', '0.8.0']   # 0.7.3 or 0.8.0

# Redmineのバージョンが範囲内
requires_redmine :version => '0.7.3'..'0.9.1'     # >= 0.7.3 and <= 0.9.1
requires_redmine :version => '0.7'..'0.9'         # >= 0.7.x and <= 0.9.x
~~~

## 権限

ロールに設定する権限

~~~
permission(name, actions, options = {})
~~~

## メニューを追加、削除

### 追加

~~~
menu(menu, item, url, options={})

menu :project_menu, :plugin_example, { :controller => 'example', :action => 'say_hello' }, :caption => 'Sample'
~~~

:caption にシンボルを渡すと、言語化される。

### 削除

既存のメニューのリンク先や呼び出すコントローラやパラメータを変えたい場合に使う。
その場合は削除後に追加し直す形になる。

~~~
delete_menu_item(menu, item)

# トップメニューからヘルプリンクを削除する
delete_menu_item :top_menu, :help
# リンク先をRedmine.JPさんにしたヘルプを追加する
menu :top_menu, :help, 'http://redmine.jp/', {:last => true}
~~~

## モジュールを追加

~~~
project_module(name, &block)
~~~

## 活動の分類を追加

~~~
activity_provider(*args)
~~~

## テキストの書式を追加

~~~
wiki_format_provider(name, formatter, helper)
~~~

## 他のプラグインが必要

他のプラグインの存在を前提としているプラグインで利用する。

~~~
requires_redmine_plugin(plugin_name, arg)

# foo というプラグインのバージョン0.7.3以上が必要
requires_redmine_plugin :foo, :version_or_higher => '0.7.3'
requires_redmine_plugin :foo, '0.7.3'

# foo というプラグインの特定バージョンが必要
requires_redmine_plugin :foo, :version => '0.7.3'              # 0.7.3 only
requires_redmine_plugin :foo, :version => ['0.7.3', '0.8.0']   # 0.7.3 or 0.8.0
~~~
