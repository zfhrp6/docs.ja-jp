---
title: "Checked と Unchecked (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4b7b18b39dbfa7ed0818d9ea6e9e62ef79a9f5b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="359bc-102">Checked と Unchecked (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="359bc-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="359bc-103">C# のステートメントは、checked または unchecked のいずれかのコンテキストで実行できます。</span><span class="sxs-lookup"><span data-stu-id="359bc-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="359bc-104">checked コンテキストでは、算術オーバーフローにより例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="359bc-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="359bc-105">unchecked コンテキストでは、算術オーバーフローは無視され、結果は切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="359bc-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated.</span></span>  
  
-   <span data-ttu-id="359bc-106">[checked](../../../csharp/language-reference/keywords/checked.md): checked コンテキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="359bc-106">[checked](../../../csharp/language-reference/keywords/checked.md) Specify checked context.</span></span>  
  
-   <span data-ttu-id="359bc-107">[unchecked](../../../csharp/language-reference/keywords/unchecked.md): unchecked コンテキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="359bc-107">[unchecked](../../../csharp/language-reference/keywords/unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="359bc-108">`checked` と `unchecked` が両方とも指定されない場合、既定のコンテキストはコンパイラ オプションなどの外的要因に依存します。</span><span class="sxs-lookup"><span data-stu-id="359bc-108">If neither `checked` nor `unchecked` is specified, the default context depends on external factors such as compiler options.</span></span>  
  
 <span data-ttu-id="359bc-109">オーバーフロー チェックにより、次の操作が影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="359bc-109">The following operations are affected by the overflow checking:</span></span>  
  
-   <span data-ttu-id="359bc-110">整数型で次の定義済み演算子を使用する式:</span><span class="sxs-lookup"><span data-stu-id="359bc-110">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="359bc-111">`++` `--` - (単項)   `+` -   `*` `/`</span><span class="sxs-lookup"><span data-stu-id="359bc-111">`++` `--` - (unary)   `+` -   `*` `/`</span></span>  
  
-   <span data-ttu-id="359bc-112">整数型間の明示的な数値変換。</span><span class="sxs-lookup"><span data-stu-id="359bc-112">Explicit numeric conversions between integral types.</span></span>  
  
 <span data-ttu-id="359bc-113">[/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) コンパイラ オプションにより、`checked` または `unchecked` キーワードの明示的な範囲内にはないすべての整数の算術ステートメントに対して、checked コンテキストまたは unchecked コンテキストを指定できます。</span><span class="sxs-lookup"><span data-stu-id="359bc-113">The [/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) compiler option lets you specify checked or unchecked context for all integer arithmetic statements that are not explicitly in the scope of a `checked` or `unchecked` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="359bc-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="359bc-114">See Also</span></span>  
 [<span data-ttu-id="359bc-115">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="359bc-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="359bc-116">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="359bc-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="359bc-117">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="359bc-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="359bc-118">ステートメントのキーワード</span><span class="sxs-lookup"><span data-stu-id="359bc-118">Statement Keywords</span></span>](../../../csharp/language-reference/keywords/statement-keywords.md)
