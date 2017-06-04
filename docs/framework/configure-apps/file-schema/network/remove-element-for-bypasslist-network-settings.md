---
title: "bypasslist の &lt;remove&gt; 要素 (ネットワーク設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#remove"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<bypasslist>, remove 要素"
  - "bypasslist, remove 要素"
  - "remove 要素, bypasslist"
  - "remove 要素, bypasslist"
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
caps.latest.revision: 16
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 16
---
# bypasslist の &lt;remove&gt; 要素 (ネットワーク設定)
IP アドレスまたは DNS 名をプロキシ バイパス リストから削除します。  
  
## 構文  
  
```  
  
      <remove   
   name = "regular expression"   
/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|**Attribute**|**説明**|  
|-------------------|------------|  
|`name`|IP アドレスまたは DNS 名を記述する正規表現。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|**要素**|**説明**|  
|------------|------------|  
|[bypasslist](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|プロキシを使用しないアドレスを記述する一連の正規表現を提供します。|  
  
## 解説  
 `remove` 要素は、IP アドレスまたは DNS サーバー名を記述する正規表現を、プロキシ サーバーをバイパスするアドレスのリストから削除します。  アドレスは構成ファイルまたは構成階層の上位レベルで既に定義されています。  
  
 `name` 属性の値は、一組の IP アドレスまたはホスト名を記述する正規表現である必要があります。  
  
 正規表現の詳細については、「[.NET Framework の正規表現](../../../../../docs/standard/base-types/regular-expressions.md)」を参照してください。  
  
## 構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル \(Machine.config\) で使用できます。  
  
## 使用例  
 adventure\-works.com ドメインで既に定義されているすべてのエントリを削除し、contoso.com ドメインをバイパス リストに追加するコード例を次に示します。  
  
```  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <remove name = "[a-z]+\.adventure-works\.com$" />  
        <add address="[a-z]+\.contoso\.com$" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## 参照  
 <xref:System.Net.WebProxy?displayProperty=fullName>   
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)