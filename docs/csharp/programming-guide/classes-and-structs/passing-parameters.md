---
title: パラメーターの引き渡し (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: a1ccfff8081d101eee46360009653b0591dfb3ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323106"
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="5d4b9-102">パラメーターの引き渡し (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="5d4b9-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="5d4b9-103">C# では、引数を値または参照によってパラメーターに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="5d4b9-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="5d4b9-104">参照渡しでは、関数メンバー、メソッド、プロパティ、インデクサー、演算子、およびコンストラクターは、パラメーターの値を変更でき、その変更を呼び出し元の環境で永続化できます。</span><span class="sxs-lookup"><span data-stu-id="5d4b9-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="5d4b9-105">値を変更する目的でパラメーターを参照で渡すには、`ref` または `out` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="5d4b9-105">To pass a parameter by reference with the intent of changing the value, use the `ref`, or `out` keyword.</span></span> <span data-ttu-id="5d4b9-106">値を変更せずにコピーを回避する目的で参照で渡すには、`in` 修飾子を使用します。</span><span class="sxs-lookup"><span data-stu-id="5d4b9-106">To pass by reference with the intent of avoiding copying but not changing the value, use the `in` modifier.</span></span> <span data-ttu-id="5d4b9-107">ここでは、説明を簡単にするために、例に `ref` キーワードだけを使用しています。</span><span class="sxs-lookup"><span data-stu-id="5d4b9-107">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="5d4b9-108">`in`、`ref`、`out` の違いの詳細については、[in](../../../csharp/language-reference/keywords/in-parameter-modifier.md)、[ref](../../../csharp/language-reference/keywords/ref.md)、[out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) に関するページと「[ref と out を使用した配列の引き渡し](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d4b9-108">For more information about the difference between `in`, `ref`, and `out`, see [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md), [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), and [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="5d4b9-109">次の例は、値パラメーターと参照パラメーターの違いを示しています。</span><span class="sxs-lookup"><span data-stu-id="5d4b9-109">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 <span data-ttu-id="5d4b9-110">詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d4b9-110">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="5d4b9-111">値型パラメーターの引き渡し</span><span class="sxs-lookup"><span data-stu-id="5d4b9-111">Passing Value-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [<span data-ttu-id="5d4b9-112">参照型パラメーターの引き渡し</span><span class="sxs-lookup"><span data-stu-id="5d4b9-112">Passing Reference-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="5d4b9-113">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="5d4b9-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5d4b9-114">参照</span><span class="sxs-lookup"><span data-stu-id="5d4b9-114">See Also</span></span>  
 [<span data-ttu-id="5d4b9-115">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="5d4b9-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5d4b9-116">メソッド</span><span class="sxs-lookup"><span data-stu-id="5d4b9-116">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
