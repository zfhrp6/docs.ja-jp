---
title: new 制約 (C# リファレンス)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8557e056a664fd470b1f185b619d81235c8fcba7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="db187-102">new 制約 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="db187-102">new Constraint (C# Reference)</span></span>
<span data-ttu-id="db187-103">`new` 制約は、ジェネリック クラス宣言内のすべての型引数に、パブリックでパラメーターなしのコンストラクターが必要であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="db187-103">The `new` constraint specifies that any type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="db187-104">new 制約を使用する場合、型を抽象型にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="db187-104">To use the new constraint, the type cannot be abstract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db187-105">例</span><span class="sxs-lookup"><span data-stu-id="db187-105">Example</span></span>  
 <span data-ttu-id="db187-106">`new` 制約は、次の例に示すように、ジェネリック クラスである型の新しいインスタンスを作成する場合に型パラメーターに適用されます。</span><span class="sxs-lookup"><span data-stu-id="db187-106">Apply the `new` constraint to a type parameter when your generic class creates new instances of the type, as shown in the following example:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="db187-107">例</span><span class="sxs-lookup"><span data-stu-id="db187-107">Example</span></span>  
 <span data-ttu-id="db187-108">`new()` 制約を別の制約と併用する場合、この制約を最後に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="db187-108">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_2.cs)]  
  
 <span data-ttu-id="db187-109">詳細については、「[型パラメーターの制約](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db187-109">For more information, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="db187-110">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="db187-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="db187-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="db187-111">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="db187-112">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="db187-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="db187-113">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="db187-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="db187-114">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="db187-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="db187-115">演算子のキーワード</span><span class="sxs-lookup"><span data-stu-id="db187-115">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="db187-116">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="db187-116">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
