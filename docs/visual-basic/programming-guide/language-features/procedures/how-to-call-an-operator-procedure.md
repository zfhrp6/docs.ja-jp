---
title: '方法: 演算子プロシージャを呼び出す (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedure calls [Visual Basic], operator overloading
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- overloaded operators [Visual Basic], calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
ms.openlocfilehash: b1dc4477daa4ceb9dfc6a9a6ab3f041e68011acd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649969"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="081e1-102">方法: 演算子プロシージャを呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="081e1-102">How to: Call an Operator Procedure (Visual Basic)</span></span>
<span data-ttu-id="081e1-103">演算子プロシージャを呼び出すには、式で演算子のシンボルを使用します。</span><span class="sxs-lookup"><span data-stu-id="081e1-103">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="081e1-104">場合は、変換演算子を呼び出す、 [CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)に値を別の 1 つのデータ型に変換します。</span><span class="sxs-lookup"><span data-stu-id="081e1-104">In the case of a conversion operator, you call the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="081e1-105">演算子プロシージャを明示的に呼び出すことはありません。</span><span class="sxs-lookup"><span data-stu-id="081e1-105">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="081e1-106">同様に、演算子を使用する、または`CType`関数、代入ステートメントまたは式、演算子を通常使用するのと同様にします。</span><span class="sxs-lookup"><span data-stu-id="081e1-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> <span data-ttu-id="081e1-107">Visual Basic では、演算子プロシージャ呼び出しを行います。</span><span class="sxs-lookup"><span data-stu-id="081e1-107">Visual Basic makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="081e1-108">クラスまたは構造体で演算子を定義とも呼びます*オーバー ロード*演算子。</span><span class="sxs-lookup"><span data-stu-id="081e1-108">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="081e1-109">演算子プロシージャを呼び出しています</span><span class="sxs-lookup"><span data-stu-id="081e1-109">To call an operator procedure</span></span>  
  
1.  <span data-ttu-id="081e1-110">通常の方法で、式で演算子のシンボルを使用します。</span><span class="sxs-lookup"><span data-stu-id="081e1-110">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2.  <span data-ttu-id="081e1-111">オペランドのデータ型が演算子の場合、正しい順序では適切であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="081e1-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3.  <span data-ttu-id="081e1-112">演算子は、期待どおりに、式の値に作用します。</span><span class="sxs-lookup"><span data-stu-id="081e1-112">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="081e1-113">変換演算子プロシージャを呼び出しています</span><span class="sxs-lookup"><span data-stu-id="081e1-113">To call a conversion operator procedure</span></span>  
  
1.  <span data-ttu-id="081e1-114">使用して`CType`式の内部です。</span><span class="sxs-lookup"><span data-stu-id="081e1-114">Use `CType` inside an expression.</span></span>  
  
2.  <span data-ttu-id="081e1-115">オペランドのデータ型は、変換して、正しい順序で適切なことを確認します。</span><span class="sxs-lookup"><span data-stu-id="081e1-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3.  <span data-ttu-id="081e1-116">`CType` 変換演算子プロシージャの呼び出しを変換後の値を返します。</span><span class="sxs-lookup"><span data-stu-id="081e1-116">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="081e1-117">例</span><span class="sxs-lookup"><span data-stu-id="081e1-117">Example</span></span>  
 <span data-ttu-id="081e1-118">次の例では、2 つ作成されます<xref:System.TimeSpan>構造体を加算してを 3 つ目の結果を格納<xref:System.TimeSpan>構造体。</span><span class="sxs-lookup"><span data-stu-id="081e1-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="081e1-119"><xref:System.TimeSpan>構造体は、いくつかの標準的な演算子をオーバー ロードする演算子プロシージャを定義します。</span><span class="sxs-lookup"><span data-stu-id="081e1-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 [!code-vb[VbVbcnProcedures#29](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]  
  
 <span data-ttu-id="081e1-120"><xref:System.TimeSpan>標準をオーバー ロード`+`演算子を前の例では演算子プロシージャの値を計算するとき`combinedSpan`です。</span><span class="sxs-lookup"><span data-stu-id="081e1-120">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="081e1-121">メッセージ交換演算子プロシージャの呼び出しの例は、次を参照してください。[する方法: クラスにその定義の演算子を使用して](./how-to-use-a-class-that-defines-operators.md)です。</span><span class="sxs-lookup"><span data-stu-id="081e1-121">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="081e1-122">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="081e1-122">Compiling the Code</span></span>  
 <span data-ttu-id="081e1-123">使用する演算子を定義クラスまたは構造体を使用していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="081e1-123">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="081e1-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="081e1-124">See Also</span></span>  
 [<span data-ttu-id="081e1-125">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="081e1-125">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="081e1-126">方法 : 演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="081e1-126">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="081e1-127">方法 : 変換演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="081e1-127">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="081e1-128">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="081e1-128">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="081e1-129">Widening</span><span class="sxs-lookup"><span data-stu-id="081e1-129">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="081e1-130">Narrowing</span><span class="sxs-lookup"><span data-stu-id="081e1-130">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="081e1-131">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="081e1-131">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="081e1-132">方法 : 構造体を宣言する</span><span class="sxs-lookup"><span data-stu-id="081e1-132">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="081e1-133">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="081e1-133">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="081e1-134">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="081e1-134">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
