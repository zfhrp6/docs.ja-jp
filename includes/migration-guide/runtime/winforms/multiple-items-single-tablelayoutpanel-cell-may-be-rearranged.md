### <a name="multiple-items-in-a-single-tablelayoutpanel-cell-may-be-rearranged"></a>単一の TableLayoutPanel セル内の複数の項目が並べ替えられることがある

|   |   |
|---|---|
|説明|.NET Framework 4.5 では、同じ <xref:System.Windows.Forms.TableLayoutPanel?displayProperty=name> セルに複数の項目がある場合、項目が .NET Framework 4.0 とは別の順序で表示されることがあります。|
|提案される解決策|この動作は、.NET Framework 4.5 のサービス更新プログラムで元に戻されました。 この問題を修正するには、.NET Framework 4.5 を .NET Framework 4.5.1 以降に更新してください。 または、同じ <xref:System.Windows.Forms.TableLayoutPanel?displayProperty=name> セルに複数の項目を置くというあいまいなケースを避けてください。|
|スコープ|マイナー|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Windows.Forms.TableLayoutControlCollection.Add(System.Windows.Forms.Control%2CSystem.Int32%2CSystem.Int32)?displayProperty=nameWithType></li></ul>|
|アナライザー|<ul><li>CD0098</li></ul>|

