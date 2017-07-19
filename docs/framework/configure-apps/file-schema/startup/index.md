---
title: "スタートアップ設定スキーマ | Microsoft Docs"
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
  - "構成スキーマ [.NET Framework], スタートアップ設定"
  - "スキーマ スタートアップ設定"
  - "スタートアップ設定スキーマ"
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# スタートアップ設定スキーマ
スタートアップ設定で、アプリケーションを実行する共通言語ランタイムのバージョンが指定されます。  
  
|要素|説明|  
|--------|--------|  
|[\<requiredRuntime\>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|共通言語ランタイムのバージョン 1.0 だけがアプリケーションでサポートされることを指定します。  ランタイム バージョン 1.1 で作成されたアプリケーションは **\<supportedRuntime\>** 要素を使用する必要があります。|  
|[\<supportedRuntime\>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|アプリケーションでサポートされる共通言語ランタイムのバージョンを指定します。|  
|[\<スタートアップ\>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|**\<requiredRuntime\>** と **\<supportedRuntime\>** 要素が含まれています。|  
  
## 参照  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<PaveOver\> Specifying Which Runtime Version to Use](http://msdn.microsoft.com/ja-jp/c376208d-980d-42b4-865b-fbe0d9cc97c2)