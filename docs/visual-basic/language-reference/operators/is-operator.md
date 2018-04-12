---
title: Is 演算子 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4b1f3f0fa1fd782550c08c816f47b7541399198e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="58af6-102">Is 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58af6-102">Is Operator (Visual Basic)</span></span>
<span data-ttu-id="58af6-103">2 つのオブジェクト参照変数を比較します。</span><span class="sxs-lookup"><span data-stu-id="58af6-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58af6-104">構文</span><span class="sxs-lookup"><span data-stu-id="58af6-104">Syntax</span></span>  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a><span data-ttu-id="58af6-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="58af6-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="58af6-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="58af6-106">Required.</span></span> <span data-ttu-id="58af6-107">どの`Boolean`値。</span><span class="sxs-lookup"><span data-stu-id="58af6-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="58af6-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="58af6-108">Required.</span></span> <span data-ttu-id="58af6-109">どの`Object`名。</span><span class="sxs-lookup"><span data-stu-id="58af6-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="58af6-110">必須です。</span><span class="sxs-lookup"><span data-stu-id="58af6-110">Required.</span></span> <span data-ttu-id="58af6-111">どの`Object`名。</span><span class="sxs-lookup"><span data-stu-id="58af6-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58af6-112">コメント</span><span class="sxs-lookup"><span data-stu-id="58af6-112">Remarks</span></span>  
 <span data-ttu-id="58af6-113">`Is`演算子は、2 つのオブジェクト参照が同じオブジェクトを参照してかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="58af6-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="58af6-114">ただし、値の比較は実行しません。</span><span class="sxs-lookup"><span data-stu-id="58af6-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="58af6-115">場合`object1`と`object2`正確な同じオブジェクト インスタンスをどちらも参照してください`result`は`True`以外の場合は一致しない場合、`result`は`False`します。</span><span class="sxs-lookup"><span data-stu-id="58af6-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>  
  
 <span data-ttu-id="58af6-116">`Is`使用することもできます、`TypeOf`キーワードを`TypeOf`しています.`Is`式で、オブジェクト変数のデータ型と互換性があるかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="58af6-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58af6-117">`Is`キーワードでも使用、[を選択しています.ステートメントの case](../../../visual-basic/language-reference/statements/select-case-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="58af6-117">The `Is` keyword is also used in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="58af6-118">例</span><span class="sxs-lookup"><span data-stu-id="58af6-118">Example</span></span>  
 <span data-ttu-id="58af6-119">次の例では、`Is`オブジェクト参照のペアを比較する演算子です。</span><span class="sxs-lookup"><span data-stu-id="58af6-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="58af6-120">結果に割り当てられている、 `Boolean` 2 つのオブジェクトが同一かどうかを表す値です。</span><span class="sxs-lookup"><span data-stu-id="58af6-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>  
  
 [!code-vb[VbVbalrOperators#27](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/is-operator_1.vb)]  
  
 <span data-ttu-id="58af6-121">前の例を示しています、としてを使用して、`Is`両方をテストする演算子が事前バインドおよび遅延バインドされたオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="58af6-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58af6-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="58af6-122">See Also</span></span>  
 [<span data-ttu-id="58af6-123">TypeOf 演算子</span><span class="sxs-lookup"><span data-stu-id="58af6-123">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [<span data-ttu-id="58af6-124">IsNot 演算子</span><span class="sxs-lookup"><span data-stu-id="58af6-124">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="58af6-125">Visual Basic における比較演算子</span><span class="sxs-lookup"><span data-stu-id="58af6-125">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="58af6-126">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="58af6-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="58af6-127">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="58af6-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="58af6-128">演算子および式</span><span class="sxs-lookup"><span data-stu-id="58af6-128">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
