---
title: "構成 (インターネット アプリケーションを) | Microsoft Docs"
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
  - "ダウンロード (インターネット リソースの)、既定のプロキシ"
  - "送信 (データを)、既定のプロキシ"
  - "受信 (データを)、既定のプロキシ"
  - "ダウンロード (インターネット リソースの)、構成 (インターネット アプリケーションを)"
  - "プロトコル固有のモジュール"
  - "カスタム認証モジュール"
  - "受信 (データを)、構成 (インターネット アプリケーションを)"
  - "構成の設定 [.NET Framework]、インターネット アプリケーション"
  - "要求 (インターネットからデータを)、構成 (インターネット アプリケーションを)"
  - "要求 (インターネットからデータを)、既定のプロキシ"
  - "インターネット要求への応答、既定のプロキシ"
  - "インターネット、構成 (インターネット アプリケーションを)"
  - "インターネット要求への応答、構成 (インターネット アプリケーションを)"
  - "既定のプロキシ"
  - "ネットワークのリソース、既定のプロキシ"
  - "送信 (データを)、構成 (インターネット アプリケーションを)"
  - "ネットワーク リソース、構成 (インターネット アプリケーションを)"
  - "インターネット、既定のプロキシ"
ms.assetid: bb707c72-eed2-4a82-8800-c9e68df2fd4f
caps.latest.revision: 15
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 15
---
# 構成 (インターネット アプリケーションを)
[\<system.Net\> 要素 \(ネットワーク設定\)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) の構成要素は、アプリケーションのネットワーク コンフィギュレーション情報が含まれます。  [\<system.Net\> 要素 \(ネットワーク設定\)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) の要素を使用して、プロキシ サーバーを設定できます。接続管理パラメータの設定、自分のアプリケーションに注文の認証および要求のモジュールが含まれます。  
  
 [\<defaultProxy\> 要素 \(ネットワーク設定\)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) の要素は `GlobalProxySelection` クラスによって返されたプロキシ サーバーを定義します。  どの <xref:System.Net.HttpWebRequest> 特定の値に <xref:System.Net.HttpWebRequest.Proxy%2A> 固有のプロパティがない既定のプロキシを使用します。  プロキシの住所の設定に加えて、プロキシを使用せず、プロキシがこの住所に使用する必要があることを指定できますサーバー住所の一覧を作成します。  
  
 、Microsoft Internet Explorer の設定がコンポーネントの設定と組み合わせて、取得後の優先順位でことを確認することが重要です。  
  
 次の例では、プロキシがこの住所に使用する必要がない contoso.com のドメインにあるサーバーへのすべての要求がプロキシをスキップするように指定されますがことを http:\/\/proxyserver に既定のプロキシ サーバーの住所を、および。  
  
```  
<configuration>  
    <system.net>  
        <defaultProxy>  
            <proxy  
                usesystemdefault = "false"  
                proxyaddress = "http://proxyserver:80"  
                bypassonlocal = "true"  
            />  
            <bypasslist>  
                <add address="http://[a-z]+\.contoso\.com/" />  
            </bypasslist>  
        </defaultProxy>  
    </system.net>  
</configuration>  
```  
  
 特定のサーバーまたは他のすべてのサーバーにするには、耐久性がある接続数をコンフィギュレーションするに [\<connectionManagement\> 要素 \(ネットワーク設定\)](../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) の要素を使用します。  次の例では、サーバーへの www.contoso.com 2 種類の耐久性がある接続、IP アドレス 192.168.1.2 のサーバーへの 4 種類の耐久性がある接続、およびそのほかすべてのサーバーへの 1 種類の耐久性がある接続を使用するアプリケーションのコンフィギュレーションを示します。  
  
```  
<configuration>  
    <system.net>  
        <connectionManagement>  
            <add address="http://www.contoso.com" maxconnection="2" />  
            <add address="192.168.1.2" maxconnection="4" />  
            <add address="*" maxconnection="1" />  
        </connectionManagement>  
    </system.net>  
</configuration>  
```  
  
 注文の認証のモジュールの [\<authenticationModules\> 要素 \(ネットワーク設定\)](../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) の要素をコンフィギュレーションします。  注文の認証のモジュールの <xref:System.Net.IAuthenticationModule> インターフェイスを行う必要があります。  
  
 次の例では、注文の認証モジュールのコンフィギュレーションを示します。  
  
```  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 インターネットのリソースの情報を要求するに対応する注文プロトコル モジュールを使用するようにアプリケーションをコンフィギュレーションするに [\<webRequestModules\> 要素 \(ネットワーク設定\)](../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) の要素を使用できます。  モジュールは指定 <xref:System.Net.IWebRequestCreate> インターフェイスを行う必要があります。  次の例のようにコンフィギュレーション ファイルで、カスタムのモジュールを指定して、既定の HTTP、HTTPS とファイルのモジュールを上書きできます。  
  
```  
<configuration>  
    <system.net>  
        <webRequestModules>  
            <add  
                prefix="HTTP"  
                type = "MyHttpRequest.dll, MyHttpRequestCreator"  
            />  
        </webRequestModules>  
    </system.net>  
</configuration>  
```  
  
## 参照  
 [.NET Framework のネットワーク プログラミング](../../../docs/framework/network-programming/index.md)   
 [ネットワーク設定スキーマ](../../../docs/framework/configure-apps/file-schema/network/index.md)   
 [\<system.Net\> 要素 \(ネットワーク設定\)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)