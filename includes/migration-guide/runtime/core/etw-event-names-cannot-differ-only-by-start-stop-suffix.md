### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a>サフィックスの "Start" または "Stop" のみで ETW イベント名を使い分けることができない

|   |   |
|---|---|
|説明|.NET Framework 4.6 と 4.6.1 では、2 つの ETW (Windows イベント トレーシング) イベント名の違いがサフィックスの &quot;Start&quot; または &quot;Stop&quot; のみのとき (たとえば、あるイベントの名前が <code>LogUser</code> で、別のイベントの名前が <code>LogUserStart</code> のとき)、ランタイムによって <xref:System.ArgumentException> がスローされます。 この場合、ランタイムはイベント ソースを作成できないため、ログ記録は生成できません。<ul><li>[X] 後方互換 // メカニズムを使用して、この機能をオン/オフにします。通常はランタイムの設定、AppContext または構成ファイルを使用します。 状況によっては自動的にオンにする必要があります。</li><li>[ ] ビルド時の中断 // 再コンパイルしようとした場合、中断されます</li></ul>|
|提案される解決策|この例外を回避するには、サフィックスの &quot;Start&quot; または &quot;Stop&quot; でしか違いのないイベント名が存在しないようにします。この要件は .NET Framework 4.6.2 以降で削除されています。サフィックスの &quot;Start&quot; と &quot;Stop&quot; のみが異なるイベント名がランタイムによって区別されます。|
|スコープ|エッジ|
|Version|4.6|
|型|ランタイム|

