---
title: "&lt;defaultProxy&gt; 要素 (ネットワーク設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<defaultProxy> 要素"
  - "defaultProxy 要素"
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
caps.latest.revision: 21
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 21
---
# &lt;defaultProxy&gt; 要素 (ネットワーク設定)
ハイパーテキスト転送プロトコル \(HTTP: Hypertext Transfer Protocol\) プロキシ サーバーを構成します。  
  
## 構文  
  
```  
  
        <defaultProxy  
  enabled="true|false"  
  useDefaultCredentials="true|false"  
  <bypasslist> … </bypasslist>  
  <proxy> … </proxy>  
  <module> … </module>  
/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|**要素**|**説明**|  
|------------|------------|  
|`enabled`|Web プロキシが使用されているかどうかを指定します。  既定値は `true` です。|  
|`useDefaultCredentials`|このホストに対する既定の資格情報が Web プロキシにアクセスするために使用されるかどうかを指定します。  既定値は `false` です。|  
  
### 子要素  
  
|**要素**|**説明**|  
|------------|------------|  
|[bypasslist](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|プロキシを使用しないアドレスを記述する一連の正規表現を提供します。|  
|[モジュール](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md)|新しいプロキシ モジュールをアプリケーションに追加します。|  
|[プロキシ](../../../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md)|プロキシ サーバーを定義します。|  
  
### 親要素  
  
|**要素**|**説明**|  
|------------|------------|  
|[system.  net](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|.NET Framework がネットワークに接続する方法を指定するための設定が含まれています。|  
  
## 解説  
 defaultProxy 要素が空の場合、Internet Explorer のプロキシ設定が使用されます。  この動作は、.NET Framework Version 1.1 とは異なります。  
  
 例外は <xref:System.Net.IWebProxy> クラスから [module](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) 要素で非パブリック型が指定されている場合、型派生していませんスローされます。このオブジェクトの既定のコンストラクターで例外が発生した、またはシステムが指定した既定のプロキシを取得している間に例外が発生しました。  例外の <xref:System.Exception.InnerException%2A> プロパティに、このエラーの根本的な原因に関する詳細情報が含まれています。  
  
## 構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル \(Machine.config\) で使用できます。  
  
## 使用例  
 Internet Explorer プロキシの既定値を使用し、プロキシ アドレスを指定し、ローカル アクセスおよび contoso.com のプロキシをバイパスするコード例を次に示します。  
  
```  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
      <bypasslist  
        <add address="[a-z]+\.contoso\.com" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## 参照  
 <xref:System.Net.WebProxy?displayProperty=fullName>   
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)