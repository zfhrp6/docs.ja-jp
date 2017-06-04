---
title: "&lt;appDomainResourceMonitoring&gt; 要素 | Microsoft Docs"
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
helpviewer_keywords: 
  - "<appDomainResourceMonitoring> 要素"
  - "appDomainResourceMonitoring 要素"
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# &lt;appDomainResourceMonitoring&gt; 要素
プロセスの有効期間中、プロセス内のすべてのアプリケーション ドメインに関する統計情報を収集するようにランタイムに指示します。  
  
## 構文  
  
```  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`enabled`|必須の属性です。<br /><br /> アプリケーション ドメインのリソース監視に関する統計情報を収集するかどうかを指定します。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|`true`|アプリケーション ドメインのリソース監視に関する統計情報が収集されます。|  
|`false`|アプリケーション ドメインのリソース監視に関する統計情報は収集されません。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## 解説  
 アプリケーション ドメインのリソース監視は、マネージ アプリケーション ドメイン クラス、[ICLRAppDomainResourceMonitor](../../../../../ocs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) ホスト インターフェイス、および Windows イベント トレーシング \(ETW\) を通じて実現されます。  監視を有効にすると、プロセスの有効期間中、プロセス内のすべてのアプリケーション ドメインに関する統計情報が収集されます。  
  
 マネージ コードから監視を有効にするには、<xref:System.AppDomain.MonitoringIsEnabled%2A> プロパティを使用します。  
  
 この構成要素は、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 以降でのみ使用できます。  
  
## 使用例  
 アプリケーション ドメインのリソース監視を有効にする方法を次の例に示します。  
  
```  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## 参照  
 <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=fullName>   
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)