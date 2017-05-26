---
title: "as (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- as_CSharpKeyword
- as
dev_langs:
- CSharp
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
caps.latest.revision: 24
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6c284f288df11e2ac32b7c27f914e3f699bd78f0
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="as-c-reference"></a>as (C# リファレンス)
`as` 演算子を使用して、互換性のある参照型または [null 許容型](../../../csharp/programming-guide/nullable-types/index.md)間で特定の型変換を実行できます。 次のコードは一例を示しています。  
  
 [!code-cs[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_1.cs)]  
  
## <a name="remarks"></a>コメント  
 `as` 演算子はキャスト演算と似ています。 ただし、変換が可能でない場合、`as` は例外を発生させる代わりに `null` を返します。 次に例を示します。  
  
```  
expression as type  
```  
  
 このコードは次の式と同等ですが、`expression` 変数は 1 回しか評価されません。  
  
```  
expression is type ? (type)expression : (type)null  
```  
  
 なお、`as` 演算子は、参照変換、null 許容変換またはボックス変換のみ実行します。 `as` 演算子は、ユーザー定義変換など、他の変換を実行できないため、ユーザー定義変換を実行するには、代わりにキャスト式を使用します。  
  
## <a name="example"></a>例  
 [!code-cs[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_2.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [is](../../../csharp/language-reference/keywords/is.md)   
 [?: 演算子](../../../csharp/language-reference/operators/conditional-operator.md)   
 [演算子のキーワード](../../../csharp/language-reference/keywords/operator-keywords.md)
