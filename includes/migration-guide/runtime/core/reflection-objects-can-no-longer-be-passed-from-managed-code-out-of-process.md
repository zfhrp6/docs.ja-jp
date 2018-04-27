### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>リフレクション オブジェクトが、マネージド コードからアウト プロセス DCOM クライアントに渡されなくなった

|   |   |
|---|---|
|説明|リフレクション オブジェクトはマネージ コードからアウト プロセス DCOM クライアントに渡されなくなりました。 影響を受ける型は次のとおりです。<ul><li><xref:System.Reflection.Assembly?displayProperty=name></li><li><xref:System.Reflection.MemberInfo?displayProperty=name> (およびその派生型、<xref:System.Reflection.FieldInfo?displayProperty=name>、<xref:System.Reflection.MethodInfo?displayProperty=name>、<xref:System.Type?displayProperty=name>、<xref:System.Reflection.TypeInfo?displayProperty=name> など)</li><li><xref:System.Reflection.MethodBody?displayProperty=name></li><li><xref:System.Reflection.Module?displayProperty=name></li><li><xref:System.Reflection.ParameterInfo?displayProperty=name>。</li></ul>オブジェクトの <code>IMarshal</code> の呼び出しは <code>E_NOINTERFACE</code> を返します。|
|提案される解決策|非リフレクション オブジェクトで動作するように、マーシャリング コードを更新します。|
|スコープ|マイナー|
|Version|4.6|
|型|ランタイム|

