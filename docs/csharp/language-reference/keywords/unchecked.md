---
title: "unchecked (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords: unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c05e7cb742d8e8f5a7804656a5ec13548d0498b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="unchecked-c-reference"></a><span data-ttu-id="a3a51-102">unchecked (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="a3a51-102">unchecked (C# Reference)</span></span>
<span data-ttu-id="a3a51-103">`unchecked` キーワードは、整数型の算術演算と変換に対してオーバーフロー チェックを抑制するために使用します。</span><span class="sxs-lookup"><span data-stu-id="a3a51-103">The `unchecked` keyword is used to suppress overflow-checking for integral-type arithmetic operations and conversions.</span></span>  
  
 <span data-ttu-id="a3a51-104">unchecked コンテキストでは、式が変換先の型の範囲外の値を生成した場合に、オーバーフローが検出されません。</span><span class="sxs-lookup"><span data-stu-id="a3a51-104">In an unchecked context, if an expression produces a value that is outside the range of the destination type, the overflow is not flagged.</span></span> <span data-ttu-id="a3a51-105">たとえば、次の例では、`unchecked` ブロックまたは式で計算が行われるため、結果が integer に対して大きすぎるという事実が無視され、`int1` には-2,147,483,639 の値が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="a3a51-105">For example, because the calculation in the following example is performed in an `unchecked` block or expression, the fact that the result is too large for an integer is ignored, and `int1` is assigned the value -2,147,483,639.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_1.cs)]  
  
 <span data-ttu-id="a3a51-106">`unchecked` 環境が削除されると、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="a3a51-106">If the `unchecked` environment is removed, a compilation error occurs.</span></span> <span data-ttu-id="a3a51-107">式のすべての用語が定数なので、コンパイル時にはオーバーフローを検出できます。</span><span class="sxs-lookup"><span data-stu-id="a3a51-107">The overflow can be detected at compile time because all the terms of the expression are constants.</span></span>  
  
 <span data-ttu-id="a3a51-108">非定数の用語を含む式は、実行時およびコンパイル時に既定ではチェックされません。</span><span class="sxs-lookup"><span data-stu-id="a3a51-108">Expressions that contain non-constant terms are unchecked by default at compile time and run time.</span></span> <span data-ttu-id="a3a51-109">checked 環境を有効にする方法については、「[checked](../../../csharp/language-reference/keywords/checked.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a3a51-109">See [checked](../../../csharp/language-reference/keywords/checked.md) for information about enabling a checked environment.</span></span>  
  
 <span data-ttu-id="a3a51-110">オーバーフローのチェックには時間がかかるため、オーバーフローの危険性がない状況では、unchecked コードを使用することで、パフォーマンスを改善できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a3a51-110">Because checking for overflow takes time, the use of unchecked code in situations where there is no danger of overflow might improve performance.</span></span> <span data-ttu-id="a3a51-111">ただし、オーバーフローの可能性がある場合は、checked 環境を使用してください。</span><span class="sxs-lookup"><span data-stu-id="a3a51-111">However, if overflow is a possibility, a checked environment should be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3a51-112">例</span><span class="sxs-lookup"><span data-stu-id="a3a51-112">Example</span></span>  
 <span data-ttu-id="a3a51-113">この例では、`unchecked` キーワードの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a3a51-113">This sample shows how to use the `unchecked` keyword.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="a3a51-114">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="a3a51-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a3a51-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a3a51-115">See Also</span></span>  
 [<span data-ttu-id="a3a51-116">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="a3a51-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a3a51-117">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="a3a51-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a3a51-118">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="a3a51-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="a3a51-119">Checked と Unchecked</span><span class="sxs-lookup"><span data-stu-id="a3a51-119">Checked and Unchecked</span></span>](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
 [<span data-ttu-id="a3a51-120">checked</span><span class="sxs-lookup"><span data-stu-id="a3a51-120">checked</span></span>](../../../csharp/language-reference/keywords/checked.md)
