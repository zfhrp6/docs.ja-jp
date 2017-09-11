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
ms.lasthandoff: 07/28/2017

---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="fa498-102">パラメーターの引き渡し (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="fa498-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="fa498-103">C# では、引数を値または参照によってパラメーターに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="fa498-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="fa498-104">参照渡しでは、関数メンバー、メソッド、プロパティ、インデクサー、演算子、およびコンストラクターは、パラメーターの値を変更でき、その変更を呼び出し元の環境で永続化できます。</span><span class="sxs-lookup"><span data-stu-id="fa498-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="fa498-105">パラメーターを参照で渡すには、`ref` キーワードまたは `out` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="fa498-105">To pass a parameter by reference, use the `ref` or `out` keyword.</span></span> <span data-ttu-id="fa498-106">ここでは、説明を簡単にするために、例に `ref` キーワードだけを使用しています。</span><span class="sxs-lookup"><span data-stu-id="fa498-106">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="fa498-107">`ref` と `out` の違いの詳細については、「[ref](../../../csharp/language-reference/keywords/ref.md)」、「[out](../../../csharp/language-reference/keywords/out.md)」、および「[ref と out を使用した配列の引き渡し](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa498-107">For more information about the difference between `ref` and `out`, see [ref](../../../csharp/language-reference/keywords/ref.md), [out](../../../csharp/language-reference/keywords/out.md), and [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="fa498-108">次の例は、値パラメーターと参照パラメーターの違いを示しています。</span><span class="sxs-lookup"><span data-stu-id="fa498-108">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 <span data-ttu-id="fa498-109">[!code-cs[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="fa498-109">[!code-cs[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]</span></span>  
  
 <span data-ttu-id="fa498-110">詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fa498-110">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="fa498-111">値型パラメーターの引き渡し</span><span class="sxs-lookup"><span data-stu-id="fa498-111">Passing Value-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [<span data-ttu-id="fa498-112">参照型パラメーターの引き渡し</span><span class="sxs-lookup"><span data-stu-id="fa498-112">Passing Reference-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="fa498-113">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="fa498-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fa498-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa498-114">See Also</span></span>  
 <span data-ttu-id="fa498-115">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="fa498-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="fa498-116">メソッド</span><span class="sxs-lookup"><span data-stu-id="fa498-116">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)

