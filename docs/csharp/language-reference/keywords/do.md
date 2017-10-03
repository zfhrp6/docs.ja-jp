---
title: "do (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- do_CSharpKeyword
- do
dev_langs:
- CSharp
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 58a9361c440bc1b17c5ab929ff7b45ba71ce50a4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/25/2017

---
# <a name="do-c-reference"></a>do (C# リファレンス)
`do` ステートメントでは、指定された式が `false` になるまで、ステートメントまたはステートメント ブロックが繰り返し実行されます。 ループの本体は、単一のステートメントで構成されている場合を除いて、中かっこ (`{}`) で囲む必要があります。 単一ステートメントで構成されている場合、中かっこはオプションです。  
  
## <a name="example"></a>例  
 次の例では、変数 `x` が 5 未満である限り、`do-while` ループ ステートメントが実行されます。  
  
 [!code-cs[csrefKeywordsIteration#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/do_1.cs)]  
  
 [while](../../../csharp/language-reference/keywords/while.md) ステートメントとは異なり、`do-while` ループは条件式が評価される前に 1 回実行されます。  
  
 `do-while` ブロック内の任意の位置で、[break](../../../csharp/language-reference/keywords/break.md) ステートメントを使用してループを抜けることができます。 [continue](../../../csharp/language-reference/keywords/continue.md) ステートメントを使用すると、`while` 式の評価ステートメントを直接ステップ実行できます。 `while` 式の評価が true の場合、ループの最初のステートメントから実行が続行されます。 式の評価が false の場合、`do-while` ループの後の最初のステートメントから実行が続行されます。  
  
 [goto](../../../csharp/language-reference/keywords/goto.md) ステートメント、[return](../../../csharp/language-reference/keywords/return.md) ステートメント、または [throw](../../../csharp/language-reference/keywords/throw.md) ステートメントを使用して `do-while` ループを抜けることもできます。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [do-while ステートメント (C++)](/cpp/cpp/do-while-statement-cpp)   
 [繰り返しステートメント](../../../csharp/language-reference/keywords/iteration-statements.md)

