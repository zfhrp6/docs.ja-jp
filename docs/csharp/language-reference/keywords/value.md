---
title: "value (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- value_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
caps.latest.revision: 14
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
ms.openlocfilehash: 012cf622091687996fec477a8b5b821b190bbc29
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="value-c-reference"></a><span data-ttu-id="ccd0a-102">value (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="ccd0a-102">value (C# Reference)</span></span>
<span data-ttu-id="ccd0a-103">コンテキスト キーワード `value` は、set アクセサーの通常のプロパティ宣言で使用します。</span><span class="sxs-lookup"><span data-stu-id="ccd0a-103">The contextual keyword `value` is used in the set accessor in ordinary property declarations.</span></span> <span data-ttu-id="ccd0a-104">これは、メソッドの入力パラメーターに似ています。</span><span class="sxs-lookup"><span data-stu-id="ccd0a-104">It is similar to an input parameter on a method.</span></span> <span data-ttu-id="ccd0a-105">`value` というキーワードは、クライアント コードでプロパティに割り当てる値を表します。</span><span class="sxs-lookup"><span data-stu-id="ccd0a-105">The word `value` references the value that client code is attempting to assign to the property.</span></span> <span data-ttu-id="ccd0a-106">次の例の `MyDerivedClass` には、`Name` というプロパティがあります。このプロパティは `value` パラメーターを使用して、バッキング フィールド `name` に新しい文字列を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="ccd0a-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="ccd0a-107">クライアント コードから見ると、演算は簡単な代入演算として記述されます。</span><span class="sxs-lookup"><span data-stu-id="ccd0a-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>  
  
 <span data-ttu-id="ccd0a-108">[!code-cs[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/value_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ccd0a-108">[!code-cs[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/value_1.cs)]</span></span>  
  
 <span data-ttu-id="ccd0a-109">`value` の使用に関する詳細については、「[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ccd0a-109">For more information about the use of `value`, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="ccd0a-110">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="ccd0a-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ccd0a-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="ccd0a-111">See Also</span></span>  
 <span data-ttu-id="ccd0a-112">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="ccd0a-112">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="ccd0a-113">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ccd0a-113">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="ccd0a-114">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="ccd0a-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)

