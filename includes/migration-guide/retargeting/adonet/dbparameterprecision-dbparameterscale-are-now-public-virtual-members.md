### <a name="dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a>DbParameter.Precision と DbParameter.Scale は、パブリック仮想メンバーになった

|   |   |
|---|---|
|説明|<xref:System.Data.Common.DbParameter.Precision> および <xref:System.Data.Common.DbParameter.Scale> はパブリック仮想プロパティとして実装されます。 これらは、対応する明示的なインターフェイス実装、<xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> と <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale> を置き換えます。|
|提案される解決策|ADO.NET データベース プロバイダーを再構築するとき、これらの違いにより、「override」キーワードが Precision および Scale プロパティに適用される必要があります。 これは、コンポーネントを再構築するときにのみ必要です。既存のバイナリは引き続き機能します。|
|スコープ|マイナー|
|Version|4.5.1|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Data.Common.DbParameter.Precision?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbParameter.Scale?displayProperty=nameWithType></li></ul>|

