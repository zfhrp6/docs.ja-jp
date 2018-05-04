### <a name="typeisassignablefrom-returns-wrong-result-for-generic-variables-with-constraints"></a>Type.IsAssignableFrom は、制約を持つジェネリック変数について正しくない結果を返す

|   |   |
|---|---|
|説明|.NET Framework 4.5 では、<xref:System.Type.IsAssignableFrom(System.Type)> は、制約を持ついくつかのジェネリック型について、常に誤って <code>false</code> を返します。|
|提案される解決策|この問題は、サービス更新プログラムで修正されました。 この問題を修正するには、.NET Framework 4.5 を .NET Framework 4.5.1 以降に更新してください。 または、ジェネリック パラメーターに制約があるジェネリック型で IsAssignableFrom を使用しないでください。 リフレクション API を回避策として使用できます。|
|スコープ|マイナー|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Type.IsAssignableFrom(System.Type)?displayProperty=nameWithType></li></ul>|
|アナライザー|<ul><li>CD0089</li></ul>|

