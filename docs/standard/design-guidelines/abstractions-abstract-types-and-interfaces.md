---
title: "抽象化 (抽象型とインターフェイス) | Microsoft Docs"
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
  - "抽象インターフェイス [.NET Framework]"
  - "抽象インターフェイス [.NET Framework]"
  - "抽象型 [.NET Framework]"
  - "抽象型 [.NET Framework]"
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 抽象化 (抽象型とインターフェイス)
抽象化は、コントラクトの説明がコントラクトの完全な実装を提供しない型です。 抽象化は通常インターフェイスまたは抽象クラスとして実装され適切に定義された一連のコントラクトを実装する型の必要なセマンティクスを説明するリファレンス ドキュメントになります。 .NET Framework で最も重要な抽象化のものが <xref:System.IO.Stream>, 、<xref:System.Collections.Generic.IEnumerable%601>, 、および <xref:System.Object>です。  
  
 抽象化のコントラクトをサポートする具象型を実装して、フレームワーク Api がかかります \(で動作\) でこの具象型を使用してフレームワークを拡張することができます、抽象化します。  
  
 時の試練に耐え得ることが有益な意味のある抽象化は、設計することは困難です。 メインの難易度がこれ以上ない数が減少して、メンバーの適切なセットを取得しています。 抽象化のメンバーが多すぎる場合は、難しいかを実装することが不可能になります。 保証された機能が少なすぎますメンバーが存在、多くの興味深いシナリオで役に立たないになります。  
  
 フレームワークで多くの抽象化も低下するために、フレームワークの使いやすさです。 非常に具体的な実装と抽象化で動作している Api の大きい画像に組み込む方法を理解していなくても抽象化を理解しにくいは多くの場合です。 また、抽象化とそのメンバーの名前は必ずしも抽象を多くの場合に暗号のような印象は交え、その使用状況を理解していなくても。  
  
 ただし、抽象化は、その他の拡張メカニズムは、多くの場合、一致しないする非常に強力な機能拡張を提供します。 多くのアーキテクチャ パターン、プラグインの中核は制御の反転 \(IoC\)、パイプライン、やなどです。 フレームワークの容易性を高めることが重要です。 適切な抽象化を使用すれば、単体テストするために大量の依存関係を消去できます。 要するに、抽象化は最新のオブジェクト指向フレームワークのいる豊富な機能を担当します。  
  
 **X のしないで** いくつかの具体的な実装と抽象化を使用する Api を開発することにより、テストしない抽象化を提供します。  
  
 **✓ は** 抽象化を設計するときは、抽象クラスとインターフェイス間慎重に選択します。  
  
 **✓ を検討してください** の抽象化の具体的な実装のテストの参照を提供します。 このようなテストは、実装が正しく、コントラクトを実装するかどうかをテストするユーザーを許可する必要があります。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)   
 [機能拡張のデザイン](../../../docs/standard/design-guidelines/designing-for-extensibility.md)