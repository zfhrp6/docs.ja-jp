---
title: "webRequestModules の &lt;remove&gt; 要素 (ネットワーク設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#remove"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<remove> 要素, webRequestModules"
  - "<webRequestModules>, remove 要素"
  - "remove 要素, webRequestModules"
  - "webRequestModules, remove 要素"
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# webRequestModules の &lt;remove&gt; 要素 (ネットワーク設定)
カスタム Web 要求モジュールをアプリケーションから削除します。  
  
## 構文  
  
```  
  
      <remove   
  name = "URI prefix"   
/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|**Attribute**|**説明**|  
|-------------------|------------|  
|`name`|この Web 要求モジュールで処理される要求の URI プレフィックス。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|**要素**|**説明**|  
|------------|------------|  
|[webRequestModules](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|ネットワーク ホストからの情報を要求するために使用するモジュールを指定します。|  
  
## 解説  
 `remove` 要素では、指定された URI プレフィックスに対する登録済み Web 要求モジュールを削除します。  
  
 `prefix` 属性の値は、"http" や "http:\/\/www.contoso.com" のように、有効な URI の先行文字である必要があります。  
  
## 構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル \(Machine.config\) で使用できます。  
  
## 使用例  
 HTTP 用の既存の Web 要求モジュールを削除し、www.contoso.com に対する HTTP 要求用の新規カスタム Web 要求モジュールを登録するコード例を次に示します。  
  
```  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <remove prefix = "http">  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## 参照  
 <xref:System.Net.WebRequest>   
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)