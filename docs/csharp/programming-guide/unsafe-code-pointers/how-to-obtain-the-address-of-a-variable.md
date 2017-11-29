---
title: "方法: 変数のアドレスを取得する (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d0969f7e62864c682660f08cd4198aa4032e0e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a>方法: 変数のアドレスを取得する (C# プログラミング ガイド)
固定変数に評価される単項式のアドレスを取得するには、address-of 演算子を使用します。  
  
```  
int number;  
int* p = &number; //address-of operator &  
```  
  
 address-of 演算子は、変数にのみ適用できます。 変数が移動可能な変数である場合、[fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)を使用して変数のアドレスを取得する前に、一時的に変数を固定できます。  
  
 ユーザーは変数が初期化されていることを確認する必要があります。 変数が初期化されていない場合、コンパイラはエラー メッセージを発行しません。  
  
 定数または値のアドレスを取得できません。  
  
## <a name="example"></a>例  
 この例では、`int`、`p` へのポインターを宣言し、整数変数 `number` のアドレスを代入します。 変数 `number` は *p への代入の結果として初期化されます。 この代入ステートメントをコメントにする場合は、変数 `number` の初期化が削除されますが、コンパイル時のエラーは発生しません。 ポインターに格納されているアドレスを取得して表示するために、[メンバー アクセス](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md)演算子 `->` が使用されていることに注目してください。  
  
 [!code-csharp[csProgGuidePointers#7](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#8](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_2.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [ポインター式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [型](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
