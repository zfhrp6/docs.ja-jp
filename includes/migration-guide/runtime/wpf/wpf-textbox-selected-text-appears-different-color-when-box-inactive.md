### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a>WPF TextBox で選択されているテキストが、テキスト ボックスがアクティブでないときに異なる色で表示される

|   |   |
|---|---|
|説明|.NET 4.5 では、WPF テキスト ボックス コントロールがアクティブでないとき (フォーカスがないとき)、ボックス内で選択されているテキストは、コントロールがアクティブなときとは別の色で表示されます。|
|提案される解決策|<xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> プロパティを <code>false</code> に設定することで、以前 (.NET 4.0) の動作が復元される可能性があります。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|

