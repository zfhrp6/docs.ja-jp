---
title: "connectionManagement の &lt;remove&gt; 要素 (ネットワーク設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/remove"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#remove"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<connectionManagement>, remove 要素"
  - "<remove> 要素, connectionManagement"
  - "connectionManagement, remove 要素"
  - "remove 要素, connectionManagement"
ms.assetid: 94b81775-5a22-4975-8c47-8620c40c3f35
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# connectionManagement の &lt;remove&gt; 要素 (ネットワーク設定)
IP アドレスまたは DNS 名を接続管理リストから削除します。  
  
## 構文  
  
```  
  
      <remove   
   name = "server name or IP address"   
/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|**Attribute**|**説明**|  
|-------------------|------------|  
|`address`|IP アドレスまたは DNS 名。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|**要素**|**説明**|  
|------------|------------|  
|[connectionManagement](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|ネットワーク ホストへの接続の最大数を指定します。|  
  
## 解説  
 `remove` 要素は、指定されたサーバーの接続管理リスト エントリを削除します。  
  
 `address` 属性の値は、有効な IP アドレスまたはホスト名である必要があります。  
  
## 構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル \(Machine.config\) で使用できます。  
  
## 使用例  
 サーバー www.adventure\-works.com のすべての接続管理リスト エントリを削除し、アプリケーションの構成でサーバー www.contoso.com への接続数を 4、それ以外のすべてのサーバーへの接続数を 2 に指定するコード例を次に示します。  
  
```  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <remove address = "http://www.adventure-works.com"/>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## 参照  
 <xref:System.Net.ServicePoint>   
 <xref:System.Net.ServicePointManager>   
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)