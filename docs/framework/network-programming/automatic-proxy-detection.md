---
title: "自動プロキシ検出 | Microsoft Docs"
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
helpviewer_keywords: 
  - "自動プロキシ検出"
  - "Web プロキシの自動検出"
  - "Web プロキシ"
  - "検出 (プロキシを自動的に)"
  - "WebProxy クラス、自動プロキシ検出"
  - "プロキシ、自動検出"
  - "ネットワーク"
  - "WPAD (Web プロキシ自動検出)"
ms.assetid: fcd9c3bd-93de-4c92-8ff3-837327ad18de
caps.latest.revision: 18
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 18
---
# 自動プロキシ検出
自動プロキシの検出は Web プロキシ サーバーがシステムによって確認され、クライアントに代わって要求を送信するに使用されるプロセスです。  この機能は、WPAD \(Web Proxy Auto\-Discovery\) とも呼ばれます。  自動ときにプロキシの検出、要求に使用できるプロキシのセットを返品する担当プロキシ コンポーネントのスクリプトを探すシステムの再試行有効になります。  プロキシ コンポーネントのスクリプトがある場合は、スクリプトがプロキシ情報、要求のストリーム、つまり回答が <xref:System.Net.WebProxy> のインスタンスを使用する要求に対して取得した場合、コンパイル、ローカル コンピュータのダウンロード実行されます。  
  
 自動プロキシの検出は <xref:System.Net.WebProxy> クラスが実行され、コンフィギュレーション ファイルの要求レベルの設定、Internet Explorer の **\[ローカル エリア ネットワーク \(LAN\)\]** のダイアログ ボックスを使用して指定した設定、および設定を使用することもできます。  
  
> [!NOTE]
>  Internet Explorer のメイン メニューから **\[ツール\]** を選択し、**\[インターネット オプション\]**を選択することにより、Internet Explorer の **\[ローカル エリア ネットワーク \(LAN\) の設定\]** のダイアログ ボックスを表示できます。  次 **\[接続\]**、のタブをクリックし、**\[LAN の設定\]**をクリックします。  
  
 自動ときに検出プロキシには、次のように、スクリプト プロキシのコンフィギュレーションを検索 <xref:System.Net.WebProxy> クラスの再試行有効化されます:  
  
1.  WinInet の `InternetQueryOption` 機能が最新 Internet Explorer プロキシのコンフィギュレーションが検出するスクリプトの検索に使用されます。  
  
2.  スクリプトが見つけられなければ、<xref:System.Net.WebProxy> クラスは、スクリプトの検索に動的ホスト コンフィギュレーション Protocol \(DHCP\) を使用します。  DHCP サーバー、スクリプトの場所 \(ホスト名\) またはスクリプトの完全な URL と応答できます。  
  
3.  DHCP が WPAD のホストを識別する名前は、DNS またはエイリアスとして WPAD のホストにただされます。  
  
4.  ホストされていないプロキシを識別し、コンフィギュレーションのスクリプトの場所が Internet Explorer の LAN 設定やコンフィギュレーション ファイルを使用して指定されている場合、この場所が使用されます。  
  
> [!NOTE]
>  NT として実行が開始アプリケーションのユーザーの Internet Explorer のプロキシ サーバーの設定 \(利用可能な場合\) サービスまたは ASP.NET の一部として使用されます。  これらの設定は、すべてのサービス アプリケーションに使用可能ではない場合があります。  
  
 プロキシに基づいて単位で connectoid でコンフィギュレーションされます。  connectoid は、ネットワーク接続ダイアログの品目で、物理ネットワークのデバイス \(またはモデム イーサネット カード\) または仮想のインターフェイスのいずれかです \(ネットワークのデバイスに実行の接続 VPN など\)。  connectoid が \(たとえば、無線接続がアクセス ポイントを変更、または VPN が有効になります\) 変更すると、プロキシの検出のアルゴリズムを再度実行されます。  
  
 既定では、Internet Explorer のプロキシ設定がプロキシを検出するために使用されます。  自分のアプリケーションが非対話型アカウントで \(IE プロキシの設定をコンフィギュレーションする便利な方法で\) を実行中または IE の設定とは異なるプロキシ設定を使用する場合は、定義された [\<defaultProxy\> 要素 \(ネットワーク設定\)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) と [\<proxy\> 要素 \(ネットワーク設定\)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) の要素でコンフィギュレーション ファイルの作成に応じて、プロキシをコンフィギュレーションできます。  
  
 作成した要求の場合、次のコード例で示すように要求を含む空白の <xref:System.Net.WebRequest.Proxy%2A> を使用して、レベル自動プロキシの検出を依頼して無効にすることができます。  
  
```csharp  
public static void DisableForMyRequest (Uri resource)  
{  
    WebRequest request = WebRequest.Create (resource);  
    request.Proxy = null;  
    WebResponse response = request.GetResponse ();  
}  
```  
  
```vb  
Public Shared Sub DisableForMyRequest(ByVal resource As Uri)  
    Dim request As WebRequest = WebRequest.Create(resource)  
    request.Proxy = Nothing  
    Dim response As WebResponse = request.GetResponse()  
    End Sub   
```  
  
 <xref:System.Net.WebRequest.DefaultWebProxy%2A> のプロパティに使用可能であるプロキシの使用が自分のアプリケーション ドメインの既定のプロキシない要求。  
  
## 参照  
 <xref:System.Net.WebProxy>   
 <xref:System.Net.WebRequest>   
 [\<system.Net\> 要素 \(ネットワーク設定\)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)