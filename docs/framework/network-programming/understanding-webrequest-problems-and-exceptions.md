---
title: "WebRequest の問題と例外について | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 74a361a5-e912-42d3-8f2e-8e9a96880a2b
caps.latest.revision: 6
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 6
---
# WebRequest の問題と例外について
<xref:System.Net.WebRequest> および派生クラス \(<xref:System.Net.HttpWebRequest>、<xref:System.Net.FtpWebRequest>と <xref:System.Net.FileWebRequest>\) が非常にステータスを通知するための例外を投げます。  場合によってはこれらの問題の解決策は明らかではありません。  
  
## 解決策  
 問題を確認するに <xref:System.Net.WebException> の <xref:System.Net.WebException.Status%2A> のプロパティを確認します。  次の表に、複数のステータスの値と考えられる決済を示します。  
  
|状態|詳細|解決方法|  
|--------|--------|----------|  
|<xref:System.Net.WebExceptionStatus><br /><br /> または<br /><br /> <xref:System.Net.WebExceptionStatus>|基になるソケットに問題があります。  接続がリセットされる場合があります。|要求を再接続し、再送信します。<br /><br /> 最新のサービス パックをインストールしてください。<br /><br /> <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A?displayProperty=fullName> のプロパティの値を増やします。<br /><br /> \[<xref:System.Net.HttpWebRequest.KeepAlive%2A?displayProperty=fullName>\] を \[`false`\] に設定します。<br /><br /> <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> のプロパティを含む最大の接続数を上げます。<br /><br /> プロキシ コンフィギュレーションを確認します。<br /><br /> SSL を使用している場合は、サーバー プロセスに証明書ストアをアクセス許可があることを確認します。<br /><br /> 大量のデータを送信する場合は、`false`に <xref:System.Net.HttpWebRequest.AllowWriteStreamBuffering%2A> を設定します。|  
|<xref:System.Net.WebExceptionStatus>|サーバーる証明書ができませんでした。|Internet Explorer を使用して URI を開くとします。  IE によって表示される警報セキュリティを設定します。  セキュリティ警報を解決できない場合、<xref:System.Net.ICertificatePolicy> を `true`返品を実行し、<xref:System.Net.ServicePointManager.CertificatePolicy%2A>に渡す証明書のポリシーのクラスを作成できます。<br /><br /> 参照 [http:\/\/support.microsoft.com\/?id\=823177](http://go.microsoft.com/fwlink/?LinkID=179653)します。<br /><br /> サーバー証明書に署名する証明機関の証明書が Internet Explorer の信頼済証明機関の一覧に追加されることを確認します。<br /><br /> URL のホスト名がサーバー証明書の共通名と一致していることを確認します。|  
|<xref:System.Net.WebExceptionStatus>|エラーが SSL のトランザクションの未収、または証明書問題があります。|.NET Framework Version 1.1 が SSL のバージョンのみ 3.0 はできません。  サーバーが TLS のバージョン 1.0 または 2.0 SSL のバージョンを使用すると、例外が投げられます。  .NET Framework Version 2.0 をにアップグレードし、サーバーに合わせて <xref:System.Net.ServicePointManager.SecurityProtocol%2A> を設定します。<br /><br /> 証明書クライアントとサーバーが信頼しない証明機関 \(CA\) が署名されています。  CA 証明書のサーバーをインストール。  " "を参照してください。[http:\/\/support.microsoft.com\/?id\=332077](http://go.microsoft.com/fwlink/?LinkID=179654)<br /><br /> 最新のサービス パックをインストールする必要があります。|  
|<xref:System.Net.WebExceptionStatus>|接続に失敗しました。|ファイアウォールまたはプロキシは接続をブロック。  接続を許可する場合は、ファイアウォールまたはプロキシを変更します。<br /><br /> 明示的に <xref:System.Net.WebProxy> のコンストラクターの呼び出し、クライアント アプリケーションの <xref:System.Net.WebProxy> を表示します \(WebServiceProxyClass.Proxy \= 新しい WebProxy \([http:\/\/server:80](http://server/)、など\)。\)<br /><br /> ワーカー プロセス ID に WSPWSP.dll、HKLM \\ SYSTEM \\ CurrentControlSet \\ Services \\ DnsCache アクセスを必要なアクセス許可がまたは HKLM \\ SYSTEM \\ CurrentControlSet \\ Services \\ WinSock2 あることを確認するに Filemon または Regmon を実行します。|  
|<xref:System.Net.WebExceptionStatus>|ドメイン ネーム サービスをホスト名を解決しませんでした。|プロキシを正しくコンフィギュレーションします。  " "を参照してください。[http:\/\/support.microsoft.com\/?id\=318140](http://go.microsoft.com/fwlink/?LinkID=179655)<br /><br /> インストール アンチウィルスのソフトウェアまたはファイアウォールが接続をブロックことを確認します。|  
|<xref:System.Net.WebExceptionStatus>|<xref:System.Net.WebRequest.Abort%2A> 名前はされた、またはエラーが発生しました。|この問題は、クライアントまたはサーバーの連結負荷によって起こされる場合があります。  負荷の引き下げ。<br /><br /> <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> の配置を上げます。<br /><br /> Web サービスの提供の設定を変更するに [http:\/\/support.microsoft.com\/?id\=821268](http://go.microsoft.com/fwlink/?LinkID=179656) は、" "を参照してください。|  
|<xref:System.Net.WebExceptionStatus>|アプリケーションが既に閉じられているソケットに作成するに努めました。|クライアントまたはサーバーには過ぎられます。  負荷の引き下げ。<br /><br /> <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> の配置を上げます。<br /><br /> Web サービスの提供の設定を変更するに [http:\/\/support.microsoft.com\/?id\=821268](http://go.microsoft.com/fwlink/?LinkID=179656) は、" "を参照してください。|  
|<xref:System.Net.WebExceptionStatus>|メッセージの長さのそのほか \(<xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>\) を超えています。|<xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A> のプロパティの値を増やします。|  
|<xref:System.Net.WebExceptionStatus>|ドメイン ネーム サービスがプロキシのホスト名を解決しませんでした。|プロキシを正しくコンフィギュレーションします。  " "を参照してください。[http:\/\/support.microsoft.com\/?id\=318140](http://go.microsoft.com/fwlink/?LinkID=179655)<br /><br /> `null`に <xref:System.Net.HttpWebRequest.Proxy%2A> のプロパティを設定することにより、プロキシを使用するには、<xref:System.Net.HttpWebRequest> を強制的にします。|  
|<xref:System.Net.WebExceptionStatus>|サーバーからの応答は有効な HTTP 応答ではありません。  この問題は HTTP サーバー 1.1 の RFC に適合しないことを .NET Framework が検出する際に。  この問題が応答に正しくないヘッダーを追加、または誤ったヘッダー delimiters.RFC 2616 がサーバーからの応答の HTTP 1.1 と有効な形式を定義するときに発生することがあります。  詳細については、[http:\/\/www.ietf.org](http://go.microsoft.com/fwlink/?LinkID=147388)" "を参照してください。|トランザクションのネットワーク追跡を取得し、回答のヘッダーを確認します。<br /><br /> \(これはセキュリティ問題にすることもできます\)、アプリケーションで分析せずにサーバーの応答が必要な場合は、コンフィギュレーション ファイルの `true` に `useUnsafeHeaderParsing` を設定します。  「[\<httpWebRequest\> 要素 \(ネットワーク設定\)](../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md)」を参照してください。|  
  
## 参照  
 <xref:System.Net.HttpWebRequest>   
 <xref:System.Net.HttpWebResponse>   
 <xref:System.Net.Dns>