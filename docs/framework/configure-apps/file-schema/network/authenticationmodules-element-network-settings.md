---
title: "&lt;authenticationModules&gt; 要素 (ネットワーク設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<authenticationModules> 要素"
  - "authenticationModules 要素"
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
caps.latest.revision: 15
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 15
---
# &lt;authenticationModules&gt; 要素 (ネットワーク設定)
ネットワーク要求を認証するために使用するモジュールを指定します。  
  
## 構文  
  
```  
  
      <authenticationModules>   
</authenticationModules>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
  
|**要素**|**説明**|  
|------------|------------|  
|[add](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-authenticationmodules-network-settings.md)|認証モジュールをアプリケーションに追加します。|  
|[clear](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-authenticationmodules-network-settings.md)|すべての認証モジュールをアプリケーションから削除します。|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-authenticationmodules-network-settings.md)|認証モジュールをアプリケーションから削除します。|  
  
### 親要素  
  
|**要素**|**説明**|  
|------------|------------|  
|[system.net](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|.NET Framework がネットワークに接続する方法を指定するための設定が含まれています。|  
  
## 解説  
 `authenticationModule` 要素は、サーバーとの間の認証プロセスを実行する認証モジュールを指定します。  認証モジュールは、<xref:System.Net.IAuthenticationModule> インターフェイスを実装する必要があります。  
  
## 構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル \(Machine.config\) で使用できます。  
  
## 使用例  
 認証モジュールを有効にするコード例を次に示します。  Version の値および PublicKeyToken の値は、指定したモジュールに対応する正しい値に置き換える必要があります。  
  
```  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## 参照  
 <xref:System.Net.IAuthenticationModule>   
 <xref:System.Net.AuthenticationManager>   
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)