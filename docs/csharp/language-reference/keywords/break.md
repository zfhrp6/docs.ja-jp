---
title: break (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 0cfe722bfefc1befd8a453f4454b05b3e4a0da76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215051"
---
# <a name="break-c-reference"></a><span data-ttu-id="c6dd4-102">break (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="c6dd4-102">break (C# Reference)</span></span>
<span data-ttu-id="c6dd4-103">`break` ステートメントは、これを囲むループまたは [switch](../../../csharp/language-reference/keywords/switch.md) ステートメントのうち、最も内側のものを終了させます。</span><span class="sxs-lookup"><span data-stu-id="c6dd4-103">The `break` statement terminates the closest enclosing loop or [switch](../../../csharp/language-reference/keywords/switch.md) statement in which it appears.</span></span> <span data-ttu-id="c6dd4-104">終了したステートメントの次にステートメントがある場合は、そこに制御が移動します。</span><span class="sxs-lookup"><span data-stu-id="c6dd4-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6dd4-105">例</span><span class="sxs-lookup"><span data-stu-id="c6dd4-105">Example</span></span>  
 <span data-ttu-id="c6dd4-106">次の例では、条件付きステートメントに 1 から 100 までをカウントするカウンターがあります。ただし、`break` ステートメントによって、ループは 4 回で終了します。</span><span class="sxs-lookup"><span data-stu-id="c6dd4-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="c6dd4-107">例</span><span class="sxs-lookup"><span data-stu-id="c6dd4-107">Example</span></span>  
 <span data-ttu-id="c6dd4-108">この例では、`break` ステートメントを使用して、入れ子になった内側のループから抜け出し、外側のループに制御を戻します。</span><span class="sxs-lookup"><span data-stu-id="c6dd4-108">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="c6dd4-109">例</span><span class="sxs-lookup"><span data-stu-id="c6dd4-109">Example</span></span>  
 <span data-ttu-id="c6dd4-110">次に示すのは、[switch](../../../csharp/language-reference/keywords/switch.md) ステートメントで `break` を使用する例です。</span><span class="sxs-lookup"><span data-stu-id="c6dd4-110">This example demonstrates the use of `break` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_3.cs)]  
  
 <span data-ttu-id="c6dd4-111">`4` を入力すると、出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="c6dd4-111">If you entered `4`, the output would be:</span></span>  
  
```  
Enter your selection (1, 2, or 3): 4  
Sorry, invalid selection.  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="c6dd4-112">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="c6dd4-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c6dd4-113">参照</span><span class="sxs-lookup"><span data-stu-id="c6dd4-113">See Also</span></span>  
 [<span data-ttu-id="c6dd4-114">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="c6dd4-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c6dd4-115">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="c6dd4-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c6dd4-116">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="c6dd4-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="c6dd4-117">switch</span><span class="sxs-lookup"><span data-stu-id="c6dd4-117">switch</span></span>](../../../csharp/language-reference/keywords/switch.md)  
 [<span data-ttu-id="c6dd4-118">ジャンプ ステートメント</span><span class="sxs-lookup"><span data-stu-id="c6dd4-118">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)  
 [<span data-ttu-id="c6dd4-119">繰り返しステートメント</span><span class="sxs-lookup"><span data-stu-id="c6dd4-119">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
