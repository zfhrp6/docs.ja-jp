---
title: "while (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- while_CSharpKeyword
- while
dev_langs:
- CSharp
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 744980f2dd55806062901d874a3137f5936e0888
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="while-c-reference"></a>while (C# リファレンス)
`while` ステートメントでは、指定された式が `false` と評価されるまで、ステートメントまたはステートメント ブロックが実行されます。  
  
## <a name="example"></a>例  
 [!code-cs[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_1.cs)]  
  
## <a name="example"></a>例  
 [!code-cs[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_2.cs)]  
  
## <a name="example"></a>例  
 `while` 式が評価されてからループが実行されるため、`while` ループは 0 回以上実行されます。 [do](../../../csharp/language-reference/keywords/do.md) ループは、これとは異なり、1 回以上実行されます。  
  
 `while` ループは、[break](../../../csharp/language-reference/keywords/break.md)、[goto](../../../csharp/language-reference/keywords/goto.md)、[return](../../../csharp/language-reference/keywords/return.md)、または [throw](../../../csharp/language-reference/keywords/throw.md) ステートメントがループの外部に制御を移動すると終了できます。 ループを終了せずに制御を次の繰り返しに渡すには、[continue](../../../csharp/language-reference/keywords/continue.md) ステートメントを使用します。 上記の 3 つの例での出力は、`int n` がインクリメントされる位置によって異なる点に注意してください。 次の例では出力は生成されません。  
  
 [!code-cs[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_3.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [while ステートメント (C++)](https://docs.microsoft.com/cpp/cpp/while-statement-cpp)   
 [繰り返しステートメント](../../../csharp/language-reference/keywords/iteration-statements.md)
