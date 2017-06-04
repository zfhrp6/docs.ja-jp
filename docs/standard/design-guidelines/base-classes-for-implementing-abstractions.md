---
title: "抽象化を実装するための基本クラス | Microsoft Docs"
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
  - "抽象化 [.NET Framework]"
  - "基本クラス、抽象化"
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 抽象化を実装するための基本クラス
厳密に言えば、クラス別のクラスの派生元が、基本クラスになります。 ここでは、ただし、基本クラスは、主に共通の抽象化するため、または一部を再利用するには、他のクラスの既定の実装が継承を目的としたクラス。 基本クラスは、通常、階層のルートに抽象化し、下部にあるいくつかのカスタム実装の間の継承階層の中央に配置できます。  
  
 これらは、抽象化を実装するための実装のヘルパーとして機能します。 たとえば、項目の順序付けられたコレクションのフレームワークの抽象化の 1 つは、 <xref:System.Collections.Generic.IList%601> インターフェイスです。 実装する <xref:System.Collections.Generic.IList%601> は重要でとなるため、フレームワーク、複数の基本クラスなど、 <xref:System.Collections.ObjectModel.Collection%601> と <xref:System.Collections.ObjectModel.KeyedCollection%602>, 、カスタム コレクションを実装するためのヘルパーとして機能します。  
  
 基本クラスは通常ありません自体には、抽象化として処理するために適していますが多すぎるの実装を含んでいる傾向があるためです。 たとえば、 `Collection<T>` 基本クラスには、多数非ジェネリックが実装している事実に関係の実装にはが含まれています。 `IList` \(非ジェネリック コレクションをより適切に統合\) へのインターフェイスとそのフィールドのいずれかでメモリに格納された項目のコレクションであるという事実にします。  
  
 既に説明したようには、基本クラスは抽象化を実装する必要があるユーザーに非常に貴重なヘルプを提供することができます、同時に重大な責任を立つことができます。 継承階層の深さを増やしおよびをので概念的には、フレームワークが複雑になる、サーフェス領域を追加します。 そのため、フレームワークのユーザーに大きな価値を提供する場合にのみ、基本クラスを使用してください。 これらを基本クラスから継承する代わりに、内部の実装への委任で大文字を積極的に検討するフレームワークを実装するときにのみ値を提供する場合に避ける必要があります。  
  
 **✓ を検討してください** 抽象メンバーが含まれている場合でものための基底クラスの抽象です。 これをユーザーに明確に伝達する、クラスが継承するためだけに設計されています。  
  
 **✓ を検討してください** の主要なシナリオの種類から別の名前空間の基本クラスを配置することです。 定義上は、基本クラスは、高度な機能拡張シナリオを想定してし、そのため、大半のユーザーに重要ではありません。  
  
 **X 回避** クラスは、パブリック Api で使用する場合に"Base"サフィックスを持つ基本クラスの名前します。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)   
 [機能拡張のデザイン](../../../docs/standard/design-guidelines/designing-for-extensibility.md)