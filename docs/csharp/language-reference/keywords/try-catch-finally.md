---
title: "try-catch-finally (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
dev_langs:
- CSharp
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
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
ms.openlocfilehash: 05b2e0075aae79f85fba26d64690eefadaa166cd
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="067ca-102">try-catch-finally (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="067ca-102">try-catch-finally (C# Reference)</span></span>
<span data-ttu-id="067ca-103">通常、`catch` および `finally` は、`try` ブロックのリソースを取得して使用する場合に、対で記述されます。`catch` ブロックで例外的な状況を処理し、`finally` ブロックでリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="067ca-103">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>  
  
 <span data-ttu-id="067ca-104">例外の再スローの使用例を含む詳細については、「[try-catch](../../../csharp/language-reference/keywords/try-catch.md)」および[例外のスロー](https://msdn.microsoft.com/library/xhcbs8fz)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="067ca-104">For more information and examples on re-throwing exceptions, see [try-catch](../../../csharp/language-reference/keywords/try-catch.md) and [Throwing Exceptions](https://msdn.microsoft.com/library/xhcbs8fz).</span></span> <span data-ttu-id="067ca-105">`finally` ブロックの詳細については、「[try-finally](../../../csharp/language-reference/keywords/try-finally.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="067ca-105">For more information about the `finally` block, see [try-finally](../../../csharp/language-reference/keywords/try-finally.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="067ca-106">例</span><span class="sxs-lookup"><span data-stu-id="067ca-106">Example</span></span>  
 <span data-ttu-id="067ca-107">[!code-cs[csrefKeywordsExceptions#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch-finally_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="067ca-107">[!code-cs[csrefKeywordsExceptions#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch-finally_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="067ca-108">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="067ca-108">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="067ca-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="067ca-109">See Also</span></span>  
 <span data-ttu-id="067ca-110">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="067ca-110">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="067ca-111">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="067ca-111">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="067ca-112">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="067ca-112">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="067ca-113">[try、throw、catch ステートメント (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp) </span><span class="sxs-lookup"><span data-stu-id="067ca-113">[try, throw, and catch Statements (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp) </span></span>  
 <span data-ttu-id="067ca-114">[例外処理ステートメント](../../../csharp/language-reference/keywords/exception-handling-statements.md) </span><span class="sxs-lookup"><span data-stu-id="067ca-114">[Exception Handling Statements](../../../csharp/language-reference/keywords/exception-handling-statements.md) </span></span>  
 <span data-ttu-id="067ca-115">[throw](../../../csharp/language-reference/keywords/throw.md) </span><span class="sxs-lookup"><span data-stu-id="067ca-115">[throw](../../../csharp/language-reference/keywords/throw.md) </span></span>  
 <span data-ttu-id="067ca-116">[方法: 例外を明示的にスローする](https://msdn.microsoft.com/library/xhcbs8fz) </span><span class="sxs-lookup"><span data-stu-id="067ca-116">[How to: Explicitly Throw Exceptions](https://msdn.microsoft.com/library/xhcbs8fz) </span></span>  
 [<span data-ttu-id="067ca-117">using ステートメント</span><span class="sxs-lookup"><span data-stu-id="067ca-117">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)

