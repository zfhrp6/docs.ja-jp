### <a name="entity-framework-version-must-match-the-net-framework-version"></a>Entity Framework バージョンは .NET Framework バージョンに一致する必要がある

|   |   |
|---|---|
|説明|Entity Framework のバージョンは .NET Framework のバージョンに一致する必要があります。 .NET 4.5 には、Entity Framework 5 をお勧めします。 .NET 4.5 プロジェクトの EF 4.x に <xref:System.ComponentModel.DataAnnotations> に関する既知の問題がいくつかあります。 .NET 4.5 では、別のアセンブリに移動したので、どの注釈を使用するのか判断するという問題があります。|
|提案される解決策|.NET Framework 4.5 の場合、Entity Framework 5 にアップグレードする|
|スコープ|Major|
|バージョン|4.5|
|型|再ターゲット中|

