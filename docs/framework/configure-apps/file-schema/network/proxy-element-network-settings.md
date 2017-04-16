---
title: "&lt;proxy&gt; 要素 (ネットワーク設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<proxy> 要素"
  - "proxy 要素"
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
caps.latest.revision: 20
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 20
---
# &lt;proxy&gt; 要素 (ネットワーク設定)
プロキシ サーバーを定義します。  
  
## 構文  
  
```  
  
      <proxy   
  autoDetect="true|false|unspecified"    
  bypassonlocal="true|false|unspecified"   
  proxyaddress="uriString"  
  scriptLocation="uriString"   
  usesystemdefault="true|false|unspecified "   
/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|**Attribute**|**説明**|  
|-------------------|------------|  
|`autoDetect`|プロキシを自動的に検出するかどうかを指定します。  既定値は `unspecified` です。|  
|`bypassonlocal`|ローカル リソースの場合に、プロキシがバイパスされるかどうかを指定します。  ローカル リソースには、ローカル サーバー \(http:\/\/localhost、http:\/\/loopback、または http:\/\/127.0.0.1\) やピリオドのない URI \(http:\/\/webserver\) が含まれます。  既定値は `unspecified` です。|  
|`proxyaddress`|使用するプロキシ URI を指定します。|  
|`scriptLocation`|構成スクリプトの場所を指定します。|  
|`usesystemdefault`|Internet Explorer のプロキシ設定を使用するかどうかを指定します。  `true` に設定されている場合、後続の属性は Internet Explorer のプロキシ設定をオーバーライドします。  既定値は `unspecified` です。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|**要素**|**説明**|  
|------------|------------|  
|[defaultProxy](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|ハイパーテキスト転送プロトコル \(HTTP: Hypertext Transfer Protocol\) プロキシ サーバーを構成します。|  
  
## テキスト値  
  
## 解説  
 `proxy` 要素は、アプリケーションのプロキシ サーバーを定義します。  この要素が構成ファイルで見つからない場合、.NET Framework では、Internet Explorer のプロキシ設定が使用されます。  
  
 `proxyaddress` 属性の値は、整形式 URI \(Uniform Resource Indicator\) で指定する必要があります。  
  
 `scriptLocation` 属性は、プロキシ構成スクリプトの自動検出を意味します。  Internet Explorer で、**\[自動構成スクリプトを使用する\]** チェック ボックスがオンの場合、<xref:System.Net.WebProxy> クラスでは、構成スクリプト \(通常は Wpad.dat ファイル\) の検出が試みられます。  
  
 Version 2.0 に移行中の .NET Framework Version 1.1 アプリケーションの場合は、`usesystemdefault` 属性を使用してください。  
  
 `proxyaddress` 属性で無効な既定のプロキシが指定されている場合、例外がスローされます。  例外の <xref:System.Exception.InnerException%2A> プロパティに、このエラーの根本的な原因に関する詳細情報が含まれています。  
  
## 構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル \(Machine.config\) で使用できます。  
  
## 使用例  
 Internet Explorer プロキシの既定値を使用し、プロキシ アドレスを指定し、ローカル アクセスのプロキシをバイパスするコード例を次に示します。  
  
```  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## 参照  
 <xref:System.Net.WebProxy?displayProperty=fullName>   
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)