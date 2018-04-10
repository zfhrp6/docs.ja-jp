---
title: checked (C# リファレンス)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
caps.latest.revision: 24
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0ae77894cdc94e41dfa281b92ed3304e0dc25731
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="checked-c-reference"></a><span data-ttu-id="6530d-102">checked (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="6530d-102">checked (C# Reference)</span></span>
<span data-ttu-id="6530d-103">`checked` キーワードは、整数型の算術演算と変換に対してオーバーフロー チェックを明示的に有効にするために使用します。</span><span class="sxs-lookup"><span data-stu-id="6530d-103">The `checked` keyword is used to explicitly enable overflow checking for integral-type arithmetic operations and conversions.</span></span>  
  
 <span data-ttu-id="6530d-104">既定では、定数値のみを含む式がチェック先の型の範囲外にある値を生成した場合、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="6530d-104">By default, an expression that contains only constant values causes a compiler error if the expression produces a value that is outside the range of the destination type.</span></span> <span data-ttu-id="6530d-105">式が 1 つ以上の非定数値を含む場合、コンパイラはオーバーフローを検出しません。</span><span class="sxs-lookup"><span data-stu-id="6530d-105">If the expression contains one or more non-constant values, the compiler does not detect the overflow.</span></span> <span data-ttu-id="6530d-106">次の例で `i2` に割り当てられた式を評価しても、コンパイラ エラーは発生しません。</span><span class="sxs-lookup"><span data-stu-id="6530d-106">Evaluating the expression assigned to `i2` in the following example does not cause a compiler error.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_1.cs)]  
  
 <span data-ttu-id="6530d-107">既定では、これらの非定数式のオーバーフローは実行時にもチェックされず、オーバーフロー例外も発生しません。</span><span class="sxs-lookup"><span data-stu-id="6530d-107">By default, these non-constant expressions are not checked for overflow at run time either, and they do not raise overflow exceptions.</span></span> <span data-ttu-id="6530d-108">前の例では、2 つの正の整数の合計として -2,147,483,639 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6530d-108">The previous example displays -2,147,483,639 as the sum of two positive integers.</span></span>  
  
 <span data-ttu-id="6530d-109">オーバーフロー チェックを有効にするには、コンパイラ オプション、環境設定、または `checked` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="6530d-109">Overflow checking can be enabled by compiler options, environment configuration, or use of the `checked` keyword.</span></span> <span data-ttu-id="6530d-110">`checked` 式または `checked` ブロックを使用して、前の合計によって生じたオーバーフローを実行時に検出する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="6530d-110">The following examples demonstrate how to use a `checked` expression or a `checked` block to detect the overflow that is produced by the previous sum at run time.</span></span> <span data-ttu-id="6530d-111">どちらの例でもオーバーフロー例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="6530d-111">Both examples raise an overflow exception.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_2.cs)]  
  
 <span data-ttu-id="6530d-112">[unchecked](../../../csharp/language-reference/keywords/unchecked.md) キーワードを使用してオーバーフロー チェックを行わないようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="6530d-112">The [unchecked](../../../csharp/language-reference/keywords/unchecked.md) keyword can be used to prevent overflow checking.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6530d-113">例</span><span class="sxs-lookup"><span data-stu-id="6530d-113">Example</span></span>  
 <span data-ttu-id="6530d-114">この例では、`checked` を使用して実行時のオーバーフロー チェックを有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6530d-114">This sample shows how to use `checked` to enable overflow checking at run time.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="6530d-115">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="6530d-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6530d-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="6530d-116">See Also</span></span>  
 [<span data-ttu-id="6530d-117">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="6530d-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6530d-118">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="6530d-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6530d-119">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="6530d-119">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="6530d-120">Checked と Unchecked</span><span class="sxs-lookup"><span data-stu-id="6530d-120">Checked and Unchecked</span></span>](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
 [<span data-ttu-id="6530d-121">unchecked</span><span class="sxs-lookup"><span data-stu-id="6530d-121">unchecked</span></span>](../../../csharp/language-reference/keywords/unchecked.md)
