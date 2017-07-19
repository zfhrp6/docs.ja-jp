---
title: "&lt;Uri&gt; 要素 (Uri 設定) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;Uri&gt; 要素 (Uri 設定)
URI \(Uniform Resource Identifier\) で表現された Web アドレスが .NET Framework によってどのように処理されるかの設定を格納します。  
  
## スキーマの階層  
 [\<configuration\> 要素](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<uri\>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
## 構文  
  
```  
<uri>  
</uri>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
  
|**要素**|**説明**|  
|------------|------------|  
|[idn](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|国際化ドメイン名 \(IDN: Internationalized Domain Name\) による解析をドメイン名に適用するかどうかを指定します。|  
|[iriParsing](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|IRI \(International Resource Identifier\) 解析を <xref:System.Uri> に適用するかどうか、および IRI の解析規則を適用するかどうかを指定します。|  
|[schemeSettings](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<xref:System.Uri> が特定のスキーマに対して解析される方法を指定します。|  
  
### 親要素  
  
|**要素**|**説明**|  
|------------|------------|  
|[適用](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|すべての名前空間の設定が含まれています。|  
  
## 解説  
 `uri` 要素には、<xref:System.Net> 名前空間のクラスによって使用される <xref:System.Uri> クラスのメンバーの設定が格納されます。  これらの設定によって、IRI および IDN のサポートが構成されます。  
  
## 例  
  
### 説明  
 次のコード例は、<xref:System.Uri> クラスで IRI の解析および IDN 名をサポートするための構成を示しています。  また、この例では、すべてのスキーム設定を消去してから、http スキームのパーセント記号をエンコードしたパス区切り記号をエスケープしないように設定します。  
  
### コード  
  
```  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## 参照  
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)