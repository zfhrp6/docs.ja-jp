---
title: "&lt;performanceCounters&gt; 要素 (ネットワーク設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<performanceCounter> 要素"
  - "performanceCounter 要素"
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;performanceCounters&gt; 要素 (ネットワーク設定)
ネットワーク パフォーマンス カウンターを有効または無効にします。  
  
## 構文  
  
```  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`enabled`|ネットワーク パフォーマンス カウンターが有効になっているかどうかを指定します。  既定値は `false` です。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[設定](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<xref:System.Net> 名前空間の基本的なネットワーク オプションを構成します。|  
  
## 解説  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル \(Machine.config\) で使用できます。  
  
 ネットワーク パフォーマンス カウンターは、使用される構成ファイルで有効になっている必要があります。  すべてのネットワーク パフォーマンス カウンターは、構成ファイル内の 1 つの設定で有効または無効にされます。  ネットワーク パフォーマンス カウンターを個別に有効または無効にすることはできません。  特定のネットワーク パフォーマンス カウンターの詳細については、「[Networking Performance Counters](http://msdn.microsoft.com/ja-jp/d1860235-f643-46ae-846c-ff0ed8b0e3cd)」を参照してください。  
  
 既定では、ネットワーク パフォーマンス カウンターは無効に設定されます。  
  
 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=fullName> プロパティを使用して、適用可能な構成ファイルから **enabled** 属性の現在の値を取得できます。  
  
## 使用例  
 <xref:System.Net> およびそれに関連する名前空間をネットワーク パフォーマンス カウンターを有効にするように構成する方法を次のコード例に示します。  
  
```  
<configuration>  
  <system.net>  
    <settings>  
      <performanceCounters  
        enabled="true"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## 参照  
 <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=fullName>   
 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=fullName>   
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)   
 [Networking Performance Counters](http://msdn.microsoft.com/ja-jp/d1860235-f643-46ae-846c-ff0ed8b0e3cd)