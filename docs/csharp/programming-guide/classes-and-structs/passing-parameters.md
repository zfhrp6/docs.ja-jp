---
title: "パラメーターの引き渡し (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
caps.latest.revision: 17
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
ms.openlocfilehash: 4b8c0c7f7b8c3820edbafbe90fb961c12da8fc84
ms.contentlocale: ja-jp
ms.lasthandoff: 09/25/2017

---
# <a name="passing-parameters-c-programming-guide"></a>パラメーターの引き渡し (C# プログラミング ガイド)
C# では、引数を値または参照によってパラメーターに渡すことができます。 参照渡しでは、関数メンバー、メソッド、プロパティ、インデクサー、演算子、およびコンストラクターは、パラメーターの値を変更でき、その変更を呼び出し元の環境で永続化できます。 パラメーターを参照で渡すには、`ref` キーワードまたは `out` キーワードを使用します。 ここでは、説明を簡単にするために、例に `ref` キーワードだけを使用しています。 `ref` と `out` の違いの詳細については、「[ref](../../../csharp/language-reference/keywords/ref.md)」、「[out](../../../csharp/language-reference/keywords/out.md)」、および「[ref と out を使用した配列の引き渡し](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)」を参照してください。  
  
 次の例は、値パラメーターと参照パラメーターの違いを示しています。  
  
 [!code-cs[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 詳細については、次のトピックを参照してください。  
  
-   [値型パラメーターの引き渡し](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [参照型パラメーターの引き渡し](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)

