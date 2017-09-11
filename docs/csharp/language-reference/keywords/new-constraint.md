---
title: "new 制約 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
caps.latest.revision: 20
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
ms.openlocfilehash: 762941794184605f90443ed8f36c88ecfa50aa84
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="d76e9-102">new 制約 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="d76e9-102">new Constraint (C# Reference)</span></span>
<span data-ttu-id="d76e9-103">`new` 制約は、ジェネリック クラス宣言内のすべての型引数に、パブリックでパラメーターなしのコンストラクターが必要であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="d76e9-103">The `new` constraint specifies that any type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="d76e9-104">new 制約を使用する場合、型を抽象型にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="d76e9-104">To use the new constraint, the type cannot be abstract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d76e9-105">例</span><span class="sxs-lookup"><span data-stu-id="d76e9-105">Example</span></span>  
 <span data-ttu-id="d76e9-106">`new` 制約は、次の例に示すように、ジェネリック クラスである型の新しいインスタンスを作成する場合に型パラメーターに適用されます。</span><span class="sxs-lookup"><span data-stu-id="d76e9-106">Apply the `new` constraint to a type parameter when your generic class creates new instances of the type, as shown in the following example:</span></span>  
  
 <span data-ttu-id="d76e9-107">[!code-cs[csrefKeywordsOperator#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d76e9-107">[!code-cs[csrefKeywordsOperator#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="d76e9-108">例</span><span class="sxs-lookup"><span data-stu-id="d76e9-108">Example</span></span>  
 <span data-ttu-id="d76e9-109">`new()` 制約を別の制約と併用する場合、この制約を最後に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d76e9-109">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>  
  
 <span data-ttu-id="d76e9-110">[!code-cs[csrefKeywordsOperator#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="d76e9-110">[!code-cs[csrefKeywordsOperator#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-constraint_2.cs)]</span></span>  
  
 <span data-ttu-id="d76e9-111">詳細については、「[型パラメーターの制約](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d76e9-111">For more information, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="d76e9-112">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="d76e9-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d76e9-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="d76e9-113">See Also</span></span>  
 <span data-ttu-id="d76e9-114"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="d76e9-114"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="d76e9-115">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="d76e9-115">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="d76e9-116">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d76e9-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="d76e9-117">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="d76e9-117">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="d76e9-118">[演算子キーワード](../../../csharp/language-reference/keywords/operator-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="d76e9-118">[Operator Keywords](../../../csharp/language-reference/keywords/operator-keywords.md) </span></span>  
 [<span data-ttu-id="d76e9-119">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="d76e9-119">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)

