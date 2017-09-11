---
title: "checked (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- checked_CSharpKeyword
- checked
dev_langs:
- CSharp
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
caps.latest.revision: 24
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
ms.openlocfilehash: abe34772c0f07b0a43f7299088bf5ea9a1d2aa78
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="checked-c-reference"></a><span data-ttu-id="cb30d-102">checked (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="cb30d-102">checked (C# Reference)</span></span>
<span data-ttu-id="cb30d-103">`checked` キーワードは、整数型の算術演算と変換に対してオーバーフロー チェックを明示的に有効にするために使用します。</span><span class="sxs-lookup"><span data-stu-id="cb30d-103">The `checked` keyword is used to explicitly enable overflow checking for integral-type arithmetic operations and conversions.</span></span>  
  
 <span data-ttu-id="cb30d-104">既定では、定数値のみを含む式がチェック先の型の範囲外にある値を生成した場合、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="cb30d-104">By default, an expression that contains only constant values causes a compiler error if the expression produces a value that is outside the range of the destination type.</span></span> <span data-ttu-id="cb30d-105">式が 1 つ以上の非定数値を含む場合、コンパイラはオーバーフローを検出しません。</span><span class="sxs-lookup"><span data-stu-id="cb30d-105">If the expression contains one or more non-constant values, the compiler does not detect the overflow.</span></span> <span data-ttu-id="cb30d-106">次の例で `i2` に割り当てられた式を評価しても、コンパイラ エラーは発生しません。</span><span class="sxs-lookup"><span data-stu-id="cb30d-106">Evaluating the expression assigned to `i2` in the following example does not cause a compiler error.</span></span>  
  
 <span data-ttu-id="cb30d-107">[!code-cs[csrefKeywordsChecked#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="cb30d-107">[!code-cs[csrefKeywordsChecked#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_1.cs)]</span></span>  
  
 <span data-ttu-id="cb30d-108">既定では、これらの非定数式のオーバーフローは実行時にもチェックされず、オーバーフロー例外も発生しません。</span><span class="sxs-lookup"><span data-stu-id="cb30d-108">By default, these non-constant expressions are not checked for overflow at run time either, and they do not raise overflow exceptions.</span></span> <span data-ttu-id="cb30d-109">前の例では、2 つの正の整数の合計として -2,147,483,639 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb30d-109">The previous example displays -2,147,483,639 as the sum of two positive integers.</span></span>  
  
 <span data-ttu-id="cb30d-110">オーバーフロー チェックを有効にするには、コンパイラ オプション、環境設定、または `checked` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="cb30d-110">Overflow checking can be enabled by compiler options, environment configuration, or use of the `checked` keyword.</span></span> <span data-ttu-id="cb30d-111">`checked` 式または `checked` ブロックを使用して、前の合計によって生じたオーバーフローを実行時に検出する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="cb30d-111">The following examples demonstrate how to use a `checked` expression or a `checked` block to detect the overflow that is produced by the previous sum at run time.</span></span> <span data-ttu-id="cb30d-112">どちらの例でもオーバーフロー例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="cb30d-112">Both examples raise an overflow exception.</span></span>  
  
 <span data-ttu-id="cb30d-113">[!code-cs[csrefKeywordsChecked#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="cb30d-113">[!code-cs[csrefKeywordsChecked#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_2.cs)]</span></span>  
  
 <span data-ttu-id="cb30d-114">[unchecked](../../../csharp/language-reference/keywords/unchecked.md) キーワードを使用してオーバーフロー チェックを行わないようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="cb30d-114">The [unchecked](../../../csharp/language-reference/keywords/unchecked.md) keyword can be used to prevent overflow checking.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb30d-115">例</span><span class="sxs-lookup"><span data-stu-id="cb30d-115">Example</span></span>  
 <span data-ttu-id="cb30d-116">この例では、`checked` を使用して実行時のオーバーフロー チェックを有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="cb30d-116">This sample shows how to use `checked` to enable overflow checking at run time.</span></span>  
  
 <span data-ttu-id="cb30d-117">[!code-cs[csrefKeywordsChecked#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="cb30d-117">[!code-cs[csrefKeywordsChecked#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_3.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="cb30d-118">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="cb30d-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cb30d-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb30d-119">See Also</span></span>  
 <span data-ttu-id="cb30d-120">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="cb30d-120">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="cb30d-121">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="cb30d-121">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="cb30d-122">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="cb30d-122">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="cb30d-123">[Checked と Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md) </span><span class="sxs-lookup"><span data-stu-id="cb30d-123">[Checked and Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md) </span></span>  
 [<span data-ttu-id="cb30d-124">unchecked</span><span class="sxs-lookup"><span data-stu-id="cb30d-124">unchecked</span></span>](../../../csharp/language-reference/keywords/unchecked.md)

