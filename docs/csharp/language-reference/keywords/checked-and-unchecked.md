---
title: Checked と Unchecked (C# リファレンス)
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: f8e292a67fab49b5fc3616e438d063eca2617274
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/18/2018
ms.locfileid: "34234374"
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="ffced-102">Checked と Unchecked (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="ffced-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="ffced-103">C# のステートメントは、checked または unchecked のいずれかのコンテキストで実行できます。</span><span class="sxs-lookup"><span data-stu-id="ffced-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="ffced-104">checked コンテキストでは、算術オーバーフローにより例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="ffced-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="ffced-105">unchecked コンテキストでは、算術オーバーフローが無視され、結果の格納先の型に収まらない上位ビットが破棄されて、結果が切り詰められます。</span><span class="sxs-lookup"><span data-stu-id="ffced-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
-   <span data-ttu-id="ffced-106">[checked](checked.md): checked コンテキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="ffced-106">[checked](checked.md) Specify checked context.</span></span>  
  
-   <span data-ttu-id="ffced-107">[unchecked](unchecked.md): unchecked コンテキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="ffced-107">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="ffced-108">オーバーフロー チェックにより、次の操作が影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="ffced-108">The following operations are affected by the overflow checking:</span></span>  
  
-   <span data-ttu-id="ffced-109">整数型で次の定義済み演算子を使用する式:</span><span class="sxs-lookup"><span data-stu-id="ffced-109">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="ffced-110">`++` `--` (単項) `-` `+` `-` `*` `/`</span><span class="sxs-lookup"><span data-stu-id="ffced-110">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
-   <span data-ttu-id="ffced-111">整数型間か、`float` または `double` から整数型へのの明示的な数値変換。</span><span class="sxs-lookup"><span data-stu-id="ffced-111">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="ffced-112">`checked` と `unchecked` のいずれも指定されない場合、非定数式 (実行時に評価される式) の既定のコンテキストが [-checked](../compiler-options/checked-compiler-option.md) コンパイラ オプションの値によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="ffced-112">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="ffced-113">既定では、そのオプションの値の設定が解除され、算術演算が unchecked コンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="ffced-113">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>
 
 <span data-ttu-id="ffced-114">定数式 (コンパイル時に完全に評価される式) の場合、既定のコンテキストは常に確認されます。</span><span class="sxs-lookup"><span data-stu-id="ffced-114">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="ffced-115">定数式が unchecked コンテキストに明示的に配置されていない限り、式のコンパイル時の評価中に発生するオーバーフローによってコンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="ffced-115">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ffced-116">参照</span><span class="sxs-lookup"><span data-stu-id="ffced-116">See Also</span></span>  
 [<span data-ttu-id="ffced-117">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="ffced-117">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="ffced-118">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="ffced-118">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="ffced-119">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="ffced-119">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="ffced-120">ステートメントのキーワード</span><span class="sxs-lookup"><span data-stu-id="ffced-120">Statement Keywords</span></span>](statement-keywords.md)
