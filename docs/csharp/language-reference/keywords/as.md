---
title: as (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
ms.openlocfilehash: 092c30a858df7baeb35bdf28bae53802fb0916d4
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
---
# <a name="as-c-reference"></a>as (C# リファレンス)
`as` 演算子を使用して、互換性のある参照型または [null 許容型](../../../csharp/programming-guide/nullable-types/index.md)間で特定の型変換を実行できます。 次のコードは一例を示しています。  
  
 [!code-csharp[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_1.cs)]  
  
## <a name="remarks"></a>コメント  
 `as` 演算子はキャスト演算と似ています。 ただし、変換が可能でない場合、`as` は例外を発生させる代わりに `null` を返します。 次に例を示します。  
  
```csharp  
expression as type  
```  
  
 このコードは次の式と同等ですが、`expression` 変数は 1 回しか評価されません。  
  
```csharp  
expression is type ? (type)expression : (type)null  
```  
  
 なお、`as` 演算子は、参照変換、null 許容変換またはボックス変換のみ実行します。 `as` 演算子は、ユーザー定義変換など、他の変換を実行できないため、ユーザー定義変換を実行するには、代わりにキャスト式を使用します。  
  
## <a name="example"></a>例  
 [!code-csharp[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_2.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [is](../../../csharp/language-reference/keywords/is.md)  
 [?: 演算子](../../../csharp/language-reference/operators/conditional-operator.md)  
 [演算子のキーワード](../../../csharp/language-reference/keywords/operator-keywords.md)
