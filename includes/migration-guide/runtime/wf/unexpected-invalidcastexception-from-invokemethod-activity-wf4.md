### <a name="unexpected-invalidcastexception-from-invokemethod-activity-in-wf4"></a>WF4 での予期しない InvalidCastException from InvokeMethod アクティビティ

|   |   |
|---|---|
|説明|NULL 値を許容するパラメーターを含むメソッドを対象とする <xref:System.Activities.Statements.InvokeMethod> を使用すると、<xref:System.InvalidCastException?displayProperty=name> がスローされる場合があります。|
|提案される解決策|この動作は、.NET Framework 4.5 のサービス リリースで元に戻されました。 この問題を修正するには、.NET Framework 4.5 に更新してください (または .NET Framework 4.5.1 以降にアップグレードしてください)。|
|スコープ|マイナー|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Activities.Statements.InvokeMethod.Parameters?displayProperty=nameWithType></li></ul>|
|アナライザー|<ul><li>CD0088</li></ul>|

