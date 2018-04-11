---
title: goto (C# リファレンス)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aa12a7547cfcd4a2076b5b0a308139f8a823f482
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="goto-c-reference"></a>goto (C# リファレンス)
`goto` ステートメントは、プログラムの制御をラベル付きステートメントに直接移します。  
  
 `goto` の一般的な用途は、特定の switch-case ラベルまたは `switch` ステートメントの既定のラベルに、制御を移動することです。  
  
 `goto` ステートメントは、深い入れ子のループから抜ける場合にも便利です。  
  
## <a name="example"></a>例  
 次の例では、[switch](../../../csharp/language-reference/keywords/switch.md) ステートメントでの `goto` の使い方を示します。  
  
 [!code-csharp[csrefKeywordsJump#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_1.cs)]  
  
## <a name="example"></a>例  
 次の例では、`goto` を使って入れ子になったループから抜け出す方法を示します。  
  
 [!code-csharp[csrefKeywordsJump#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_2.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [goto ステートメント](/cpp/cpp/goto-statement-cpp)  
 [ジャンプ ステートメント](../../../csharp/language-reference/keywords/jump-statements.md)
