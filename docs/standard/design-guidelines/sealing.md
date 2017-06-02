---
title: "封印 | Microsoft Docs"
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
  - "機能拡張の制限"
  - "シール クラス [.NET Framework]"
  - "カスタマイズの防止"
  - "シール クラス"
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 封印
オブジェクト指向フレームワークの機能の 1 つは、開発者が拡張および framework デザイナーによって予期しない方法でそれらをカスタマイズできます。 これは、両方の電源および拡張可能なデザインの危険性です。 ご利用のフレームワークを設計するときは、そのため、必要なときは、機能拡張の慎重に設計し、危険な場合は、機能拡張を制限するために非常に重要です。  
  
 機能拡張を防ぐ強力なメカニズムをシールするとします。 クラスまたは個別のメンバーのいずれかを封印することができます。 クラスをシールすると、ユーザーがクラスから継承できなくなります。 メンバーをシールすると、ユーザーが特定のメンバーをオーバーライドできなくなります。  
  
 **X のしないで** これを行うには相応の理由をしなくてもクラスをシールします。  
  
 機能拡張シナリオを想定することはできませんので、クラスをシールすることは相応の理由ではありません。 Framework ユーザーが便利なメンバーを追加するなど、さまざまな明確な理由のクラスから継承したいです。 参照してください [封印されていないクラス](../../../docs/standard/design-guidelines/unsealed-classes.md) 明確な理由の例についてはユーザーが型を継承します。  
  
 クラスをシールする理由を以下に示します。  
  
-   クラスは、静的クラスです。 「[静的クラスのデザイン](../../../docs/standard/design-guidelines/static-class.md)」を参照してください。  
  
-   クラスは、継承されたプロテクト メンバーにセキュリティに影響する機密情報を格納します。  
  
-   クラスは、多くの仮想メンバーを継承し、それらを個別に封印した場合のコストは封印されていないクラスを残すことのメリットを上回ります。  
  
-   クラスは、非常に高速なランタイム ルックアップを必要とする属性です。 Sealed 属性には、封印されていないものよりもわずかに高いパフォーマンス レベルがあります。 「[属性](../../../docs/standard/design-guidelines/属性.md)」を参照してください。  
  
 **X のしないで** sealed 型でプロテクト仮想メンバーを宣言します。  
  
 定義上、シールされた型からは継承できません。 つまり、sealed 型でプロテクト メンバーを呼び出すことができない、sealed 型で仮想メソッドをオーバーライドすることはできません。  
  
 **✓ を検討してください** をオーバーライドするメンバーをシールします。  
  
 仮想メンバーの概要に起因する問題 \(で説明した [仮想メンバー](../../../docs/standard/design-guidelines/virtual-members.md)\) 少しほどには同様に、上書きを適用します。 上書きの封印を開発者から隠ぺい継承階層の時点からこれらの問題です。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)   
 [機能拡張のデザイン](../../../docs/standard/design-guidelines/designing-for-extensibility.md)   
 [封印されていないクラス](../../../docs/standard/design-guidelines/unsealed-classes.md)