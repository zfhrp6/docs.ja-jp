---
title: "方法 : foreach を使用してコレクション クラスにアクセスする (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "コレクション クラス [C#], foreach ステートメント"
ms.assetid: a6b9cf5c-6c8d-4223-b12c-288949434493
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法 : foreach を使用してコレクション クラスにアクセスする (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

次のコード例では、[foreach](../../../csharp/language-reference/keywords/foreach-in.md) と共に使用できる非ジェネリック コレクション クラスの記述方法を示します。  この例では、文字列のトークナイザ クラスを定義しています。  
  
> [!NOTE]
>  この例では、ジェネリック コレクション クラスを使用できない場合にのみ推奨される方法を示します。  <xref:System.Collections.Generic.IEnumerable%601> をサポートするタイプ セーフのジェネリック コレクション クラスを実装する方法の例については、「[反復子](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
 この例の次のコード セグメントでは、区切り記号として ' ' と '\-' を使用して "This is a sample sentence." という文をトークンに分割する `Tokens` クラスを使用しています。  コードでは、これらのトークンを表示するために `foreach` ステートメントを使用しています。  
  
 [!code-cs[csProgGuideCollections#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_1.cs)]  
  
## 使用例  
 内部では、`Tokens` クラスは配列を使用してトークンを格納します。  配列で <xref:System.Collections.IEnumerator> と <xref:System.Collections.IEnumerable> を実装しているため、このコード例では `Tokens` クラスでこれらを定義するのではなく、配列の列挙型メソッド \(<xref:System.Collections.IEnumerable.GetEnumerator%2A>、<xref:System.Collections.IEnumerator.MoveNext%2A>、<xref:System.Collections.IEnumerator.Reset%2A>、および <xref:System.Collections.IEnumerator.Current%2A>\) を使用することもできました。  この例にメソッド定義が含まれているのは、メソッドを定義する方法と各メソッドの動作を明確にするためです。  
  
 [!code-cs[csProgGuideCollections#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_2.cs)]  
  
 C\# では、`foreach` と互換性を保つために、コレクション クラスで <xref:System.Collections.IEnumerable> と <xref:System.Collections.IEnumerator> を実装する必要はありません。  必須の <xref:System.Collections.IEnumerable.GetEnumerator%2A>、<xref:System.Collections.IEnumerator.MoveNext%2A>、<xref:System.Collections.IEnumerator.Reset%2A>、および <xref:System.Collections.IEnumerator.Current%2A> の各メンバーがクラスに含まれていれば、クラスで `foreach` を使用できます。  インターフェイスを省略すると、`Current` の戻り値の型を <xref:System.Object> よりも明確に定義できるという利点があります。  これによりタイプ セーフになります。  
  
 たとえば、前の例の次の行を変更します。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 `Current` によって文字列が返されるため、次のコードに示すように、コンパイラは `foreach` ステートメントで互換性のない型が使用されていることを検出できます。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 <xref:System.Collections.IEnumerable> と <xref:System.Collections.IEnumerator> を省略すると、コレクション クラスを他の共通言語ランタイム言語の `foreach` ステートメント \(または同等のステートメント\) と相互運用できなくなるので注意が必要です。  
  
## 参照  
 <xref:System.Collections.Generic>   
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [配列](../../../csharp/programming-guide/arrays/index.md)   
 [コレクション](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)