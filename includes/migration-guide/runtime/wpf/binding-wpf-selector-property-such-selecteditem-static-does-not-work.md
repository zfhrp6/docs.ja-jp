### <a name="binding-a-wpf-selector-property-such-as-selecteditem-to-a-static-property-does-not-work"></a>WPF セレクター プロパティ ('SelectedItem' など) を静的プロパティにバインドしても機能しない

|   |   |
|---|---|
|説明|.NET Framework 4.5 では、静的プロパティにデータ バインドされた WPF セレクター プロパティ (<xref:System.Windows.Controls.ListBox?displayProperty=name> または <xref:System.Windows.Controls.DataGrid?displayProperty=name> の &#39;SelectedItem&#39; など) は、バインドされたプロパティが更新されたときに、正しく更新されません。|
|提案される解決策|この動作は、.NET Framework 4.5 のサービス更新プログラムで元に戻されました。 この問題を修正するには、.NET Framework 4.5 を .NET Framework 4.5.1 以降に更新してください。|
|スコープ|マイナー|
|Version|4.5|
|型|ランタイム|

