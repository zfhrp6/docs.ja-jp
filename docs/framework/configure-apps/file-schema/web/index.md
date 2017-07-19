---
title: "Web 設定スキーマ | Microsoft Docs"
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
  - "ASP.NET 構成システム, Web 設定スキーマ"
  - "構成ファイル [ASP.NET]"
  - "構成スキーマ [.NET Framework], [Web 設定]"
  - "スキーマ Web 設定"
  - "[Web 設定], スキーマ [ASP.NET]"
  - "Web.config 構成ファイル [ASP.NET]"
ms.assetid: ae1ac356-267d-4753-8d7a-7a04eb45a9be
caps.latest.revision: 6
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 6
---
# Web 設定スキーマ
Web 設定では、ASP.NET ホスト層で管理されるプロセス全体の動作に適用する、CPU および実行レベルの ASP.NET 設定を指定します。  これらの設定は、ASP.NET アプリケーションの Web.config ファイルで指定されるアプリケーション ドメイン型の設定とは異なります。  
  
 Web 設定は、.NET Framework の各バージョンのインストール フォルダーにある Aspnet.config ファイルに含まれています。  たとえば、[!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] の Aspnet.config ファイルは、次のフォルダーにあります。  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 Web 設定は、machine.config ファイル、ルートの Web.config ファイル、アプリケーション レベルの Web.config ファイルなどのその他の構成ファイルでは使用されません。  
  
 [\<configuration\> 要素](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<system.web\> 要素 \(Web 設定\)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)  
  
 [\<applicationPool\> 要素 \(Web 設定\)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)  
  
|要素|説明|  
|--------|--------|  
|[\<system.web\>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|ASP.NET ホスト層で使用される情報が含まれています。|  
|[\<applicationPool\>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|ASP.NET ホスト層で管理されるプロセス全体の動作に適用する、CPU および実行レベルの ASP.NET 設定を指定します。|  
  
## 参照  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)