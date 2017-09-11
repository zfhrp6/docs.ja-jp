---
title: "goto (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- goto_CSharpKeyword
- goto
dev_langs:
- CSharp
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
caps.latest.revision: 22
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
ms.openlocfilehash: cd298809ab883f425f3bb88239f2951ab98cc03e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="goto-c-reference"></a><span data-ttu-id="64d5f-102">goto (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="64d5f-102">goto (C# Reference)</span></span>
<span data-ttu-id="64d5f-103">`goto` ステートメントは、プログラムの制御をラベル付きステートメントに直接移します。</span><span class="sxs-lookup"><span data-stu-id="64d5f-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>  
  
 <span data-ttu-id="64d5f-104">`goto` の一般的な用途は、特定の switch-case ラベルまたは `switch` ステートメントの既定のラベルに、制御を移動することです。</span><span class="sxs-lookup"><span data-stu-id="64d5f-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>  
  
 <span data-ttu-id="64d5f-105">`goto` ステートメントは、深い入れ子のループから抜ける場合にも便利です。</span><span class="sxs-lookup"><span data-stu-id="64d5f-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64d5f-106">例</span><span class="sxs-lookup"><span data-stu-id="64d5f-106">Example</span></span>  
 <span data-ttu-id="64d5f-107">次の例では、[switch](../../../csharp/language-reference/keywords/switch.md) ステートメントでの `goto` の使い方を示します。</span><span class="sxs-lookup"><span data-stu-id="64d5f-107">The following example demonstrates using `goto` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>  
  
 <span data-ttu-id="64d5f-108">[!code-cs[csrefKeywordsJump#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="64d5f-108">[!code-cs[csrefKeywordsJump#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="64d5f-109">例</span><span class="sxs-lookup"><span data-stu-id="64d5f-109">Example</span></span>  
 <span data-ttu-id="64d5f-110">次の例では、`goto` を使って入れ子になったループから抜け出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="64d5f-110">The following example demonstrates using `goto` to break out from nested loops.</span></span>  
  
 <span data-ttu-id="64d5f-111">[!code-cs[csrefKeywordsJump#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="64d5f-111">[!code-cs[csrefKeywordsJump#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="64d5f-112">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="64d5f-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="64d5f-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="64d5f-113">See Also</span></span>  
 <span data-ttu-id="64d5f-114">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="64d5f-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="64d5f-115">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="64d5f-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="64d5f-116">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="64d5f-116">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="64d5f-117">[GoTo ステートメント](/cpp/cpp/goto-statement-cpp) </span><span class="sxs-lookup"><span data-stu-id="64d5f-117">[goto Statement](/cpp/cpp/goto-statement-cpp) </span></span>  
 [<span data-ttu-id="64d5f-118">ジャンプ ステートメント</span><span class="sxs-lookup"><span data-stu-id="64d5f-118">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)

