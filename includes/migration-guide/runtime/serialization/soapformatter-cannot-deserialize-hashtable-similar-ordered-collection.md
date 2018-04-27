### <a name="soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a>SoapFormatter は、ハッシュテーブルなどの順序付けられたコレクション オブジェクトを逆シリアル化できない

|   |   |
|---|---|
|説明|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=name> は、特定のバージョンの .NET Framework でシリアル化されたオブジェクトが別のバージョンで正常に逆シリアル化されることを保証しません。 具体的には、(<xref:System.Collections.Hashtable?displayProperty=name> のような) 順序付けられたコレクションの中には、4.0 と 4.5 の間でメンバーが追加されたものがあり、このような種類のオブジェクトが .NET 4.5 でシリアル化された場合、.NET 4.0 では逆シリアル化できません。 シリアル化データのシリアル化と逆シリアル化の両方が同じバージョンの .NET Framework で行われた場合、問題は発生しないことに注意してください。|
|提案される解決策|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=name> のシリアル化は、.NET Framework の変更に対応できる <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> のシリアル化または <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> に置き換える必要があります。|
|スコープ|マイナー|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object,System.Runtime.Remoting.Messaging.Header[])?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType></li></ul>|

