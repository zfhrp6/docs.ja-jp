---
title: '&amp;演算子 (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76c8fc52a518dfe7850a5680b7d4f06f3d09bf73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="f1200-102">&amp;演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1200-102">&amp; Operator (Visual Basic)</span></span>
<span data-ttu-id="f1200-103">2 つの式の文字列の連結を生成します。</span><span class="sxs-lookup"><span data-stu-id="f1200-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1200-104">構文</span><span class="sxs-lookup"><span data-stu-id="f1200-104">Syntax</span></span>  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="f1200-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="f1200-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="f1200-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="f1200-106">Required.</span></span> <span data-ttu-id="f1200-107">どの`String`または`Object`変数。</span><span class="sxs-lookup"><span data-stu-id="f1200-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="f1200-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="f1200-108">Required.</span></span> <span data-ttu-id="f1200-109">データ型に拡大変換を持つ任意の式`String`です。</span><span class="sxs-lookup"><span data-stu-id="f1200-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="f1200-110">必須です。</span><span class="sxs-lookup"><span data-stu-id="f1200-110">Required.</span></span> <span data-ttu-id="f1200-111">データ型に拡大変換を持つ任意の式`String`です。</span><span class="sxs-lookup"><span data-stu-id="f1200-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1200-112">コメント</span><span class="sxs-lookup"><span data-stu-id="f1200-112">Remarks</span></span>  
 <span data-ttu-id="f1200-113">データ型の場合`expression1`または`expression2`は`String`に拡大変換が`String`に変換されます`String`です。</span><span class="sxs-lookup"><span data-stu-id="f1200-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="f1200-114">かどうか、データ型のいずれかが拡大変換されないに`String`、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="f1200-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="f1200-115">データ型`result`は`String`します。</span><span class="sxs-lookup"><span data-stu-id="f1200-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="f1200-116">1 つまたは両方の式が評価される場合[Nothing](../../../visual-basic/language-reference/nothing.md)またはの値が<xref:System.DBNull.Value?displayProperty=nameWithType>の値を文字列として扱われます""です。</span><span class="sxs-lookup"><span data-stu-id="f1200-116">If one or both expressions evaluate to [Nothing](../../../visual-basic/language-reference/nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1200-117">`&`演算子を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。</span><span class="sxs-lookup"><span data-stu-id="f1200-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="f1200-118">コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、再定義された動作を理解することを確認します。</span><span class="sxs-lookup"><span data-stu-id="f1200-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f1200-119">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="f1200-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1200-120">型として変数を識別する、アンパサンド (&) 文字を使用することができますも`Long`します。</span><span class="sxs-lookup"><span data-stu-id="f1200-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="f1200-121">詳細については、次を参照してください。[型文字](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)です。</span><span class="sxs-lookup"><span data-stu-id="f1200-121">For more information, see [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1200-122">例</span><span class="sxs-lookup"><span data-stu-id="f1200-122">Example</span></span>  
 <span data-ttu-id="f1200-123">この例では、`&`演算子を強制的に文字列を連結します。</span><span class="sxs-lookup"><span data-stu-id="f1200-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="f1200-124">結果は、2 つの文字列オペランドの連結を表す文字列値です。</span><span class="sxs-lookup"><span data-stu-id="f1200-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f1200-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1200-125">See Also</span></span>  
 [<span data-ttu-id="f1200-126">& = 演算子</span><span class="sxs-lookup"><span data-stu-id="f1200-126">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [<span data-ttu-id="f1200-127">連結演算子</span><span class="sxs-lookup"><span data-stu-id="f1200-127">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [<span data-ttu-id="f1200-128">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="f1200-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="f1200-129">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="f1200-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="f1200-130">Visual Basic の連結演算子</span><span class="sxs-lookup"><span data-stu-id="f1200-130">Concatenation Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
