---
title: "パラメーターの名前を付ける | Microsoft Docs"
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
  - "パラメーター名"
  - "パラメーターの名前 [.NET Framework]"
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# パラメーターの名前を付ける
読みやすさの明らかなため、以外には、パラメーターがドキュメントでは、デザイナーで表示される Intellisense とクラス参照機能を提供するビジュアル デ ザイン ツールとためパラメーター名に関するガイドラインに従う必要があります。  
  
 **✓ は** パラメーター名の camel 表記を使用します。  
  
 **✓ は** わかりやすいパラメーター名を使用します。  
  
 **✓ を検討してください** パラメーターの型ではなく、パラメーターの意味に基づく名前を使用します。  
  
### 演算子のオーバー ロードのパラメーターの名前を付ける  
 **✓ は** を使用して `left` と `right` パラメーターに意味がない場合は、二項演算子のオーバー ロード パラメーター名にします。  
  
 **✓ は** を使用して `value` の単項演算子のオーバー ロードのパラメーター名、パラメーターの意味がない場合。  
  
 **✓ を検討してください** 大きな価値が増加している場合、オーバー ロードのパラメーターの演算子にわかりやすい名前。  
  
 **X のしないで** 使用略語や数値の添字演算子のオーバー ロードのパラメーターの名前。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)   
 [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)