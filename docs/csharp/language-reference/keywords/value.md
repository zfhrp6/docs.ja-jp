---
title: value (C# リファレンス)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2501bc8964ed76534dba6c7cc519e095c57cb898
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="value-c-reference"></a><span data-ttu-id="26559-102">value (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="26559-102">value (C# Reference)</span></span>
<span data-ttu-id="26559-103">コンテキスト キーワード `value` は、set アクセサーの通常のプロパティ宣言で使用します。</span><span class="sxs-lookup"><span data-stu-id="26559-103">The contextual keyword `value` is used in the set accessor in ordinary property declarations.</span></span> <span data-ttu-id="26559-104">これは、メソッドの入力パラメーターに似ています。</span><span class="sxs-lookup"><span data-stu-id="26559-104">It is similar to an input parameter on a method.</span></span> <span data-ttu-id="26559-105">`value` というキーワードは、クライアント コードでプロパティに割り当てる値を表します。</span><span class="sxs-lookup"><span data-stu-id="26559-105">The word `value` references the value that client code is attempting to assign to the property.</span></span> <span data-ttu-id="26559-106">次の例の `MyDerivedClass` には、`Name` というプロパティがあります。このプロパティは `value` パラメーターを使用して、バッキング フィールド `name` に新しい文字列を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="26559-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="26559-107">クライアント コードから見ると、演算は簡単な代入演算として記述されます。</span><span class="sxs-lookup"><span data-stu-id="26559-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/value_1.cs)]  
  
 <span data-ttu-id="26559-108">`value` の使用に関する詳細については、「[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26559-108">For more information about the use of `value`, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="26559-109">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="26559-109">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="26559-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="26559-110">See Also</span></span>  
 [<span data-ttu-id="26559-111">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="26559-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="26559-112">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="26559-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="26559-113">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="26559-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
