---
title: "return (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 90c84b51c6ee57864eac552bc488c9f9c15e9394
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="return-c-reference"></a><span data-ttu-id="2edcd-102">return (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="2edcd-102">return (C# Reference)</span></span>
<span data-ttu-id="2edcd-103">`return` ステートメントは、メソッドの実行を終了し、呼び出し側のメソッドに制御を戻します。</span><span class="sxs-lookup"><span data-stu-id="2edcd-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="2edcd-104">省略可能な値を返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="2edcd-104">It can also return an optional value.</span></span> <span data-ttu-id="2edcd-105">メソッドが `void` 型の場合、`return` ステートメントは省略できます。</span><span class="sxs-lookup"><span data-stu-id="2edcd-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>  
  
 <span data-ttu-id="2edcd-106">return ステートメントが `try` ブロック内にある場合は、制御が呼び出し側のメソッドに返される前に、`finally` ブロック (存在する場合) が実行されます。</span><span class="sxs-lookup"><span data-stu-id="2edcd-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2edcd-107">例</span><span class="sxs-lookup"><span data-stu-id="2edcd-107">Example</span></span>  
 <span data-ttu-id="2edcd-108">次の例では、メソッドで`CalculateArea()`ローカル変数を返す`area`として、[二重](../../../csharp/language-reference/keywords/double.md)値。</span><span class="sxs-lookup"><span data-stu-id="2edcd-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a [double](../../../csharp/language-reference/keywords/double.md) value.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/return_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="2edcd-109">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="2edcd-109">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2edcd-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="2edcd-110">See Also</span></span>  
 [<span data-ttu-id="2edcd-111">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="2edcd-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2edcd-112">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="2edcd-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2edcd-113">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="2edcd-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="2edcd-114">return ステートメント</span><span class="sxs-lookup"><span data-stu-id="2edcd-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)  
 [<span data-ttu-id="2edcd-115">ジャンプ ステートメント</span><span class="sxs-lookup"><span data-stu-id="2edcd-115">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
