### <a name="previewlostkeyboardfocus-is-called-repeatedly-if-its-handler-shows-a-windows-forms-message-box"></a>PreviewLostKeyboardFocus は、そのハンドラーが Windows フォーム メッセージ ボックスを表示する場合、繰り返し呼び出される

|   |   |
|---|---|
|説明|.NET Framework 4.5 以降では、<xref:System.Windows.UIElement.PreviewLostKeyboardFocus> ハンドラーから <code>System.Windows.Forms.MessageBox.Show</code> を呼び出すと、メッセージ ボックスが閉じられたとき、ハンドラーが再実行して、メッセージ ボックスの無限ループになる可能性があります。|
|提案される解決策|この問題を回避するには、2 つの方法があります。<ol><li><code>System.Windows.Forms.MessageBox.Show</code> の代わりに <code>System.Windows.MessageBox.Show</code> を呼び出すことによって回避できます。</li><li><xref:System.Windows.UIElement.LostKeyboardFocus> イベント ハンドラーから (<xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=name> イベント ハンドラーではなく) メッセージ ボックスを表示することによって回避できます。</li></ol>|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Windows.ContentElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.IInputElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement.PreviewLostKeyboardFocus?displayProperty=nameWithType></li><li><xref:System.Windows.UIElement3D.PreviewLostKeyboardFocus?displayProperty=nameWithType></li></ul>|

