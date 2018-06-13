---
title: ^ 演算子 (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
ms.openlocfilehash: 5cc3cd2cfc932646e5b2dd6ec034555b07582379
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33271251"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="955e1-102">^ 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="955e1-102">^ Operator (C# Reference)</span></span>
<span data-ttu-id="955e1-103">整数型と `bool` には、2 項 `^` 演算子が事前定義されています。</span><span class="sxs-lookup"><span data-stu-id="955e1-103">Binary `^` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="955e1-104">整数型の場合、`^` はそのオペランドのビット演算排他的 OR を計算します。</span><span class="sxs-lookup"><span data-stu-id="955e1-104">For integral types, `^` computes the bitwise exclusive-OR of its operands.</span></span> <span data-ttu-id="955e1-105">`bool` オペランドの場合、`^` はそのオペランドの論理排他的 OR を計算します。つまり、そのオペランドの厳密に 1 つが `true` の場合およびその場合に限って、結果が `true` になります。</span><span class="sxs-lookup"><span data-stu-id="955e1-105">For `bool` operands, `^` computes the logical exclusive-or of its operands; that is, the result is `true` if and only if exactly one of its operands is `true`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="955e1-106">コメント</span><span class="sxs-lookup"><span data-stu-id="955e1-106">Remarks</span></span>  
 <span data-ttu-id="955e1-107">ユーザー定義型は `^` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="955e1-107">User-defined types can overload the `^` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="955e1-108">整数型に対する演算は、通常、列挙型で使用できます。</span><span class="sxs-lookup"><span data-stu-id="955e1-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="955e1-109">例</span><span class="sxs-lookup"><span data-stu-id="955e1-109">Example</span></span>  
 [!code-csharp[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]  
  
 <span data-ttu-id="955e1-110">前の例における `0xf8 ^ 0x3f` の計算では、16 進値の F8 と 3F に対応する次の 2 つのバイナリ値にビット演算排他的 OR が実行されます。</span><span class="sxs-lookup"><span data-stu-id="955e1-110">The computation of `0xf8 ^ 0x3f` in the previous example performs a bitwise exclusive-OR of the following two binary values, which correspond to the hexadecimal values F8 and 3F:</span></span>  
  
 `1111 1000`  
  
 `0011 1111`  
  
 <span data-ttu-id="955e1-111">排他的 OR の結果は `1100 0111` であり、16 進値の C7 です。</span><span class="sxs-lookup"><span data-stu-id="955e1-111">The result of the exclusive-OR is `1100 0111`, which is C7 in hexadecimal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="955e1-112">参照</span><span class="sxs-lookup"><span data-stu-id="955e1-112">See Also</span></span>  
 [<span data-ttu-id="955e1-113">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="955e1-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="955e1-114">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="955e1-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="955e1-115">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="955e1-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
