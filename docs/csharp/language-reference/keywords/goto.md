---
title: goto (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: 2dd70a30b885dcdae9637b02e8c34ac39f4879fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="goto-c-reference"></a><span data-ttu-id="80893-102">goto (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="80893-102">goto (C# Reference)</span></span>
<span data-ttu-id="80893-103">`goto` ステートメントは、プログラムの制御をラベル付きステートメントに直接移します。</span><span class="sxs-lookup"><span data-stu-id="80893-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>  
  
 <span data-ttu-id="80893-104">`goto` の一般的な用途は、特定の switch-case ラベルまたは `switch` ステートメントの既定のラベルに、制御を移動することです。</span><span class="sxs-lookup"><span data-stu-id="80893-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>  
  
 <span data-ttu-id="80893-105">`goto` ステートメントは、深い入れ子のループから抜ける場合にも便利です。</span><span class="sxs-lookup"><span data-stu-id="80893-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80893-106">例</span><span class="sxs-lookup"><span data-stu-id="80893-106">Example</span></span>  
 <span data-ttu-id="80893-107">次の例では、[switch](../../../csharp/language-reference/keywords/switch.md) ステートメントでの `goto` の使い方を示します。</span><span class="sxs-lookup"><span data-stu-id="80893-107">The following example demonstrates using `goto` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="80893-108">例</span><span class="sxs-lookup"><span data-stu-id="80893-108">Example</span></span>  
 <span data-ttu-id="80893-109">次の例では、`goto` を使って入れ子になったループから抜け出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="80893-109">The following example demonstrates using `goto` to break out from nested loops.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="80893-110">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="80893-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="80893-111">参照</span><span class="sxs-lookup"><span data-stu-id="80893-111">See Also</span></span>  
 [<span data-ttu-id="80893-112">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="80893-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="80893-113">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="80893-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="80893-114">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="80893-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="80893-115">GoTo ステートメント</span><span class="sxs-lookup"><span data-stu-id="80893-115">goto Statement</span></span>](/cpp/cpp/goto-statement-cpp)  
 [<span data-ttu-id="80893-116">ジャンプ ステートメント</span><span class="sxs-lookup"><span data-stu-id="80893-116">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
