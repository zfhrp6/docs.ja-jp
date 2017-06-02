---
title: "&lt;webRequestModules&gt; 要素 (ネットワーク設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<webRequestModules> 要素"
  - "webRequestModules 要素"
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# &lt;webRequestModules&gt; 要素 (ネットワーク設定)
ネットワーク ホストからの情報を要求するために使用するモジュールを指定します。  
  
## 構文  
  
```  
  
      <webRequestModules>   
</webRequestModules>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
  
|**要素**|**説明**|  
|------------|------------|  
|[add](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-webrequestmodules-network-settings.md)|カスタム Web 要求モジュールをアプリケーションに追加します。|  
|[clear](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-webrequestmodules-network-settings.md)|登録されているすべての Web 要求モジュールをアプリケーションから削除します。|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-webrequestmodules-network-settings.md)|カスタム Web 要求モジュールをアプリケーションから削除します。|  
  
### 親要素  
  
|**要素**|**説明**|  
|------------|------------|  
|[system.net](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|.NET Framework がネットワークに接続する方法を指定するための設定が含まれています。|  
  
## 解説  
 `webRequestModules` 要素はネットワーク ホストへの情報要求を処理するために <xref:System.Net.WebRequest> クラスの子孫を登録します。  Web 要求モジュールは、<xref:System.Net.IWebRequestCreate> インターフェイスを実装する必要があります。  
  
 .NET Framework には、http:\/\/、https:\/\/、および file:\/\/ で始まる URI 用に、Web 要求モジュールが用意されています。  構成ファイルにカスタム モジュールを登録するだけで、既定のモジュールをオーバーライドできます。  
  
## 構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル \(Machine.config\) で使用できます。  
  
## 使用例  
 既定の HTTP モジュールを登録するコード例を次に示します。  Version の値および PublicKeyToken の値は、指定したモジュールに対応する正しい値に置き換える必要があります。  
  
```  
<configuration>  
  <system.net>  
    <webRequestModules>  
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
 <xref:System.Net.IWebRequestCreate>   
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)