---
title: "TypeOf 演算子 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- TypeOf
- vb.TypeOf
helpviewer_keywords:
- types [Visual Basic], compatible
- comparison operators [Visual Basic]
- TypeOf...Is expression
- data types [Visual Basic], compatible
- TypeOf operator [Visual Basic]
- compatible data types [Visual Basic]
ms.assetid: 33f65296-659a-4b9a-9a29-c2a91cff68b2
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 51bd2af7af28aa229fa62770c5b92d31e461333b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="typeof-operator-visual-basic"></a><span data-ttu-id="711cf-102">TypeOf 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="711cf-102">TypeOf Operator (Visual Basic)</span></span>
<span data-ttu-id="711cf-103">オブジェクト参照変数をデータ型と比較します。</span><span class="sxs-lookup"><span data-stu-id="711cf-103">Compares an object reference variable to a data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="711cf-104">構文</span><span class="sxs-lookup"><span data-stu-id="711cf-104">Syntax</span></span>  
  
```  
result = TypeOf objectexpression Is typename  
```  
  
```  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a><span data-ttu-id="711cf-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="711cf-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="711cf-106">必須。</span><span class="sxs-lookup"><span data-stu-id="711cf-106">Returned.</span></span> <span data-ttu-id="711cf-107">`Boolean` 値。</span><span class="sxs-lookup"><span data-stu-id="711cf-107">A `Boolean` value.</span></span>  
  
 `objectexpression`  
 <span data-ttu-id="711cf-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="711cf-108">Required.</span></span> <span data-ttu-id="711cf-109">参照型に評価される任意の式。</span><span class="sxs-lookup"><span data-stu-id="711cf-109">Any expression that evaluates to a reference type.</span></span>  
  
 `typename`  
 <span data-ttu-id="711cf-110">必須です。</span><span class="sxs-lookup"><span data-stu-id="711cf-110">Required.</span></span> <span data-ttu-id="711cf-111">任意のデータ型名。</span><span class="sxs-lookup"><span data-stu-id="711cf-111">Any data type name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="711cf-112">コメント</span><span class="sxs-lookup"><span data-stu-id="711cf-112">Remarks</span></span>  
 <span data-ttu-id="711cf-113">`TypeOf` 演算子は、`objectexpression` の実行時の型が `typename` と互換性があるかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="711cf-113">The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`.</span></span> <span data-ttu-id="711cf-114">互換性は、`typename` の型のカテゴリに依存します。</span><span class="sxs-lookup"><span data-stu-id="711cf-114">The compatibility depends on the type category of `typename`.</span></span> <span data-ttu-id="711cf-115">互換性を決定する方法を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="711cf-115">The following table shows how compatibility is determined.</span></span>  
  
|<span data-ttu-id="711cf-116">`typename` の型のカテゴリ</span><span class="sxs-lookup"><span data-stu-id="711cf-116">Type category of `typename`</span></span>|<span data-ttu-id="711cf-117">互換性の条件</span><span class="sxs-lookup"><span data-stu-id="711cf-117">Compatibility criterion</span></span>|  
|---------------------------------|-----------------------------|  
|<span data-ttu-id="711cf-118">クラス</span><span class="sxs-lookup"><span data-stu-id="711cf-118">Class</span></span>|<span data-ttu-id="711cf-119">`objectexpression` が `typename` 型である、または `typename` を継承する</span><span class="sxs-lookup"><span data-stu-id="711cf-119">`objectexpression` is of type `typename` or inherits from `typename`</span></span>|  
|<span data-ttu-id="711cf-120">構造体</span><span class="sxs-lookup"><span data-stu-id="711cf-120">Structure</span></span>|<span data-ttu-id="711cf-121">`objectexpression` が `typename` 型である</span><span class="sxs-lookup"><span data-stu-id="711cf-121">`objectexpression` is of type `typename`</span></span>|  
|<span data-ttu-id="711cf-122">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="711cf-122">Interface</span></span>|<span data-ttu-id="711cf-123">`objectexpression` が `typename` を実装する、または `typename` を実装するクラスを継承する</span><span class="sxs-lookup"><span data-stu-id="711cf-123">`objectexpression` implements `typename` or inherits from a class that implements `typename`</span></span>|  
  
 <span data-ttu-id="711cf-124">`objectexpression` の実行時の型が互換性の条件を満たす場合、`result` は `True` です。</span><span class="sxs-lookup"><span data-stu-id="711cf-124">If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`.</span></span> <span data-ttu-id="711cf-125">それ以外の場合、`result` は `False` です。</span><span class="sxs-lookup"><span data-stu-id="711cf-125">Otherwise, `result` is `False`.</span></span>  <span data-ttu-id="711cf-126">`objectexpression` が null の場合、`TypeOf`...`Is` は `False` を返し、...`IsNot` は `True` を返します。</span><span class="sxs-lookup"><span data-stu-id="711cf-126">If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.</span></span>  
  
 <span data-ttu-id="711cf-127">`TypeOf` は、常に `Is` キーワードと共に `TypeOf`...`Is` 式を構築するか、または `IsNot` キーワードと共に `TypeOf`...`IsNot` 式を構築します。</span><span class="sxs-lookup"><span data-stu-id="711cf-127">`TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="711cf-128">例</span><span class="sxs-lookup"><span data-stu-id="711cf-128">Example</span></span>  
 <span data-ttu-id="711cf-129">次の例では、`TypeOf`...`Is` 式でさまざまなデータ型を使用して、2 つのオブジェクト参照変数の型の互換性をテストしています。</span><span class="sxs-lookup"><span data-stu-id="711cf-129">The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.</span></span>  
  
 [!code-vb[VbVbalrOperators#39](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/typeof-operator_1.vb)]  
  
 <span data-ttu-id="711cf-130">変数 `refInteger` は、実行時の型 `Integer` を持ちます。</span><span class="sxs-lookup"><span data-stu-id="711cf-130">The variable `refInteger` has a run-time type of `Integer`.</span></span> <span data-ttu-id="711cf-131">`Integer` と互換性がありますが、`Double` との互換性はありません。</span><span class="sxs-lookup"><span data-stu-id="711cf-131">It is compatible with `Integer` but not with `Double`.</span></span> <span data-ttu-id="711cf-132">変数 `refForm` は、実行時の型 <xref:System.Windows.Forms.Form> を持ちます。</span><span class="sxs-lookup"><span data-stu-id="711cf-132">The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="711cf-133">この変数は、<xref:System.Windows.Forms.Form> (同じ型)、<xref:System.Windows.Forms.Control> (<xref:System.Windows.Forms.Form> は <xref:System.Windows.Forms.Control> を継承する)、および <xref:System.ComponentModel.IComponent> (<xref:System.Windows.Forms.Form> は <xref:System.ComponentModel.IComponent> を実装する <xref:System.ComponentModel.Component> を継承する) と互換性があります。</span><span class="sxs-lookup"><span data-stu-id="711cf-133">It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="711cf-134">ただし、`refForm` には <xref:System.Windows.Forms.Label> との互換性はありません。</span><span class="sxs-lookup"><span data-stu-id="711cf-134">However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="711cf-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="711cf-135">See Also</span></span>  
 [<span data-ttu-id="711cf-136">Is 演算子</span><span class="sxs-lookup"><span data-stu-id="711cf-136">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="711cf-137">IsNot 演算子</span><span class="sxs-lookup"><span data-stu-id="711cf-137">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="711cf-138">Visual Basic における比較演算子</span><span class="sxs-lookup"><span data-stu-id="711cf-138">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="711cf-139">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="711cf-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="711cf-140">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="711cf-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="711cf-141">演算子および式</span><span class="sxs-lookup"><span data-stu-id="711cf-141">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
