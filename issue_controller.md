# チケット操作

## 分かり辛い点

### 親チケットの設定

親チケット番号を参照するには、 `@issue.parent_id` を見ればいいが、
代入する場合は、

~~~
@issue.parent_id = 1
~~~

のように書いても親チケットを変更できず、

~~~
@issue.parent_issue_id = 1
~~~

を使う必要がある。

~~~
@issue.safe_attributes = params[:issue]
~~~

のような形で代入する場合も同様。

### カスタムフィールド

#### 関連クラス

CustomField: カスタムフィールド（項目欄）

CustomValue: カスタムフィールドに入っている値

CustomFieldValue: カスタムフィールドと値を参照するためのクラス

#### メソッド（チケットから参照できるもの）

custom_fields: そんなメソッドは無い

custom_values: CustomValueとのhas_many関連。

available_custom_fields: チケットの全てのカスタムフィールド（プロジェクトで無効なものも含む）

custom_field_values: 未設定のカスタムフィールドに初期値を割り当て

visible_custom_field_values: custom_field_valuesの内、閲覧可能なもののみに絞り込む（ロールや表示設定）