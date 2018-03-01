---
title: "continue (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1ace2c90d03593b51b9ea461a47e122c5da1ab81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="continue-c-reference"></a><span data-ttu-id="fd636-102">continue (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="fd636-102">continue (C# Reference)</span></span>
<span data-ttu-id="fd636-103">`continue` ステートメントは、それを囲んでいる [while](../../../csharp/language-reference/keywords/while.md)、[do](../../../csharp/language-reference/keywords/do.md)、[for](../../../csharp/language-reference/keywords/for.md)、または [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ステートメントの次の反復処理にコントロールを渡します。</span><span class="sxs-lookup"><span data-stu-id="fd636-103">The `continue` statement passes control to the next iteration of the enclosing [while](../../../csharp/language-reference/keywords/while.md), [do](../../../csharp/language-reference/keywords/do.md), [for](../../../csharp/language-reference/keywords/for.md), or [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement in which it appears.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd636-104">例</span><span class="sxs-lookup"><span data-stu-id="fd636-104">Example</span></span>  
 <span data-ttu-id="fd636-105">この例では、1 から 10 までカウントするようカウンターが初期化されます。</span><span class="sxs-lookup"><span data-stu-id="fd636-105">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="fd636-106">`continue` ステートメントと式 `(i < 9)` を組み合わせて使用すると、`for` 本文の `continue` から終わりまでのステートメントがスキップされます。</span><span class="sxs-lookup"><span data-stu-id="fd636-106">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/continue_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="fd636-107">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="fd636-107">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fd636-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="fd636-108">See Also</span></span>  
 [<span data-ttu-id="fd636-109">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="fd636-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="fd636-110">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="fd636-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="fd636-111">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="fd636-111">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="fd636-112">break ステートメント</span><span class="sxs-lookup"><span data-stu-id="fd636-112">break Statement</span></span>](/cpp/cpp/break-statement-cpp)  
 [<span data-ttu-id="fd636-113">ジャンプ ステートメント</span><span class="sxs-lookup"><span data-stu-id="fd636-113">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
