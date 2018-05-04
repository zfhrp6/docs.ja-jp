### <a name="aspnet-accessibility-improvement-in-net-471"></a>.NET 4.7.1 の ASP.NET アクセシビリティ機能の強化

|   |   |
|---|---|
|説明|ASP.NET のお客様のサポートを改善する目的で、ASP.NET Web コントロールによる Visual Studio のアクセシビリティ テクノロジの処理方法が向上しています。  次のような点が変更されます。<ul><li>[詳細の表示] ウィザードの [フィールドの追加] ダイアログなど、コントロールで不足していた UI アクセシビリティ パターンを実装するための変更。</li><li>データ ページャー フィールド エディターなど、ハイ コントラスト モードでの表示を改善するための変更。</li><li>オブジェクト コンテキストの構成ウィンドウまたはデータ ソースの構成ウィンドウなど、制御するためのキーボード ナビゲーション操作を改善するための変更。</li></ul>|
|提案される解決策|**以上の変更を選択する方法と選択しない方法** Visual Studio デザイナーの場合、.NET Framework 4.7.1 以降で実行しなければ、以上の変更から改善を得ることはありません。 Web アプリケーションの場合、次のいずれかの手法をとることで、以上の変更によって機能が強化されます。<ul><li>Visual Studio 2017 15.3 以降をインストールする。このバージョンからは既定で、次の項目にある AppContext スイッチで新しいアクセシビリティ機能に対応しています。</li><li>下の例のように、devenv.exe.config ファイルの `<runtime>` セクションに **Switch.UseLegacyAccessibility** AppContext スイッチを追加し、それを `false` に設定することで、以前のアクセシビリティ動作を無効にします。</li></ul><pre><code>&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;<br />&lt;configuration&gt;<br />&lt;runtime&gt;<br />...</code></pre>|
|スコープ|マイナー|
|Version|4.7.1|
|型|再ターゲット中|
