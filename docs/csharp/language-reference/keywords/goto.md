---
title: "goto (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords: goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aa12a7547cfcd4a2076b5b0a308139f8a823f482
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="goto-c-reference"></a><span data-ttu-id="2bb53-102">goto (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="2bb53-102">goto (C# Reference)</span></span>
<span data-ttu-id="2bb53-103">`goto` ステートメントは、プログラムの制御をラベル付きステートメントに直接移します。</span><span class="sxs-lookup"><span data-stu-id="2bb53-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>  
  
 <span data-ttu-id="2bb53-104">`goto` の一般的な用途は、特定の switch-case ラベルまたは `switch` ステートメントの既定のラベルに、制御を移動することです。</span><span class="sxs-lookup"><span data-stu-id="2bb53-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>  
  
 <span data-ttu-id="2bb53-105">`goto` ステートメントは、深い入れ子のループから抜ける場合にも便利です。</span><span class="sxs-lookup"><span data-stu-id="2bb53-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bb53-106">例</span><span class="sxs-lookup"><span data-stu-id="2bb53-106">Example</span></span>  
 <span data-ttu-id="2bb53-107">次の例では、[switch](../../../csharp/language-reference/keywords/switch.md) ステートメントでの `goto` の使い方を示します。</span><span class="sxs-lookup"><span data-stu-id="2bb53-107">The following example demonstrates using `goto` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="2bb53-108">例</span><span class="sxs-lookup"><span data-stu-id="2bb53-108">Example</span></span>  
 <span data-ttu-id="2bb53-109">次の例では、`goto` を使って入れ子になったループから抜け出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2bb53-109">The following example demonstrates using `goto` to break out from nested loops.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="2bb53-110">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="2bb53-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2bb53-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="2bb53-111">See Also</span></span>  
 [<span data-ttu-id="2bb53-112">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="2bb53-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2bb53-113">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="2bb53-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2bb53-114">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="2bb53-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="2bb53-115">goto ステートメント</span><span class="sxs-lookup"><span data-stu-id="2bb53-115">goto Statement</span></span>](/cpp/cpp/goto-statement-cpp)  
 [<span data-ttu-id="2bb53-116">ジャンプ ステートメント</span><span class="sxs-lookup"><span data-stu-id="2bb53-116">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
