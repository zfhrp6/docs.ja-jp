---
title: "connectionManagement の &lt;clear&gt; 要素 (ネットワーク設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/clear"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#clear"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<clear> 要素, connectionManagement"
  - "<connectionManagement>, clear 要素"
  - "clear 要素, connectionManagement"
  - "connectionManagement, clear 要素"
ms.assetid: fb259282-84c4-4dc4-a226-78d904a6edc3
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# connectionManagement の &lt;clear&gt; 要素 (ネットワーク設定)
すべてのエントリを接続管理リストから削除します。  
  
## 構文  
  
```  
  
<clear/>  
  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
 なし。  
  
### 親要素  
  
|**要素**|**説明**|  
|------------|------------|  
|[connectionManagement](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|ネットワーク ホストへの接続の最大数を指定します。|  
  
## 解説  
 `clear` 要素は、接続管理リストからすべてのエントリを削除します。  
  
## 構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル \(Machine.config\) で使用できます。  
  
## 使用例  
 すべてのエントリを接続管理リストから削除し、サーバー www.contoso.com とそれ以外のすべてのネットワーク ホストの接続管理エントリを追加するコード例を次に示します。  
  
```  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <clear/>  
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