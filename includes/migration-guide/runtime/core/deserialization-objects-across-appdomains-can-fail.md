### <a name="deserialization-of-objects-across-appdomains-can-fail"></a>アプリ ドメイン全体でのオブジェクトの逆シリアル化に失敗する可能性がある

|   |   |
|---|---|
|説明|場合によっては、アプリが異なるアプリケーション ベースを持つ複数のアプリ ドメインを使用すると、アプリ ドメイン間で論理呼び出しコンテキストのオブジェクトを逆シリアル化しようとして、例外がスローされます。|
|提案される解決策|「[軽減策: アプリ ドメイン全体でのオブジェクトの逆シリアル化](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)」を参照してください。|
|スコープ|エッジ|
|Version|4.5.1|
|型|ランタイム|

