---
title: "方法: 複数の文字列を連結する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "連結 (文字列を) [C#]"
  - "結合 (文字列を) [C#]"
  - "文字列 [C#], 連結"
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# 方法: 複数の文字列を連結する (C# プログラミング ガイド)
*連結*とは、ある文字列を別の文字列の末尾に追加するプロセスです。  `+` 演算子を使用してリテラル文字列または文字列定数を連結すると、コンパイラにより単一の文字列が作成されます。  連結は実行時には行われません。  ただし、文字列変数は実行時にのみ連結できます。  さまざまな方法のパフォーマンスへの影響を理解する必要があります。  
  
## 使用例  
 ソース コードの読みやすさを改善するために、長いリテラル文字列を短い文字列に分割する方法を次の例に示します。  これらの部分は、コンパイル時に単一の文字列に連結されます。  含まれる文字列の数は、実行時のパフォーマンスには影響しません。  
  
 [!code-cs[csProgGuideStrings#30](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_1.cs)]  
  
## 使用例  
 文字列変数を連結するには、`+` 演算子、`+=` 演算子、<xref:System.String.Concat%2A?displayProperty=fullName> メソッド、<xref:System.String.Format%2A?displayProperty=fullName> メソッド、または <xref:System.Text.StringBuilder.Append%2A?displayProperty=fullName> メソッドを使用します。  `+` 演算子は使いやすく、直感的なコードの作成に役立ちます。  1 つのステートメントで複数の \+ 演算子を使用する場合でも、文字列の内容は一度しかコピーされません。  ループなどでこの操作を複数回繰り返すと、効率が低下する可能性があります。  たとえば次のようなコードがあるとします。  
  
 [!code-cs[csProgGuideStrings#23](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_2.cs)]  
  
> [!NOTE]
>  文字列連結において、C\# コンパイラは null 文字列を空の文字列と同じものとして処理しますが、元の null 文字列値の変換は行いません。  
  
 多数の文字列を連結しない場合 \(たとえば、ループで\)、このコードのパフォーマンスへの影響は通常は大きくありません。  <xref:System.String.Concat%2A?displayProperty=fullName> メソッドと <xref:System.String.Format%2A?displayProperty=fullName> メソッドについても同様です。  
  
 ただし、パフォーマンスを重視する場合、常に <xref:System.Text.StringBuilder> クラスを使用して文字列を連結する必要があります。  次のコード例では、`+` 演算子の連結効果を使用せず、<xref:System.Text.StringBuilder> クラスの <xref:System.Text.StringBuilder.Append%2A> メソッドを使用して文字列を連結します。  
  
 [!code-cs[csProgGuideStrings#22](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_3.cs)]  
  
## 参照  
 <xref:System.String>   
 <xref:System.Text.StringBuilder>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [文字列](../../../csharp/programming-guide/strings/index.md)