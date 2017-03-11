---
title: "DirectCast Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.directCast"
  - "directCast"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DirectCast keyword"
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 23
---
# DirectCast Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

継承または実装に基づく型変換処理を実行します。  
  
## 解説  
 `DirectCast` は Visual Basic のランタイム ヘルパー ルーチンを変換に使用しません。このため、オブジェクト型 \(`Object`\) との間で変換を行う場合に、`CType` よりもいくらかパフォーマンスがよくなります。  
  
 キーワード `DirectCast` は、[CType 関数](../../../visual-basic/language-reference/functions/ctype-function.md) およびキーワード [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) と似た方法で使用します。  1 つ目の引数に式を指定し、2 つ目の引数に変換後の型を指定します。  `DirectCast` の場合、この 2 つの引数のデータ型の間に、継承または実装の関係があることが必要です。  つまり、一方の型が他方を継承しているか、実装している必要があります。  
  
## エラー  
 `DirectCast` は、継承または実装の関係が存在しないことを検出すると、コンパイル エラーを生成します。  コンパイラ エラーが発生しなくても、変換が成功したとは限りません。  実行する変換が縮小変換である場合、実行時に失敗する可能性があります。  このとき、ランタイムによって <xref:System.InvalidCastException> エラーがスローされます。  
  
## 型変換のキーワード  
 型変換のキーワードを比較したものを次に示します。  
  
|||||  
|-|-|-|-|  
|Keyword|データ型|引数の関係|実行時のエラー|  
|[CType 関数](../../../visual-basic/language-reference/functions/ctype-function.md)|Any 型|2 つのデータ型の間で拡大変換または縮小変換を定義する必要があります。|<xref:System.InvalidCastException> をスロー|  
|`DirectCast`|Any 型|一方の型が他方を継承または実装していることが必要|<xref:System.InvalidCastException> をスロー|  
|[TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md)|参照型のみ|一方の型が他方を継承または実装していることが必要|[Nothing](../../../visual-basic/language-reference/nothing.md) を返す|  
  
## 使用例  
 `DirectCast` の 2 つの使用例を次に示します。1 つは実行時に失敗し、もう 1 つは成功します。  
  
 [!code-vb[VbVbalrKeywords#1](../../../visual-basic/language-reference/codesnippet/visualbasic/directcast-operator_1.vb)]  
  
 この例では、`q` のランタイム型は倍精度浮動小数点数型 \(`Double`\) です。  `Double` は `Integer` に変換できるので、`CType` は成功します。  しかし、最初の `DirectCast` は実行時に失敗します。`Double` のランタイム型は `Integer` に変換可能ですが、継承の関係にはないからです。  2 番目の `DirectCast` は、<xref:System.Windows.Forms.Form> 型から <xref:System.Windows.Forms.Control> 型への変換です。<xref:System.Windows.Forms.Form> は <xref:System.Windows.Forms.Control> を継承しているので成功します。  
  
## 参照  
 <xref:System.Convert.ChangeType%2A?displayProperty=fullName>   
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)