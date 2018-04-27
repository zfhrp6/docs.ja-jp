### <a name="concurrentqueuelttgttrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a>ConcurrentQueue&lt;T&gt;.TryPeek は、出力パラメーターを介して誤った null を返すことがあります

|   |   |
|---|---|
|説明|一部のマルチ スレッド シナリオでは、<xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=name> は true を返すことができますが、出力パラメーターに (正しいピーク値の代わりに) null 値を入れることがあります。|
|提案される解決策|この問題は、.NET Framework 4.5.1 で修正されます。 この Framework にアップグレードすると、問題が解決されます。|
|スコープ|Major|
|バージョン|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|

