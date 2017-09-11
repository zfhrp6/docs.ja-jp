---
title: "^ 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ^_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
caps.latest.revision: 19
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
ms.openlocfilehash: f081dd2979930404639638179444adc05dd462e1
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="98334-102">^ 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="98334-102">^ Operator (C# Reference)</span></span>
<span data-ttu-id="98334-103">整数型と `bool` には、2 項 `^` 演算子が事前定義されています。</span><span class="sxs-lookup"><span data-stu-id="98334-103">Binary `^` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="98334-104">整数型の場合、`^` はそのオペランドのビット演算排他的 OR を計算します。</span><span class="sxs-lookup"><span data-stu-id="98334-104">For integral types, `^` computes the bitwise exclusive-OR of its operands.</span></span> <span data-ttu-id="98334-105">`bool` オペランドの場合、`^` はそのオペランドの論理排他的 OR を計算します。つまり、そのオペランドの厳密に 1 つが `true` の場合およびその場合に限って、結果が `true` になります。</span><span class="sxs-lookup"><span data-stu-id="98334-105">For `bool` operands, `^` computes the logical exclusive-or of its operands; that is, the result is `true` if and only if exactly one of its operands is `true`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98334-106">コメント</span><span class="sxs-lookup"><span data-stu-id="98334-106">Remarks</span></span>  
 <span data-ttu-id="98334-107">ユーザー定義型は `^` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="98334-107">User-defined types can overload the `^` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="98334-108">整数型に対する演算は、通常、列挙型で使用できます。</span><span class="sxs-lookup"><span data-stu-id="98334-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98334-109">例</span><span class="sxs-lookup"><span data-stu-id="98334-109">Example</span></span>  
 <span data-ttu-id="98334-110">[!code-cs[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="98334-110">[!code-cs[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]</span></span>  
  
 <span data-ttu-id="98334-111">前の例における `0xf8 ^ 0x3f` の計算では、16 進値の F8 と 3F に対応する次の 2 つのバイナリ値にビット演算排他的 OR が実行されます。</span><span class="sxs-lookup"><span data-stu-id="98334-111">The computation of `0xf8 ^ 0x3f` in the previous example performs a bitwise exclusive-OR of the following two binary values, which correspond to the hexadecimal values F8 and 3F:</span></span>  
  
 `1111 1000`  
  
 `0011 1111`  
  
 <span data-ttu-id="98334-112">排他的 OR の結果は `1100 0111` であり、16 進値の C7 です。</span><span class="sxs-lookup"><span data-stu-id="98334-112">The result of the exclusive-OR is `1100 0111`, which is C7 in hexadecimal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98334-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="98334-113">See Also</span></span>  
 <span data-ttu-id="98334-114">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="98334-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="98334-115">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="98334-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="98334-116">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="98334-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

