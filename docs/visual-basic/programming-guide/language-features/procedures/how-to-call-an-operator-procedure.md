---
title: "方法: 演算子プロシージャ (Visual Basic) を呼び出す |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- operator procedures, calling
- procedures, operator
- procedure calls, operator overloading
- syntax, Operator procedures
- operators [Visual Basic], overloading
- return values, Operator procedures
- overloaded operators, calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: cd85a14a6f5534e90497268134f4b2b0cc292249
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="487f0-102">方法: 演算子プロシージャを呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="487f0-102">How to: Call an Operator Procedure (Visual Basic)</span></span>
<span data-ttu-id="487f0-103">演算子プロシージャを呼び出すには、式で演算子のシンボルを使用します。</span><span class="sxs-lookup"><span data-stu-id="487f0-103">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="487f0-104">場合、変換演算子を呼び出す、 [CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)に値を別の&1; つのデータ型に変換します。</span><span class="sxs-lookup"><span data-stu-id="487f0-104">In the case of a conversion operator, you call the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="487f0-105">演算子プロシージャを明示的に呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="487f0-105">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="487f0-106">同様に、演算子を使用する、または`CType`関数、代入ステートメント、または式、演算子を使用すると、通常は同じようにします。</span><span class="sxs-lookup"><span data-stu-id="487f0-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="487f0-107">演算子プロシージャの呼び出しを使用します。</span><span class="sxs-lookup"><span data-stu-id="487f0-107"> makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="487f0-108">クラスまたは構造体で、演算子を定義することと呼ばれる*オーバー ロード*演算子。</span><span class="sxs-lookup"><span data-stu-id="487f0-108">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="487f0-109">演算子プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="487f0-109">To call an operator procedure</span></span>  
  
1.  <span data-ttu-id="487f0-110">通常の方法で、式の中で演算子のシンボルを使用します。</span><span class="sxs-lookup"><span data-stu-id="487f0-110">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2.  <span data-ttu-id="487f0-111">オペランドのデータ型が適切な演算子の場合と、正しい順序であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="487f0-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3.  <span data-ttu-id="487f0-112">演算子は、期待どおりに、式の値に作用します。</span><span class="sxs-lookup"><span data-stu-id="487f0-112">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="487f0-113">変換演算子プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="487f0-113">To call a conversion operator procedure</span></span>  
  
1.  <span data-ttu-id="487f0-114">使用`CType`式の内部です。</span><span class="sxs-lookup"><span data-stu-id="487f0-114">Use `CType` inside an expression.</span></span>  
  
2.  <span data-ttu-id="487f0-115">オペランドのデータ型が適切な変換して、正しい順序であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="487f0-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3.  <span data-ttu-id="487f0-116">`CType`変換演算子プロシージャの呼び出しを変換後の値を返します。</span><span class="sxs-lookup"><span data-stu-id="487f0-116">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="487f0-117">例</span><span class="sxs-lookup"><span data-stu-id="487f0-117">Example</span></span>  
 <span data-ttu-id="487f0-118">次の例では、2 つ作成されます<xref:System.TimeSpan>構造体、それらを加算、および&3; つ目の結果を格納<xref:System.TimeSpan>構造体</xref:System.TimeSpan></xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="487f0-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="487f0-119"><xref:System.TimeSpan>構造体がいくつかの標準的な演算子をオーバー ロードする演算子プロシージャを定義します</xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="487f0-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 <span data-ttu-id="487f0-120">[!code-vb[VbVbcnProcedures #&29;](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="487f0-120">[!code-vb[VbVbcnProcedures#29](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]</span></span>  
  
 <span data-ttu-id="487f0-121"><xref:System.TimeSpan>、標準のオーバー ロード`+`演算子で、前の例では演算子プロシージャの値を計算するとき`combinedSpan`</xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="487f0-121">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="487f0-122">メッセージ交換演算子プロシージャの呼び出しの例は、次を参照してください。[方法: クラスを定義演算子を使用して](./how-to-use-a-class-that-defines-operators.md)します。</span><span class="sxs-lookup"><span data-stu-id="487f0-122">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="487f0-123">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="487f0-123">Compiling the Code</span></span>  
 <span data-ttu-id="487f0-124">使用する演算子を定義、クラスまたは構造体を使用していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="487f0-124">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="487f0-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="487f0-125">See Also</span></span>  
 <span data-ttu-id="487f0-126">[演算子プロシージャ](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="487f0-126">[Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="487f0-127"> [方法: 演算子を定義](./how-to-define-an-operator.md) </span><span class="sxs-lookup"><span data-stu-id="487f0-127"> [How to: Define an Operator](./how-to-define-an-operator.md) </span></span>  
<span data-ttu-id="487f0-128"> [方法: 変換演算子を定義します。](./how-to-define-a-conversion-operator.md) </span><span class="sxs-lookup"><span data-stu-id="487f0-128"> [How to: Define a Conversion Operator](./how-to-define-a-conversion-operator.md) </span></span>  
<span data-ttu-id="487f0-129"> [Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md) </span><span class="sxs-lookup"><span data-stu-id="487f0-129"> [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md) </span></span>  
<span data-ttu-id="487f0-130"> [拡大変換](../../../../visual-basic/language-reference/modifiers/widening.md) </span><span class="sxs-lookup"><span data-stu-id="487f0-130"> [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) </span></span>  
<span data-ttu-id="487f0-131"> [縮小変換](../../../../visual-basic/language-reference/modifiers/narrowing.md) </span><span class="sxs-lookup"><span data-stu-id="487f0-131"> [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md) </span></span>  
<span data-ttu-id="487f0-132"> [Structure ステートメント](../../../../visual-basic/language-reference/statements/structure-statement.md) </span><span class="sxs-lookup"><span data-stu-id="487f0-132"> [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md) </span></span>  
<span data-ttu-id="487f0-133"> [方法: 構造体を宣言](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md) </span><span class="sxs-lookup"><span data-stu-id="487f0-133"> [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md) </span></span>  
<span data-ttu-id="487f0-134"> [明示的および暗黙的な変換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="487f0-134"> [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span></span>  
<span data-ttu-id="487f0-135"> [拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)</span><span class="sxs-lookup"><span data-stu-id="487f0-135"> [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)</span></span>
