---
title: value (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: c8f808540385552f6222566f23251f6cbd6e86df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="value-c-reference"></a><span data-ttu-id="10e82-102">value (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="10e82-102">value (C# Reference)</span></span>
<span data-ttu-id="10e82-103">コンテキスト キーワード `value` は、set アクセサーの通常のプロパティ宣言で使用します。</span><span class="sxs-lookup"><span data-stu-id="10e82-103">The contextual keyword `value` is used in the set accessor in ordinary property declarations.</span></span> <span data-ttu-id="10e82-104">これは、メソッドの入力パラメーターに似ています。</span><span class="sxs-lookup"><span data-stu-id="10e82-104">It is similar to an input parameter on a method.</span></span> <span data-ttu-id="10e82-105">`value` というキーワードは、クライアント コードでプロパティに割り当てる値を表します。</span><span class="sxs-lookup"><span data-stu-id="10e82-105">The word `value` references the value that client code is attempting to assign to the property.</span></span> <span data-ttu-id="10e82-106">次の例の `MyDerivedClass` には、`Name` というプロパティがあります。このプロパティは `value` パラメーターを使用して、バッキング フィールド `name` に新しい文字列を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="10e82-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="10e82-107">クライアント コードから見ると、演算は簡単な代入演算として記述されます。</span><span class="sxs-lookup"><span data-stu-id="10e82-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/value_1.cs)]  
  
 <span data-ttu-id="10e82-108">`value` の使用に関する詳細については、「[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10e82-108">For more information about the use of `value`, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="10e82-109">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="10e82-109">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="10e82-110">参照</span><span class="sxs-lookup"><span data-stu-id="10e82-110">See Also</span></span>  
 [<span data-ttu-id="10e82-111">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="10e82-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="10e82-112">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="10e82-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="10e82-113">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="10e82-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
