### <a name="missing-target-framework-moniker-results-in-40-behavior"></a>ターゲット フレームワーク モニカーがないと、4.0 の動作になる

|   |   |
|---|---|
|説明|アセンブリ レベルで <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> が適用されていないアプリケーションは、自動的に .NET Framework 4.0 のセマンティクス (quirks) を使用して実行します。 高い品質を確保するには、すべてのバイナリを、ビルドされた .NET Framework のバージョンを示す <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> で明示的に属性指定することをお勧めします。 プロジェクト ファイルでターゲット フレームワーク モニカーを使用すると、MSBuid は <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> を自動的に適用します。|
|提案される解決策|<xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> は、属性をアセンブリに直接追加するか、[プロジェクト ファイルで、または Visual Studio のプロジェクト プロパティ GUI](http://blogs.msdn.com/b/visualstudio/archive/2010/05/19/visual-studio- managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework.aspx) でターゲット フレームワークを指定することによって指定する必要があります。|
|スコープ|Major|
|バージョン|4.5|
|型|ランタイム|

