---
title: "TryCast Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.trycast"
  - "trycast"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "TryCast keyword"
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# TryCast Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

例外をスローしない型変換演算を開始します。  
  
## 解説  
 変換が失敗した場合、`CType` および `DirectCast` の両方から <xref:System.InvalidCastException> エラーが発生します。  これは、アプリケーションのパフォーマンスに悪影響を与える可能性があります。  `TryCast` は、例外を処理するのではなく、返された値が `Nothing` かどうかをテストするだけで済むように [Nothing](../../../visual-basic/language-reference/nothing.md) を返します。  
  
 `TryCast` キーワードは、[CType 関数](../../../visual-basic/language-reference/functions/ctype-function.md) や [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) キーワードと同じように使用します。  1 つ目の引数に式を指定し、2 つ目の引数に変換後の型を指定します。  `TryCast` は、クラスやインターフェイスなどの参照型のみを扱います。  2 つの型の間には、継承または実装の関係が必要です。  つまり、一方の型が他方を継承しているか、実装している必要があります。  
  
## エラー  
 継承も実装もないことを確認した場合、`TryCast` はコンパイラ エラーを生成します。  コンパイラ エラーが発生しなくても、変換が成功したとは限りません。  実行する変換が縮小変換である場合、実行時に失敗する可能性があります。  この場合、`TryCast` は [Nothing](../../../visual-basic/language-reference/nothing.md) を返します。  
  
## 型変換のキーワード  
 型変換のキーワードを比較したものを次に示します。  
  
|||||  
|-|-|-|-|  
|Keyword|データ型|引数の関係|実行時のエラー|  
|[CType 関数](../../../visual-basic/language-reference/functions/ctype-function.md)|Any 型|2 つのデータ型の間で拡大変換または縮小変換を定義する必要があります。|<xref:System.InvalidCastException> をスロー|  
|[DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md)|Any 型|一方の型が他方を継承または実装していることが必要|<xref:System.InvalidCastException> をスロー|  
|`TryCast`|参照型のみ|一方の型が他方を継承または実装していることが必要|[Nothing](../../../visual-basic/language-reference/nothing.md) を返す|  
  
## 使用例  
 次の例は、`TryCast` を使用する方法を示しています。  
  
 [!code-vb[VbVbalrKeywords#6](../../../visual-basic/language-reference/codesnippet/visualbasic/trycast-operator_1.vb)]  
  
## 参照  
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)