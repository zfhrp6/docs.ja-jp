---
title: "bypasslist の &lt;add&gt; 要素 (ネットワーク設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#add"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<add> 要素, bypasslist"
  - "<bypasslist>, add 要素"
  - "add 要素, bypasslist"
  - "bypasslist, add 要素"
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
caps.latest.revision: 17
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 17
---
# bypasslist の &lt;add&gt; 要素 (ネットワーク設定)
IP アドレスまたは DNS 名をプロキシ バイパス リストに追加します。  
  
## 構文  
  
```  
  
      <add   
   address = "regular expression"   
/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|**Attribute**|**説明**|  
|-------------------|------------|  
|**address**|IP アドレスまたは DNS 名を記述する正規表現。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|**要素**|**説明**|  
|------------|------------|  
|[bypasslist](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|プロキシを使用しないアドレスを記述する一連の正規表現を提供します。|  
  
## 解説  
 `add` 要素は、IP アドレスまたは DNS サーバー名を記述する正規表現を、プロキシ サーバーをバイパスするアドレスのリストに挿入します。  
  
 `address` 属性の値は、一組の IP アドレスまたはホスト名を記述する正規表現である必要があります。  
  
 この要素に正規表現を指定する場合は注意が必要です。  たとえば、"\[a\-z\]\+\\.contoso\\.com" という正規表現は、contoso.com ドメインの各ホストに一致しますが、contoso.com.cpandl.com ドメインの各ホストとも一致します。  contoso.com ドメインのホストとだけ一致させるためには、アンカーとして "$" を使用し、"\[a\-z\]\+\\.contoso\\.com$" のように記述します。  
  
 正規表現の詳細については、「[.NET Framework の正規表現](../../../../../docs/standard/base-types/regular-expressions.md)」を参照してください。  
  
## 構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル \(Machine.config\) で使用できます。  
  
## 使用例  
 2 つのアドレスをバイパス リストに追加するコード例を次に示します。  第 1 の例では、contoso.com ドメインにあるすべてのサーバーでプロキシをバイパスします。第 2 の例では、IP アドレスが 192.168 で始まるすべてのサーバーでプロキシをバイパスします。  
  
```  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## 参照  
 <xref:System.Net.WebProxy?displayProperty=fullName>   
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)