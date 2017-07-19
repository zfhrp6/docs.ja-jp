---
title: "構造体のデザイン | Microsoft Docs"
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
  - "クラス ライブラリ デザインのガイドライン [.NET Framework] 構造体"
  - "構造体の割り当てを解除"
  - "構造体の割り当てください。"
  - "値型、構造体"
  - "構造の設計"
  - "型のデザインのガイドライン、構造体"
  - "構造体 [.NET Framework] のデザイン ガイドライン"
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 構造体のデザイン
ほとんどの場合、汎用的な値の型は構造体、c\# のキーワードと呼ばれます。 このセクションでは、一般的な構造体のデザインのガイドラインを示します。  
  
 **X のしないで** 構造体の既定のコンス トラクターを提供します。  
  
 このガイドラインに従うには、配列の項目ごとに、コンス トラクターを実行することがなく作成する構造体の配列が使用できます。 C\# で許可しないことを既定のコンス トラクターを持つ構造体に注意してください。  
  
 **X のしないで** 変更可能な値の型を定義します。  
  
 変更可能な値の型には、いくつかの問題があります。 たとえば、プロパティ get アクセス操作子が値型を返すときに、呼び出し元は、コピーを受け取ります。 コピーが暗黙的に作成されるため、開発者は、コピー、および元の値ではなくを変化することに注意してください限りません。 また、一部の言語 \(動的言語、特に\) では、できるコピーによって、ローカル変数を逆参照されたときにも、ために、変更可能な値の型を使用して問題があります。  
  
 **✓ は** すべてのインスタンス データの状態が 0 に設定されているように、false の場合、または null \(該当する場合\) は無効です。  
  
 無効なインスタンスの偶発的な作成を禁止これは、構造体の配列が作成されるときです。  
  
 **✓ は** 実装 <xref:System.IEquatable%601> を値の型。  
  
 <xref:System.Object.Equals%2A?displayProperty=fullName> 値型のメソッドとボックス化、および既定の実装はリフレクションを使用しているため、非常に効率です。<xref:System.IEquatable%601.Equals%2A> 多くのパフォーマンスを向上させることができ、できる機構を実装するため、ボックス化は発生しません。  
  
 **X のしないで** 明示的に延長 <xref:System.ValueType>します。 実際には、ほとんどの言語は、これを防ぐ。  
  
 通常、構造体では、非常に役に立ちますが、小規模で、1 つ、変更できないの値がないボックス化する多くの場合にのみ使用する必要があります。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [型デザインのガイドライン](../../../docs/standard/design-guidelines/type.md)   
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)   
 [クラスまたは構造体の選択](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)