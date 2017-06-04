---
title: "機能拡張のデザイン | Microsoft Docs"
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
  - "クラス ライブラリを拡張します。"
  - ".NET framework クラス ライブラリによる拡張機能"
  - "クラス ライブラリ デザインのガイドライン [.NET Framework] の機能拡張"
  - "クラス ライブラリの機能拡張 [.NET Framework]"
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 機能拡張のデザイン
フレームワークの設計の 1 つの重要な側面を行って、framework の機能拡張は慎重に考慮されていることを確認しています。 これは、コストとさまざまな機能拡張機構に関連付けられている利点を理解することが必要です。 この章では、拡張メカニズムを決定できます。\-サブクラス化、イベント、仮想メンバーを、コールバック、およびなど —、framework の要件を最も満たすことができます。  
  
 フレームワークの機能拡張を許可するように多くの方法があります。 コストが非常に強力に性能の低いが、低コストの範囲です。 、特定の機能拡張必要条件については、要件を満たしているコストが機能拡張機構を選択してください。 後で、複数の機能拡張を追加する通常できますが、重大な変更を導入することがなく離れた実行しないことができますのことに注意してください。  
  
## このセクションの内容  
 [封印されていないクラス](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [プロテクト メンバー](../../../docs/standard/design-guidelines/protected-members.md)  
 [イベントとコールバック](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [仮想メンバー](../../../docs/standard/design-guidelines/virtual-members.md)  
 [抽象化 \(抽象型とインターフェイス\)](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [抽象化を実装するための基本クラス](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [封印](../../../docs/standard/design-guidelines/sealing.md)  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)