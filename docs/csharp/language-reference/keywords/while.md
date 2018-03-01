---
title: "while (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 420b409689d877c3e1ac744e8d7a65500cf8f964
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="while-c-reference"></a>while (C# リファレンス)
`while` ステートメントでは、指定された式が `false` と評価されるまで、ステートメントまたはステートメント ブロックが実行されます。  
  
## <a name="example"></a>例  
 [!code-csharp[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_1.cs)]  
  
## <a name="example"></a>例  
 [!code-csharp[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_2.cs)]  
  
## <a name="example"></a>例  
 `while` 式が評価されてからループが実行されるため、`while` ループは 0 回以上実行されます。 [do](../../../csharp/language-reference/keywords/do.md) ループは、これとは異なり、1 回以上実行されます。  
  
 `while` ループは、[break](../../../csharp/language-reference/keywords/break.md)、[goto](../../../csharp/language-reference/keywords/goto.md)、[return](../../../csharp/language-reference/keywords/return.md)、または [throw](../../../csharp/language-reference/keywords/throw.md) ステートメントがループの外部に制御を移動すると終了できます。 ループを終了せずに制御を次の繰り返しに渡すには、[continue](../../../csharp/language-reference/keywords/continue.md) ステートメントを使用します。 上記の 3 つの例での出力は、`int n` がインクリメントされる位置によって異なる点に注意してください。 次の例では出力は生成されません。  
  
 [!code-csharp[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_3.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [while ステートメント (C++)](/cpp/cpp/while-statement-cpp)  
 [繰り返しステートメント](../../../csharp/language-reference/keywords/iteration-statements.md)
