### <a name="two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a>非パブリック セッターを持つプロパティへの双方向データ バインドはサポートされません

|   |   |
|---|---|
|説明|パブリック セッターを持たないプロパティへのデータ バインドを試みることは、サポートされるシナリオではありません。 .NET framework 4.5.1 以降では、このシナリオでは <xref:System.InvalidOperationException?displayProperty=name> がスローされます。 この新しい例外は、具体的に .NET Framework 4.5.1 を対象とするアプリでのみスローされることに注意してください。 アプリが .NET Framework 4.5 をターゲットとしている場合、この呼び出しは許されます。 アプリが特定のバージョンの .NET Framework をターゲットにしていない場合、バインドは一方向として扱われます。|
|提案される解決策|一方向のバインドを使用するか、プロパティのセッターを公開するように、アプリを更新する必要があります。 または、.NET Framework 4.5 をターゲットにすると、アプリは以前の動作を示すようになります。|
|スコープ|マイナー|
|Version|4.5.1|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType></li></ul>|

