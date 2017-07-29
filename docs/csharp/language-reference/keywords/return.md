---
title: "return (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- return_CSharpKeyword
- return
dev_langs:
- CSharp
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
caps.latest.revision: 18
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
ms.openlocfilehash: 596375a1cba8f5ecbad636a6829c1a0599f8c0f4
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="return-c-reference"></a>return (C# リファレンス)
`return` ステートメントは、メソッドの実行を終了し、呼び出し側のメソッドに制御を戻します。 省略可能な値を返すこともできます。 メソッドが `void` 型の場合、`return` ステートメントは省略できます。  
  
 return ステートメントが `try` ブロック内にある場合は、制御が呼び出し側のメソッドに返される前に、`finally` ブロック (存在する場合) が実行されます。  
  
## <a name="example"></a>例  
 次の例では、メソッド `A()` が変数 `Area` を [double](../../../csharp/language-reference/keywords/double.md) 値として返します。  
  
 [!code-cs[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/return_1.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [return ステートメント](/cpp/cpp/return-statement-cpp)   
 [ジャンプ ステートメント](../../../csharp/language-reference/keywords/jump-statements.md)

