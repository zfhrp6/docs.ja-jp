### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a>WinForm の CheckForOverflowUnderflow プロパティが System.Drawing に対して true に設定されるようになった

|   |   |
|---|---|
|説明|System.Drawing.dll アセンブリの CheckForOverflowUnderflow プロパティが true に設定されます。|
|提案される解決策|これまではオーバーフローが発生すると、その結果は自動的に切り捨てられました。 現在では、<xref:System.OverflowException?displayProperty=name> 例外がスローされます。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|

