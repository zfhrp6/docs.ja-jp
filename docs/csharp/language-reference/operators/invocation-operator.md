---
title: "() 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ()_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 159a663ca151a276b3b56f13cf8e997069210d67
ms.lasthandoff: 03/13/2017

---
# <a name="-operator-c-reference"></a>() 演算子 (C# リファレンス)
かっこは式内での演算の順序を指定することに加え、以下のタスクを実行するために使用されます。  
  
1.  キャストまたは型変換を指定する。  
  
     [!code-cs[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]  
  
2.  メソッドまたはデリゲートを呼び出す。  
  
     [!code-cs[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]  
  
## <a name="remarks"></a>コメント  
 キャストによってある型から別の型への変換演算子が明示的に呼び出されます。その変換演算子が定義されていない場合、キャストは失敗します。 変換演算子を定義するには、「[explicit](../../../csharp/language-reference/keywords/explicit.md)」および「[implicit](../../../csharp/language-reference/keywords/implicit.md)」を参照してください。  
  
 `()` 演算子はオーバーロードできません。  
  
 詳細については、「[キャストと型変換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)」を参照してください。  
  
 キャスト式では、構文があいまいになる可能性があります。 たとえば式 `(x)–y` は、キャスト式 (型 x への –y のキャスト) とも、かっこで囲まれた式と組み合わせた x – y の値を計算する加法式とも解釈できます。  
  
 メソッド呼び出しの詳細については、「[メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)」を参照してください。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# 演算子](../../../csharp/language-reference/operators/index.md)
