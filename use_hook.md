# 用意されたHookを使う

Redmine側に用意されている処理を追加する箇所があり、Hookと呼ばれている。

メソッドに変更を加える場合に対して、リスクが少ないのが利点。

## Hookの場所

Hookの場所を表示するコマンドが1.x時代はあったが、2.x以降はないため

~~~
grep call_hook -R *
~~~

などのコマンドで呼び出し箇所（call_hookメソッド）を検索して、逆引きする必要がある。

Windows環境の場合は、サクラエディタや秀丸の正規表現検索を利用するとよい。


公式にあるHook一覧： http://www.redmine.org/projects/redmine/wiki/Hooks_List

## Hookの書き方（メソッド）

~~~
class PluginHook < Redmine::Hook::ViewListener
  def controller_issues_new_before_save(context = {})
    issue = context[:issue]
    issue.assigned_to = User.current
  end
end
~~~

のように、 `Redmine::Hook::ViewListener` を継承したクラスで
使いたいHookの名前でメソッドを作成する。

Hookメソッドの引数は、連想配列で渡されるので `context = {}` が標準になる模様。

引数contextの中には、call_hookから渡された各値が入っているので、
call_hookでのキー割り当てを参照して、欲しい値を取り出す。

基本的にはそのHookを呼び出した状況に沿った値が入っている。
（チケット更新処理の途中だったら :issue にチケットが入るなど）

Hook用に定義したクラスは init.rb で require すること。
ファイルはlib配下に置く。

## Hookの書き方（View）

~~~
class PluginHook < Redmine::Hook::ViewListener
  render_on :view_layouts_base_body_bottom, :partial => 'foo/bar'
end
~~~

`Redmine::Hook::ViewListener` を継承したクラスで `render_on Hook名` を定義する。

:partial や :file 、 :template などの形式で呼び出すViewファイルを指定する。

内部ではrenderメソッドを呼び出しているため、 renderメソッドで使える引数は一通り使えるはず。

呼び出されたViewファイルでは、呼び出し元で利用できていたインスタンス変数（@付きの変数）が
継続して利用できるので、
やろうと思えば @issues や @trackers などの一覧系情報を参照して添削することも可能。
