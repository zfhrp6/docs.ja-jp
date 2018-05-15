---
title: return (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 29d2b8e28ae6240b9d06b82695efe1736404c5cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="return-c-reference"></a>return (C# リファレンス)
`return` ステートメントは、メソッドの実行を終了し、呼び出し側のメソッドに制御を戻します。 省略可能な値を返すこともできます。 メソッドが `void` 型の場合、`return` ステートメントは省略できます。  
  
 return ステートメントが `try` ブロック内にある場合は、制御が呼び出し側のメソッドに返される前に、`finally` ブロック (存在する場合) が実行されます。  
  
## <a name="example"></a>例  
 次の例では、メソッド `CalculateArea()` がローカル変数 `area` を [double](../../../csharp/language-reference/keywords/double.md) 値として返します。  
  
 [!code-csharp[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/return_1.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [return ステートメント](/cpp/cpp/return-statement-cpp)  
 [ジャンプ ステートメント](../../../csharp/language-reference/keywords/jump-statements.md)
