---
title: checked (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
ms.openlocfilehash: b05af798217a4f312bcf134d531135713efa8c66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="checked-c-reference"></a><span data-ttu-id="9ff6b-102">checked (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="9ff6b-102">checked (C# Reference)</span></span>
<span data-ttu-id="9ff6b-103">`checked` キーワードは、整数型の算術演算と変換に対してオーバーフロー チェックを明示的に有効にするために使用します。</span><span class="sxs-lookup"><span data-stu-id="9ff6b-103">The `checked` keyword is used to explicitly enable overflow checking for integral-type arithmetic operations and conversions.</span></span>  
  
 <span data-ttu-id="9ff6b-104">既定では、定数値のみを含む式がチェック先の型の範囲外にある値を生成した場合、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="9ff6b-104">By default, an expression that contains only constant values causes a compiler error if the expression produces a value that is outside the range of the destination type.</span></span> <span data-ttu-id="9ff6b-105">式が 1 つ以上の非定数値を含む場合、コンパイラはオーバーフローを検出しません。</span><span class="sxs-lookup"><span data-stu-id="9ff6b-105">If the expression contains one or more non-constant values, the compiler does not detect the overflow.</span></span> <span data-ttu-id="9ff6b-106">次の例で `i2` に割り当てられた式を評価しても、コンパイラ エラーは発生しません。</span><span class="sxs-lookup"><span data-stu-id="9ff6b-106">Evaluating the expression assigned to `i2` in the following example does not cause a compiler error.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_1.cs)]  
  
 <span data-ttu-id="9ff6b-107">既定では、これらの非定数式のオーバーフローは実行時にもチェックされず、オーバーフロー例外も発生しません。</span><span class="sxs-lookup"><span data-stu-id="9ff6b-107">By default, these non-constant expressions are not checked for overflow at run time either, and they do not raise overflow exceptions.</span></span> <span data-ttu-id="9ff6b-108">前の例では、2 つの正の整数の合計として -2,147,483,639 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ff6b-108">The previous example displays -2,147,483,639 as the sum of two positive integers.</span></span>  
  
 <span data-ttu-id="9ff6b-109">オーバーフロー チェックを有効にするには、コンパイラ オプション、環境設定、または `checked` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="9ff6b-109">Overflow checking can be enabled by compiler options, environment configuration, or use of the `checked` keyword.</span></span> <span data-ttu-id="9ff6b-110">`checked` 式または `checked` ブロックを使用して、前の合計によって生じたオーバーフローを実行時に検出する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="9ff6b-110">The following examples demonstrate how to use a `checked` expression or a `checked` block to detect the overflow that is produced by the previous sum at run time.</span></span> <span data-ttu-id="9ff6b-111">どちらの例でもオーバーフロー例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="9ff6b-111">Both examples raise an overflow exception.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_2.cs)]  
  
 <span data-ttu-id="9ff6b-112">[unchecked](../../../csharp/language-reference/keywords/unchecked.md) キーワードを使用してオーバーフロー チェックを行わないようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="9ff6b-112">The [unchecked](../../../csharp/language-reference/keywords/unchecked.md) keyword can be used to prevent overflow checking.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ff6b-113">例</span><span class="sxs-lookup"><span data-stu-id="9ff6b-113">Example</span></span>  
 <span data-ttu-id="9ff6b-114">この例では、`checked` を使用して実行時のオーバーフロー チェックを有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9ff6b-114">This sample shows how to use `checked` to enable overflow checking at run time.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="9ff6b-115">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="9ff6b-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9ff6b-116">参照</span><span class="sxs-lookup"><span data-stu-id="9ff6b-116">See Also</span></span>  
 [<span data-ttu-id="9ff6b-117">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="9ff6b-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9ff6b-118">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="9ff6b-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9ff6b-119">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="9ff6b-119">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="9ff6b-120">Checked と Unchecked</span><span class="sxs-lookup"><span data-stu-id="9ff6b-120">Checked and Unchecked</span></span>](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
 [<span data-ttu-id="9ff6b-121">unchecked</span><span class="sxs-lookup"><span data-stu-id="9ff6b-121">unchecked</span></span>](../../../csharp/language-reference/keywords/unchecked.md)
