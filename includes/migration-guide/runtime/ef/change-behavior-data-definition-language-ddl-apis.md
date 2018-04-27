### <a name="change-in-behavior-in-data-definition-language-ddl-apis"></a>データ定義言語 (DDL: Data Definition Language) API の動作の変更

|   |   |
|---|---|
|説明|AttachDBFilename が指定されたときの DDL API の動作が、次のように変更されました。<ul><li>接続文字列で初期カタログ値を指定する必要がなくなりました。 以前は、AttachDBFilename と初期カタログの両方が必要でした。</li><li>AttachDBFilename と初期カタログの両方が指定され、指定された MDF ファイルが存在した場合、ObjectContext.DatabaseExists メソッドは true を返します。 以前は、false を返していました。</li><li>AttachDBFilename と初期カタログの両方が指定され、指定された MDF ファイルが存在した場合、ObjectContext.DeleteDatabase メソッドを呼び出すと、ファイルは削除されます。</li><li>接続文字列が存在しない MDF と存在しない初期カタログで AttachDBFilename の値を指定したときに ObjectContext.DeleteDatabase が呼び出された場合、メソッドは InvalidOperationException 例外をスローします。 以前は、SqlException 例外をスローしていました。</li></ul>|
|提案される解決策|これらの変更により、DDL API を使用するアプリケーションおよびツールの構築が簡単になりました。 これらの変更は、次のシナリオでアプリケーションの互換性に影響を及ぼす可能性があります。<ul><li>ユーザーは、ObjectContext.DatabaseExists が true を返した場合に ObjectContext.DeleteDatabase を呼び出す代わりに、DROP DATABASE コマンドを直接実行するコードを作成します。 データベースがアタッチされておらず、MDF ファイルが存在する場合、これによって既存のコードが破損します。</li><li>ユーザーは、初期カタログと MDF ファイルが存在しないとき、ObjectContext.DeleteDatabase メソッドが InvalidOperationException 例外ではなく、SqlException 例外をスローすることを前提としたコードを作成します。</li></ul>|
|スコープ|マイナー|
|Version|4.5|
|型|ランタイム|

