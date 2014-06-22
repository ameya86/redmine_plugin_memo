2.5.x想定

# モジュールを増やす

プラグインディレクトリの `init.rb` の
`Redmine::Plugin.register` メソッド内に以下を追加する

~~~
project_module :module_name do
  permission :permission_a, :controller_name => [:action_a, :action_b], {:option => :type}
  permission :view_foo, :foos => [:index, :show], :require => :member
end
~~~

以下、対応表

|項目            |説明|
|----------------|---|
|:module_name    |モジュール名。<br>Redmine標準のモジュールや他のプラグインと被らない名前がよい。<br>安直に書くならプラグイン名もしくは提供する機能名を英語かローマ字で。|
|permission      |モジュールに対応した権限の定義。<br>最低ひとつは必須？|
|:permission_a   |権限名。|
|:controller_name|呼び出すコントローラの名前。 IssuesController なら :issues のように書く。|
|option          |任意項目。[[ロールの権限を増やす]] を参考|

`config/locales/**.yml` に `project_module_xxxx:` （xxxxはモジュール名）を入れておくと
モジュール名が翻訳して表示される。

## 関連機能

[[init.rb]]
[[ロールの権限を増やす]]