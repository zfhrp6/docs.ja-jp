### <a name="sqlvariant-data-uses-sqlvariant-collation-rather-than-database-collation"></a>sql_variant データはデータベースの照合順序ではなく、sql_variant の照合順序を使用する

|   |   |
|---|---|
|説明|<code>sql_variant</code> データはデータベースの照合順序ではなく <code>sql_variant</code> の照合順序を使用します。|
|提案される解決策|この変更により、データベースの照合順序が <code>sql_variant</code> の照合順序と異なる場合にデータ破損が生じる可能性に対応できます。 破損したデータに依存するアプリケーションでは、エラーが発生する場合があります。|
|スコープ|透明|
|Version|4.5|
|型|ランタイム|

