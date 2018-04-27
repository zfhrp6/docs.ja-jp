### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a>.NET Framework 1.1 および 2.0 からのマネージド ブラウザーでのコントロールのホストがブロックされる

|   |   |
|---|---|
|説明|これらのコントロールのホストは、Internet Explorer でブロックされます。|
|提案される解決策|Internet Explorer では、マネージ ブラウザーを使用してコントロールをホストするアプリケーションは起動できません。 以前の動作を復元するには、レジストリ サブキー <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> の EnableIEHosting 値を、x86 システム用および x64 システム上の 32 ビット プロセス用に <code>1</code> に設定し、レジストリ サブキー <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> の <code>EnableIEHosting</code> 値を x64 システム上の 64 ビット プロセス用に <code>1</code> に設定します。|
|スコープ|マイナー|
|Version|4.5|
|型|ランタイム|

