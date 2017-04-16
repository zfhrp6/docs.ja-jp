---
title: "リソースの名前付け | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "リソースのローカライズされた名前 [.NET Framework]"
  - "ローカリゼーションでは、名前付けのガイドライン"
  - "リソース名"
  - "名前付けのガイドライン、グローバル アプリケーション"
  - "名前付けのガイドライン、国際対応のアプリケーション"
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# リソースの名前付け
場合プロパティと同様、特定のオブジェクトを使用してローカライズ可能なリソースを参照できる、ので、リソースの名前付けのガイドラインは、プロパティのガイドラインに似ています。  
  
 **✓ は** リソース キーで pascal 表記を使用を使用します。  
  
 **✓ は** 短い識別子ではなくわかりやすいを提供します。  
  
 **X のしないで** メインの CLR 言語の言語に固有のキーワードを使用します。  
  
 **✓ は** のみ英数字とアンダー スコアのリソースの名前付けに使用します。  
  
 **✓ は** 例外メッセージ リソースの名前付け規則を使用します。  
  
 リソース識別子は、例外の種類名と、例外の短い識別子にする必要があります。  
  
 `ArgumentExceptionIllegalCharacters`   
 `ArgumentExceptionInvalidName`   
 `ArgumentExceptionFileNameIsMalformed`  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)   
 [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)