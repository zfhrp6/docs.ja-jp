### <a name="wpf-layout-rounding-of-margins-has-changed"></a>WPF レイアウトでの余白の丸め方の変更

|   |   |
|---|---|
|説明|余白、境界線、およびそれらの内部の背景の丸め処理の方法が変更されました。 この変更の結果、以下のようになります。<ul><li>要素の幅または高さが最大で 1 ピクセル拡大または縮小することがあります。</li><li>オブジェクトの配置が最大で 1 ピクセル移動することがあります。</li><li>中央揃えの要素が中央から最大で 1 ピクセル垂直まは水平方向にずれることがあります。</li></ul>既定では、この新しいレイアウトは .NET Framework の 4.6 を対象とするアプリに対してのみ有効となります。|
|提案される解決策|この変更はの右端または下端高 Dpi での WPF コントロールのクリッピングを除去する傾向があります、ため、.NET Framework の以前のバージョンを対象と、.NET Framework 4.6 上で実行されているアプリこともできますこの新しい動作を次の行を追加することで、<code>&lt;runtime&gt;</code> 、app.config ファイルのセクション: <code>&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false&quot; /&gt;</code>WPF コントロールへの以前のレイアウトのアルゴリズムを使用してレンダリングの目的は、.NET Framework 4.6 を対象するアプリこれを行うには、次の行を追加することによって、 <code>&lt;runtime&gt;</code> app.config ファイルのセクション<code>&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true&quot; /&gt;</code>。|
|スコープ|マイナー|
|Version|4.6|
|型|再ターゲット中|

