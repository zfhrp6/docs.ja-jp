---
title: "ジェネリック インターフェイス (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 言語, ジェネリック インターフェイス"
  - "ジェネリック [C#], インターフェイス"
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
caps.latest.revision: 28
caps.handback.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# ジェネリック インターフェイス (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

多くの場合、ジェネリック コレクション クラス、またはコレクション内の項目を表すジェネリック クラスにインターフェイスを定義すると便利です。  ジェネリック クラスでは、値型に対するボックス化およびボックス化解除の操作を回避するために、<xref:System.IComparable> よりも <xref:System.IComparable%601> などのジェネリック インターフェイスを使用することをお勧めします。  .NET Framework クラス ライブラリでは、<xref:System.Collections.Generic> 名前空間のコレクション クラスと共に使用する、いくつかのジェネリック インターフェイスが定義されています。  
  
 型パラメーターに関する制約としてインターフェイスを指定すると、そのインターフェイスを実装する型のみを使用できます。  次のコード例で、`GenericList<T>` クラスから派生する `SortedList<T>` クラスを示します。  詳細については、「[ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)」を参照してください。  `SortedList<T>` は、制約 `where T : IComparable<T>` を追加します。  これによって、`SortedList<T>` の `BubbleSort` メソッドが、リスト要素でジェネリックの <xref:System.IComparable%601.CompareTo%2A> メソッドを使用できるようになります。  この例では、リスト要素は単純なクラス `Person` であり、`IComparable<Person>` を実装しています。  
  
 [!code-cs[csProgGuideGenerics#29](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_1.cs)]  
  
 単一の型に対する制約として、次のように複数のインターフェイスを指定できます。  
  
 [!code-cs[csProgGuideGenerics#30](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_2.cs)]  
  
 1 つのインターフェイスで、次のように複数の型パラメーターを定義できます。  
  
 [!code-cs[csProgGuideGenerics#31](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_3.cs)]  
  
 クラスに適用される継承の規則が、インターフェイスにも適用されます。  
  
 [!code-cs[csProgGuideGenerics#32](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_4.cs)]  
  
 ジェネリック インターフェイスが非バリアントの場合 \(つまり、型パラメーターを戻り値としてのみ使用する場合\)、そのジェネリック インターフェイスは、非ジェネリック インターフェイスから継承できます。  .NET Framework クラス ライブラリでは、<xref:System.Collections.Generic.IEnumerable%601> は <xref:System.Collections.IEnumerable> から継承されます。<xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> の戻り値と <xref:System.Collections.Generic.IEnumerator%601.Current%2A> プロパティの getter で、<xref:System.Collections.Generic.IEnumerable%601> のみが `T` を使用するためです。  
  
 具象クラスでは、次のように閉じた構造のインターフェイスを実装できます。  
  
 [!code-cs[csProgGuideGenerics#33](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_5.cs)]  
  
 ジェネリック クラスでは、インターフェイスで必要なすべての引数がクラスのパラメーター リストに指定されている場合、次のように、ジェネリック インターフェイスまたは閉じた構造のインターフェイスを実装できます。  
  
 [!code-cs[csProgGuideGenerics#34](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_6.cs)]  
  
 メソッドのオーバーロードを管理する規則は、ジェネリック クラス、ジェネリック構造体、ジェネリック インターフェイスのそれぞれのメソッドに対して同じです。  詳細については、「[ジェネリック メソッド](../../../csharp/programming-guide/generics/generic-methods.md)」を参照してください。  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [interface](../../../csharp/language-reference/keywords/interface.md)   
 [ジェネリック](../Topic/Generics%20in%20the%20.NET%20Framework.md)