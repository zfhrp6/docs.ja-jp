---
title: "メンバー デザインのガイドライン | Microsoft Docs"
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
  - "メンバー デザインのガイドラインは、メンバーのデザイン ガイドライン [.NET Framework]"
  - "メンバー [.NET Framework] のデザイン ガイドライン"
  - "クラス ライブラリ デザインのガイドライン [.NET Framework] のメンバー"
  - "メンバー デザインのガイドライン [.NET Framework]"
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# メンバー デザインのガイドライン
メソッド、プロパティ、イベント、コンス トラクター、およびフィールドは、メンバーとしてまとめて呼ばれます。 メンバーが、最終的に、フレームワークのエンドユーザーに、framework の機能が公開されていることを意味します。  
  
 メンバーは、仮想または非仮想、具体的なまたは抽象クラスで静的メソッドまたはインスタンスにすることができ、ユーザー補助機能のいくつかの異なるスコープができます。 このすべてのバリエーション驚異的な表現力には、同時に、framework デザイナー側注意が必要です。  
  
 この章では、任意の型のメンバーをデザインするときに従う必要が基本的なガイドラインを提供します。  
  
## このセクションの内容  
 [メンバーのオーバー ロード](../../../docs/standard/design-guidelines/member-overloading.md)  
 [プロパティのデザイン](../../../docs/standard/design-guidelines/property.md)  
 [コンス トラクターのデザイン](../../../docs/standard/design-guidelines/constructor.md)  
 [イベントのデザイン](../../../docs/standard/design-guidelines/event.md)  
 [フィールドのデザイン](../../../docs/standard/design-guidelines/field.md)  
 [拡張メソッド](../../../docs/standard/design-guidelines/extension-methods.md)  
 [演算子のオーバー ロード](../../../docs/standard/design-guidelines/operator-overloads.md)  
 [パラメーターのデザイン](../../../docs/standard/design-guidelines/parameter-design.md)  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)