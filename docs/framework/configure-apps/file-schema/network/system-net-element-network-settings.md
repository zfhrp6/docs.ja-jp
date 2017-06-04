---
title: "&lt;system.Net&gt; 要素 (ネットワーク設定) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<system.Net> 要素"
  - "system.Net 要素"
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# &lt;system.Net&gt; 要素 (ネットワーク設定)
.NET Framework がネットワークに接続する方法を指定するための設定が含まれています。  
  
## 構文  
  
```  
  
      <system.net>   
</system.net>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
  
|**要素**|**説明**|  
|------------|------------|  
|[authenticationModules](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|インターネット要求を認証するために使用するモジュールを指定します。|  
|[connectionManagement](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|インターネット ホストへの接続の最大数を指定します。|  
|[defaultProxy](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|ハイパーテキスト転送プロトコル \(HTTP: Hypertext Transfer Protocol\) プロキシ サーバーを構成します。|  
|[mailSettings](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|SMTP \(Simple Mail Transport Protocol\) の電子メール送信オプションを設定します。|  
|[requestCaching](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|ネットワーク要求のキャッシュ機構を制御します。|  
|[設定](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<xref:System.Net> 名前空間および関連する子名前空間内のクラスの基本的なネットワーク オプションを構成します。|  
|[\<webRequestModules\> 要素 \(ネットワーク設定\)](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|インターネット ホストからの情報を要求するために使用するモジュールを指定します。|  
  
### 親要素  
  
|**要素**|**説明**|  
|------------|------------|  
|[適用](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|すべての名前空間の設定が含まれています。|  
  
## 解説  
 [\<system.net\>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md) 要素は <xref:System.Net> および関連する子名前空間内のクラスの設定が含まれます。  この設定により、認証モジュール、接続管理、メール設定、プロキシ サーバー、およびインターネット ホストから情報を受け取るためのインターネット要求モジュールが構成されます。  
  
## 使用例  
 <xref:System.Net> クラスで使用される一般的な構成を次のコード例に示します。  
  
```  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type = "System.Net.DigestClient" />  
      <add type = "System.Net.NegotiateClient" />  
      <add type = "System.Net.KerberosClient" />  
      <add type = "System.Net.NtlmClient" />  
      <add type = "System.Net.BasicClient" />  
    </authenticationModules>  
    <connectionManagement>  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
    <defaultProxy>  
      <proxy  
        usesystemdefault = "true"  
        bypassonlocal = "true"  
      />  
    </defaultProxy>  
    <webRequestModules>  
      <add prefix = "http"  
        type = "System.Net.HttpRequestCreator"  
      />  
      <add prefix = "https"  
        type = "System.Net.HttpRequestCreator"  
      />  
      <add prefix = "file"  
        type = "System.Net.FileWebRequestCreator"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## 参照  
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)