---
title: "^ 演算子 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4ccd32ea8abd8ca3252380083eafecad2b572ed7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="1d0d4-102">^ 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="1d0d4-102">^ Operator (C# Reference)</span></span>
<span data-ttu-id="1d0d4-103">整数型と `bool` には、2 項 `^` 演算子が事前定義されています。</span><span class="sxs-lookup"><span data-stu-id="1d0d4-103">Binary `^` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="1d0d4-104">整数型の場合、`^` はそのオペランドのビット演算排他的 OR を計算します。</span><span class="sxs-lookup"><span data-stu-id="1d0d4-104">For integral types, `^` computes the bitwise exclusive-OR of its operands.</span></span> <span data-ttu-id="1d0d4-105">`bool` オペランドの場合、`^` はそのオペランドの論理排他的 OR を計算します。つまり、そのオペランドの厳密に 1 つが `true` の場合およびその場合に限って、結果が `true` になります。</span><span class="sxs-lookup"><span data-stu-id="1d0d4-105">For `bool` operands, `^` computes the logical exclusive-or of its operands; that is, the result is `true` if and only if exactly one of its operands is `true`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d0d4-106">コメント</span><span class="sxs-lookup"><span data-stu-id="1d0d4-106">Remarks</span></span>  
 <span data-ttu-id="1d0d4-107">ユーザー定義型は `^` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="1d0d4-107">User-defined types can overload the `^` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="1d0d4-108">整数型に対する演算は、通常、列挙型で使用できます。</span><span class="sxs-lookup"><span data-stu-id="1d0d4-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d0d4-109">例</span><span class="sxs-lookup"><span data-stu-id="1d0d4-109">Example</span></span>  
 [!code-csharp[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]  
  
 <span data-ttu-id="1d0d4-110">前の例における `0xf8 ^ 0x3f` の計算では、16 進値の F8 と 3F に対応する次の 2 つのバイナリ値にビット演算排他的 OR が実行されます。</span><span class="sxs-lookup"><span data-stu-id="1d0d4-110">The computation of `0xf8 ^ 0x3f` in the previous example performs a bitwise exclusive-OR of the following two binary values, which correspond to the hexadecimal values F8 and 3F:</span></span>  
  
 `1111 1000`  
  
 `0011 1111`  
  
 <span data-ttu-id="1d0d4-111">排他的 OR の結果は `1100 0111` であり、16 進値の C7 です。</span><span class="sxs-lookup"><span data-stu-id="1d0d4-111">The result of the exclusive-OR is `1100 0111`, which is C7 in hexadecimal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d0d4-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d0d4-112">See Also</span></span>  
 [<span data-ttu-id="1d0d4-113">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="1d0d4-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1d0d4-114">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="1d0d4-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1d0d4-115">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="1d0d4-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
