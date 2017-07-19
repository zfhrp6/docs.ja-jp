---
title: "&lt;configuration&gt; 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<configuration> 要素"
  - "configuration 要素"
  - "コンテナー タグ, <configuration> 要素"
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
caps.latest.revision: 15
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# &lt;configuration&gt; 要素
共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。  
  
 **\<configuration\>**  
  
## 構文  
  
```  
  
      <configuration>   
   <!-- configuration settings -->   
</configuration>  
```  
  
## 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<assemblyBinding\> 要素](../../../../docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)|構成レベルでのアセンブリ バインディング ポリシーを指定します。|  
|[スタートアップ設定スキーマ](../../../../docs/framework/configure-apps/file-schema/startup/index.md)|スタートアップ設定スキーマのすべての要素。|  
|[ランタイム設定スキーマ](../../../../docs/framework/configure-apps/file-schema/runtime/index.md)|ランタイム設定スキーマのすべての要素。|  
|[リモート処理設定スキーマ](http://msdn.microsoft.com/ja-jp/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e)|リモート処理設定スキーマのすべての要素。|  
|[ネットワーク設定スキーマ](../../../../docs/framework/configure-apps/file-schema/network/index.md)|ネットワーク設定スキーマのすべての要素。|  
|[暗号設定スキーマ](../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)|暗号設定スキーマのすべての要素。|  
|[構成セクション スキーマ](../../../../docs/framework/configure-apps/file-schema/configuration-sections-schema.md)|構成セクション設定スキーマのすべての要素。|  
|[トレースおよびデバッグ設定のスキーマ](../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)|トレースおよびデバッグ設定スキーマのすべての要素。|  
|[ASP.NET 設定スキーマ](http://msdn.microsoft.com/ja-jp/116608f3-c03d-4413-9fc7-978703e18b0f)|ASP.NET 構成スキーマのすべての要素。これには、ASP.NET Web サイトおよびアプリケーションを構成するための要素が含まれます。  Web.config ファイルで使用します。|  
|[XML Web サービス設定スキーマ](http://msdn.microsoft.com/ja-jp/f84d6d55-1add-4eb7-ae46-33df5833ea2e)|Web サービス設定スキーマのすべての要素。|  
|[Web 設定スキーマ](../../../../docs/framework/configure-apps/file-schema/web/index.md)|IIS などのホスト アプリケーションと ASP.NET の連携を構成する要素も含め、Web 設定スキーマのすべての要素。  aspnet.config ファイルで使用します。|  
  
## 解説  
 各構成ファイルは **\<configuration\>** の 1 要素を一つだけ含める必要があります。  
  
## 参照  
 [構成ファイル スキーマ](../../../../docs/framework/configure-apps/file-schema/index.md)