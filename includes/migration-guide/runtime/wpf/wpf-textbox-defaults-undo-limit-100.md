### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a>WPF TextBox は既定で元に戻す上限が 100 に設定される

|   |   |
|---|---|
|説明|.NET 4.5 では、WPF テキスト ボックスの既定の元に戻す上限は 100 です (.NET 4.0 では無制限でした)。|
|提案される解決策|元に戻す上限が 100 では低すぎる場合、<xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit> を使用して上限を明示的に設定できます。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|

