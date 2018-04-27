### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a>ObjectDisposedException が WPF スペルチェックでスローされる

|   |   |
|---|---|
|説明|スペルチェックで <xref:System.ObjectDisposedException?displayProperty=name> がスローされ、WPF アプリケーションがシャットダウン時にクラッシュする場合があります。 これは .NET 4.7 WPF で修正されます。例外は正しく処理されるため、アプリケーションが悪影響を受けることはなくなります。 ただし、デバッグ時に実行中のアプリケーションで初回例外が見られる場合があるので注意してください。|
|提案される解決策|.NET 4.7 にアップグレードします。|
|スコープ|エッジ|
|Version|4.6.1|
|型|ランタイム|

