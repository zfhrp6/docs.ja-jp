---
title: "unchecked (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
dev_langs:
- CSharp
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
caps.latest.revision: 23
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
ms.openlocfilehash: 5878a2412e6c85da85b1a3b8c2a8255b51e67137
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="unchecked-c-reference"></a><span data-ttu-id="32f63-102">unchecked (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="32f63-102">unchecked (C# Reference)</span></span>
<span data-ttu-id="32f63-103">`unchecked` キーワードは、整数型の算術演算と変換に対してオーバーフロー チェックを抑制するために使用します。</span><span class="sxs-lookup"><span data-stu-id="32f63-103">The `unchecked` keyword is used to suppress overflow-checking for integral-type arithmetic operations and conversions.</span></span>  
  
 <span data-ttu-id="32f63-104">unchecked コンテキストでは、式が変換先の型の範囲外の値を生成した場合に、オーバーフローが検出されません。</span><span class="sxs-lookup"><span data-stu-id="32f63-104">In an unchecked context, if an expression produces a value that is outside the range of the destination type, the overflow is not flagged.</span></span> <span data-ttu-id="32f63-105">たとえば、次の例では、`unchecked` ブロックまたは式で計算が行われるため、結果が integer に対して大きすぎるという事実が無視され、`int1` には-2,147,483,639 の値が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="32f63-105">For example, because the calculation in the following example is performed in an `unchecked` block or expression, the fact that the result is too large for an integer is ignored, and `int1` is assigned the value -2,147,483,639.</span></span>  
  
 <span data-ttu-id="32f63-106">[!code-cs[csrefKeywordsChecked#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="32f63-106">[!code-cs[csrefKeywordsChecked#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_1.cs)]</span></span>  
  
 <span data-ttu-id="32f63-107">`unchecked` 環境が削除されると、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="32f63-107">If the `unchecked` environment is removed, a compilation error occurs.</span></span> <span data-ttu-id="32f63-108">式のすべての用語が定数なので、コンパイル時にはオーバーフローを検出できます。</span><span class="sxs-lookup"><span data-stu-id="32f63-108">The overflow can be detected at compile time because all the terms of the expression are constants.</span></span>  
  
 <span data-ttu-id="32f63-109">非定数の用語を含む式は、実行時およびコンパイル時に既定ではチェックされません。</span><span class="sxs-lookup"><span data-stu-id="32f63-109">Expressions that contain non-constant terms are unchecked by default at compile time and run time.</span></span> <span data-ttu-id="32f63-110">checked 環境を有効にする方法については、「[checked](../../../csharp/language-reference/keywords/checked.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="32f63-110">See [checked](../../../csharp/language-reference/keywords/checked.md) for information about enabling a checked environment.</span></span>  
  
 <span data-ttu-id="32f63-111">オーバーフローのチェックには時間がかかるため、オーバーフローの危険性がない状況では、unchecked コードを使用することで、パフォーマンスを改善できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="32f63-111">Because checking for overflow takes time, the use of unchecked code in situations where there is no danger of overflow might improve performance.</span></span> <span data-ttu-id="32f63-112">ただし、オーバーフローの可能性がある場合は、checked 環境を使用してください。</span><span class="sxs-lookup"><span data-stu-id="32f63-112">However, if overflow is a possibility, a checked environment should be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32f63-113">例</span><span class="sxs-lookup"><span data-stu-id="32f63-113">Example</span></span>  
 <span data-ttu-id="32f63-114">この例では、`unchecked` キーワードの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="32f63-114">This sample shows how to use the `unchecked` keyword.</span></span>  
  
 <span data-ttu-id="32f63-115">[!code-cs[csrefKeywordsChecked#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="32f63-115">[!code-cs[csrefKeywordsChecked#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="32f63-116">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="32f63-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="32f63-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="32f63-117">See Also</span></span>  
 <span data-ttu-id="32f63-118">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="32f63-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="32f63-119">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="32f63-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="32f63-120">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="32f63-120">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="32f63-121">[Checked と Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md) </span><span class="sxs-lookup"><span data-stu-id="32f63-121">[Checked and Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md) </span></span>  
 [<span data-ttu-id="32f63-122">checked</span><span class="sxs-lookup"><span data-stu-id="32f63-122">checked</span></span>](../../../csharp/language-reference/keywords/checked.md)

