### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a>WPF TextBox.Text とデータ バインドを非同期にできる

|   |   |
|---|---|
|説明|場合によっては、データ バインディングの書き込み操作中にプロパティが変更された場合、<xref:System.Windows.Controls.TextBox.Text> プロパティにデータ バインディング プロパティ値の以前の値が反映されることがあります。|
|提案される解決策|これによって生じる悪影響はないはずです。 ただし、<xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> プロパティを <code>false</code> に設定して、以前の動作を復元することは可能です。|
|スコープ|エッジ|
|Version|4.5|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType></li></ul>|

