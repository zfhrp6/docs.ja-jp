---
title: new 制約 (C# リファレンス)
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 77c955102ba9cede831c85838a6a7e57025ad35b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="18ab8-102">new 制約 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="18ab8-102">new Constraint (C# Reference)</span></span>
<span data-ttu-id="18ab8-103">`new` 制約は、ジェネリック クラス宣言内のすべての型引数に、パブリックでパラメーターなしのコンストラクターが必要であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="18ab8-103">The `new` constraint specifies that any type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="18ab8-104">new 制約を使用する場合、型を抽象型にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="18ab8-104">To use the new constraint, the type cannot be abstract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18ab8-105">例</span><span class="sxs-lookup"><span data-stu-id="18ab8-105">Example</span></span>  
 <span data-ttu-id="18ab8-106">`new` 制約は、次の例に示すように、ジェネリック クラスである型の新しいインスタンスを作成する場合に型パラメーターに適用されます。</span><span class="sxs-lookup"><span data-stu-id="18ab8-106">Apply the `new` constraint to a type parameter when your generic class creates new instances of the type, as shown in the following example:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="18ab8-107">例</span><span class="sxs-lookup"><span data-stu-id="18ab8-107">Example</span></span>  
 <span data-ttu-id="18ab8-108">`new()` 制約を別の制約と併用する場合、この制約を最後に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18ab8-108">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_2.cs)]  
  
 <span data-ttu-id="18ab8-109">詳細については、「[型パラメーターの制約](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18ab8-109">For more information, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="18ab8-110">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="18ab8-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="18ab8-111">参照</span><span class="sxs-lookup"><span data-stu-id="18ab8-111">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="18ab8-112">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="18ab8-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="18ab8-113">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="18ab8-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="18ab8-114">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="18ab8-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="18ab8-115">演算子のキーワード</span><span class="sxs-lookup"><span data-stu-id="18ab8-115">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="18ab8-116">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="18ab8-116">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
