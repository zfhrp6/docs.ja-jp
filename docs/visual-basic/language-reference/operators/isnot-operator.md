---
title: IsNot 演算子 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 969fdebdf15a1f779075c58616ccd16c64976a35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="c42d0-102">IsNot 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c42d0-102">IsNot Operator (Visual Basic)</span></span>
<span data-ttu-id="c42d0-103">2 つのオブジェクト参照変数を比較します。</span><span class="sxs-lookup"><span data-stu-id="c42d0-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c42d0-104">構文</span><span class="sxs-lookup"><span data-stu-id="c42d0-104">Syntax</span></span>  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a><span data-ttu-id="c42d0-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="c42d0-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="c42d0-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="c42d0-106">Required.</span></span> <span data-ttu-id="c42d0-107">`Boolean` 値。</span><span class="sxs-lookup"><span data-stu-id="c42d0-107">A `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="c42d0-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="c42d0-108">Required.</span></span> <span data-ttu-id="c42d0-109">どの`Object`変数または式。</span><span class="sxs-lookup"><span data-stu-id="c42d0-109">Any `Object` variable or expression.</span></span>  
  
 `object2`  
 <span data-ttu-id="c42d0-110">必須です。</span><span class="sxs-lookup"><span data-stu-id="c42d0-110">Required.</span></span> <span data-ttu-id="c42d0-111">どの`Object`変数または式。</span><span class="sxs-lookup"><span data-stu-id="c42d0-111">Any `Object` variable or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c42d0-112">コメント</span><span class="sxs-lookup"><span data-stu-id="c42d0-112">Remarks</span></span>  
 <span data-ttu-id="c42d0-113">`IsNot`演算子は、次の 2 つのオブジェクト参照が別のオブジェクトを参照してかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="c42d0-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="c42d0-114">ただし、値の比較は実行しません。</span><span class="sxs-lookup"><span data-stu-id="c42d0-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="c42d0-115">場合`object1`と`object2`正確な同じオブジェクト インスタンスをどちらも参照してください`result`は`False`以外の場合は一致しない場合、`result`は`True`します。</span><span class="sxs-lookup"><span data-stu-id="c42d0-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>  
  
 <span data-ttu-id="c42d0-116">`IsNot`逆の`Is`演算子。</span><span class="sxs-lookup"><span data-stu-id="c42d0-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="c42d0-117">利点は、`IsNot`は避けることができますを組み合わせて`Not`と`Is`、読みにくくなることができます。</span><span class="sxs-lookup"><span data-stu-id="c42d0-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>  
  
 <span data-ttu-id="c42d0-118">使用することができます、`Is`と`IsNot`事前バインドおよび遅延バインディングの両方のオブジェクトをテストする演算子です。</span><span class="sxs-lookup"><span data-stu-id="c42d0-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c42d0-119">`IsNot`から返される式を比較する演算子を使用することはできません、`TypeOf`演算子。</span><span class="sxs-lookup"><span data-stu-id="c42d0-119">The `IsNot` operator cannot be used to compare expressions returned from the `TypeOf` operator.</span></span> <span data-ttu-id="c42d0-120">代わりに、使用する必要があります、`Not`と`Is`演算子。</span><span class="sxs-lookup"><span data-stu-id="c42d0-120">Instead, you must use the `Not` and `Is` operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c42d0-121">例</span><span class="sxs-lookup"><span data-stu-id="c42d0-121">Example</span></span>  
 <span data-ttu-id="c42d0-122">次のコード例では、両方は使用して、`Is`演算子および`IsNot`を同じ比較を実行する演算子です。</span><span class="sxs-lookup"><span data-stu-id="c42d0-122">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>  
  
 [!code-vb[VbVbalrOperators#29](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isnot-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c42d0-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="c42d0-123">See Also</span></span>  
 [<span data-ttu-id="c42d0-124">Is 演算子</span><span class="sxs-lookup"><span data-stu-id="c42d0-124">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="c42d0-125">TypeOf 演算子</span><span class="sxs-lookup"><span data-stu-id="c42d0-125">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [<span data-ttu-id="c42d0-126">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="c42d0-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="c42d0-127">方法: 2 つのオブジェクトが等しいかどうかをテストする</span><span class="sxs-lookup"><span data-stu-id="c42d0-127">How to: Test Whether Two Objects Are the Same</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
