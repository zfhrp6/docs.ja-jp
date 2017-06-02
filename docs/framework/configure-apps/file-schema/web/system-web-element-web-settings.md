---
title: "&lt;system.web&gt; 要素 (Web 設定) | Microsoft Docs"
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
  - "<system.Web> 要素"
  - "ASP.NET 構成システム"
  - "構成ファイル [ASP.NET]"
  - "system.Web 要素"
  - "Web.config 構成ファイル [ASP.NET]"
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# &lt;system.web&gt; 要素 (Web 設定)
プロセス全体の動作を ASP.NET ホスト層でどのように管理するかについての情報を含みます。  
  
## 構文  
  
```  
<system.web>  
</system.web>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<applicationPool\>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|aspnet.config ファイル内で、IIS アプリケーション プールの構成設定を指定します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<configuration\>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|共通言語ランタイムおよび [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] アプリケーションで使用されるすべての構成ファイルのルート要素を指定します。|  
  
## 解説  
 `system.web` 要素とその `applicationPool` 子要素は、[!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] で [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] に追加されました。  [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] 以降を統合モードで実行する場合、この要素を組み合わせて使用すると、ASP.NET が IIS アプリケーション プールでホストされているときに、ASP.NET でどのようにスレッドを管理し、どのように要求をキューに配置するかを構成できます。  [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] 以降をクラシック モードまたは ISAPI モードで実行する場合、これらの設定は無視されます。  
  
## 使用例  
 次の例は、ASP.NET が IIS アプリケーション プールでホストされているときの ASP.NET プロセス全体の動作を aspnet.config ファイルで構成する方法を示しています。  この例では、IIS が統合モードで実行されていること、およびアプリケーションが [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] 以降のバージョンを使用していることが前提になります。  この動作は、[!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] より前のバージョンの [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] では発生しません。  この例で指定している値は既定値です。  
  
```  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"   
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## 要素情報  
  
|||  
|-|-|  
|名前空間||  
|スキーマ名||  
|検証ファイル||  
|空も使用できる||  
  
## 参照  
 [\<applicationPool\> 要素 \(Web 設定\)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)