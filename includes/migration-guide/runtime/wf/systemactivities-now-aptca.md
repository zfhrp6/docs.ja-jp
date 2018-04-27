### <a name="systemactivities-is-now-aptca"></a>System.Activities が APTCA に

|   |   |
|---|---|
|説明|アセンブリは <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=name> 属性でマークされています。|
|提案される解決策|派生クラスに <xref:System.Security.SecurityCriticalAttribute?displayProperty=name>のマークを付けることはできません。 以前は、派生型に <xref:System.Security.SecurityCriticalAttribute?displayProperty=name>マークを付ける必要がありました。 ただし、この変更によって生じる実質的な影響はないはずです。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|

