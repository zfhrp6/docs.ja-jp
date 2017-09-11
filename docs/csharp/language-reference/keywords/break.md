---
title: "break (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- break
- break_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
caps.latest.revision: 21
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
ms.openlocfilehash: 73f6b6a37513b3aed796d811672fa43fa9e1c0b1
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="break-c-reference"></a><span data-ttu-id="9f1bc-102">break (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="9f1bc-102">break (C# Reference)</span></span>
<span data-ttu-id="9f1bc-103">`break` ステートメントは、これを囲むループまたは [switch](../../../csharp/language-reference/keywords/switch.md) ステートメントのうち、最も内側のものを終了させます。</span><span class="sxs-lookup"><span data-stu-id="9f1bc-103">The `break` statement terminates the closest enclosing loop or [switch](../../../csharp/language-reference/keywords/switch.md) statement in which it appears.</span></span> <span data-ttu-id="9f1bc-104">終了したステートメントの次にステートメントがある場合は、そこに制御が移動します。</span><span class="sxs-lookup"><span data-stu-id="9f1bc-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f1bc-105">例</span><span class="sxs-lookup"><span data-stu-id="9f1bc-105">Example</span></span>  
 <span data-ttu-id="9f1bc-106">次の例では、条件付きステートメントに 1 から 100 までをカウントするカウンターがあります。ただし、`break` ステートメントによって、ループは 4 回で終了します。</span><span class="sxs-lookup"><span data-stu-id="9f1bc-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>  
  
 <span data-ttu-id="9f1bc-107">[!code-cs[csrefKeywordsJump#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9f1bc-107">[!code-cs[csrefKeywordsJump#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f1bc-108">例</span><span class="sxs-lookup"><span data-stu-id="9f1bc-108">Example</span></span>  
 <span data-ttu-id="9f1bc-109">この例では、`break` ステートメントを使用して、入れ子になった内側のループから抜け出し、外側のループに制御を戻します。</span><span class="sxs-lookup"><span data-stu-id="9f1bc-109">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span>  
  
 <span data-ttu-id="9f1bc-110">[!code-cs[csrefKeywordsJump#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="9f1bc-110">[!code-cs[csrefKeywordsJump#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f1bc-111">例</span><span class="sxs-lookup"><span data-stu-id="9f1bc-111">Example</span></span>  
 <span data-ttu-id="9f1bc-112">次に示すのは、[switch](../../../csharp/language-reference/keywords/switch.md) ステートメントで `break` を使用する例です。</span><span class="sxs-lookup"><span data-stu-id="9f1bc-112">This example demonstrates the use of `break` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>  
  
 <span data-ttu-id="9f1bc-113">[!code-cs[csrefKeywordsJump#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="9f1bc-113">[!code-cs[csrefKeywordsJump#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_3.cs)]</span></span>  
  
 <span data-ttu-id="9f1bc-114">`4` を入力すると、出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="9f1bc-114">If you entered `4`, the output would be:</span></span>  
  
```  
Enter your selection (1, 2, or 3): 4  
Sorry, invalid selection.  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="9f1bc-115">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="9f1bc-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9f1bc-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="9f1bc-116">See Also</span></span>  
 <span data-ttu-id="9f1bc-117">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="9f1bc-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="9f1bc-118">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9f1bc-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="9f1bc-119">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="9f1bc-119">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="9f1bc-120">[switch](../../../csharp/language-reference/keywords/switch.md) </span><span class="sxs-lookup"><span data-stu-id="9f1bc-120">[switch](../../../csharp/language-reference/keywords/switch.md) </span></span>  
 <span data-ttu-id="9f1bc-121">[ジャンプ ステートメント](../../../csharp/language-reference/keywords/jump-statements.md) </span><span class="sxs-lookup"><span data-stu-id="9f1bc-121">[Jump Statements](../../../csharp/language-reference/keywords/jump-statements.md) </span></span>  
 [<span data-ttu-id="9f1bc-122">繰り返しステートメント</span><span class="sxs-lookup"><span data-stu-id="9f1bc-122">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)

