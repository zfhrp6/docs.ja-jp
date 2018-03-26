---
title: '方法 : ポインターのインクリメントとデクリメント (C# プログラミング ガイド)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
caps.latest.revision: ''
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2c8efc6d0844d867ad6eebccf3bb22c03e6d5020
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2018
---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a>方法 : ポインターのインクリメントとデクリメント (C# プログラミング ガイド)
pointer-type* 型のポインターの [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) でポインターの位置を変更するには、インクリメント演算子 (`++`) とデクリメント演算子 (`--`) を使用します。 インクリメント式とデクリメント式には、次の書式を使用します。  
  
```  
++p;  
p++;  
--p;  
p--;  
```  
  
 インクリメント演算子とデクリメント演算子は、`void*` 以外のすべての型のポインターに適用できます。  
  
 `pointer-type` 型のポインターにインクリメント演算子を適用すると、ポインター変数に格納されているアドレスに [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) が加算されます。  
  
 `pointer-type` 型のポインターにデクリメント演算子を適用すると、ポインター変数に格納されているアドレスから `sizeof` (`pointer-type`) が減算されます。  
  
 演算がポインターのドメインをオーバーフローしても例外は生成されません。生じる結果は実装によって異なります。  
  
## <a name="example"></a>例  
 この例では、ポインターを `int` のサイズだけインクリメントして、配列をステップ実行します。 ステップごとに、配列要素のアドレスと内容を表示します。  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]  
  
 **Value:0 @ Address:12860272**  
**Value:1 @ Address:12860276**  
**Value:2 @ Address:12860280**  
**Value:3 @ Address:12860284**  
**Value:4 @ Address:12860288**   
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [ポインター式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)  
 [ポインターの操作](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [型](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
