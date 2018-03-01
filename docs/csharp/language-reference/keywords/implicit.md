---
title: "implicit (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- implicit
- implicit_CSharpKeyword
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c893c7a9afbdc6f715010d537e9ccaf66c5785c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-c-reference"></a>implicit (C# リファレンス)
`implicit` キーワードを使用して、暗黙のユーザー定義型変換演算子を宣言します。 変換を実行してもデータ損失が発生しないことが保証されている場合に、ユーザー定義型とその他の型との間の暗黙の変換を有効にするために使用します。  
  
## <a name="example"></a>例  
 [!code-csharp[csrefKeywordsConversion#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicit_1.cs)]  
  
 暗黙の変換では不要なキャストを省略できるため、ソース コードが読みやすくなります。 ただし、暗黙の変換では、一方の型からもう一方の型に明示的にキャストする必要がないため、予期しない結果が生じないように注意する必要があります。 プログラマーが意識しなくても安全に使用できるように、通常、暗黙の変換演算子は、例外をスローしたり情報を失ったりしてはなりません。 このような条件を満たすことができない変換演算子は、`explicit` でマークする必要があります。 詳細については、「[変換演算子の使用](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)」を参照してください。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [explicit](../../../csharp/language-reference/keywords/explicit.md)  
 [演算子 (C# リファレンス)](../../../csharp/language-reference/keywords/operator.md)  
 [方法: 構造体間にユーザー定義の変換を実装する](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
