### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>MEF カタログは IEnumerable を実装するため、シリアライザーの作成には使用できなくなった

|   |   |
|---|---|
|説明|.NET Framework 4.5 以降では、MEF カタログは IEnumerable を実装するため、シリアライザー (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> オブジェクト) の作成には使用できなくなりました。 MEF カタログをシリアル化しようとすると、例外がスローされます。|
|提案される解決策|シリアライザーの作成に MEF を使用できなくなりました。|
|スコープ|Major|
|バージョン|4.5|
|型|ランタイム|

