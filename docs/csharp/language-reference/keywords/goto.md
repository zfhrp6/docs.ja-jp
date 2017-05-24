---
title: "goto (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- goto_CSharpKeyword
- goto
dev_langs:
- CSharp
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
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
ms.openlocfilehash: 700376096d969052a9f4633f565f9d9fd4dfec46
ms.contentlocale: ja-jp
ms.lasthandoff: 05/22/2017

---
# <a name="goto-c-reference"></a>goto (C# リファレンス)
`goto` ステートメントは、プログラムの制御をラベル付きステートメントに直接移します。  
  
 `goto` の一般的な用途は、特定の switch-case ラベルまたは `switch` ステートメントの既定のラベルに、制御を移動することです。  
  
 `goto` ステートメントは、深い入れ子のループから抜ける場合にも便利です。  
  
## <a name="example"></a>例  
 次の例では、[switch](../../../csharp/language-reference/keywords/switch.md) ステートメントでの `goto` の使い方を示します。  
  
 [!code-cs[csrefKeywordsJump#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_1.cs)]  
  
## <a name="example"></a>例  
 次の例では、`goto` を使って入れ子になったループから抜け出す方法を示します。  
  
 [!code-cs[csrefKeywordsJump#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_2.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [GoTo ステートメント](https://docs.microsoft.com/cpp/cpp/goto-statement-cpp)   
 [ジャンプ ステートメント](../../../csharp/language-reference/keywords/jump-statements.md)
