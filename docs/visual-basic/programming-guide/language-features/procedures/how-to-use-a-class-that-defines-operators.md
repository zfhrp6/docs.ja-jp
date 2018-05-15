---
title: '方法: 演算子を定義するクラスを使用する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedures [Visual Basic], calling
- examples [Visual Basic], CType
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
ms.openlocfilehash: 7e1d5698c1e83f0adf1be67245e0726aecaabdac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="59f73-102">方法: 演算子を定義するクラスを使用する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59f73-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="59f73-103">クラスまたは独自の演算子を定義する構造体を使用している場合は、Visual Basic からこれらの演算子を表示できます。</span><span class="sxs-lookup"><span data-stu-id="59f73-103">If you are using a class or structure that defines its own operators, you can access those operators from Visual Basic.</span></span>  
  
 <span data-ttu-id="59f73-104">クラスまたは構造体で演算子を定義とも呼びます*オーバー ロード*演算子。</span><span class="sxs-lookup"><span data-stu-id="59f73-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59f73-105">例</span><span class="sxs-lookup"><span data-stu-id="59f73-105">Example</span></span>  
 <span data-ttu-id="59f73-106">次の例では、SQL 構造<xref:System.Data.SqlTypes.SqlString>、変換演算子を定義する ([CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md))、SQL 文字列と Visual Basic の文字列間で双方向でします。</span><span class="sxs-lookup"><span data-stu-id="59f73-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) in both directions between a SQL string and a Visual Basic string.</span></span> <span data-ttu-id="59f73-107">使用して`CType(` *SQL 文字列式*、 `String)` SQL 文字列を文字列に変換する Visual Basic、および`CType(` *Visual Basic の文字列式*、 <xref:System.Data.SqlTypes.SqlString> `)`に逆方向に変換します。</span><span class="sxs-lookup"><span data-stu-id="59f73-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a Visual Basic string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#31](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]  
  
 <span data-ttu-id="59f73-108"><xref:System.Data.SqlTypes.SqlString>変換演算子を定義する構造体 ([CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)) から`String`に<xref:System.Data.SqlTypes.SqlString>とから<xref:System.Data.SqlTypes.SqlString>に`String`です。</span><span class="sxs-lookup"><span data-stu-id="59f73-108">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="59f73-109">割り当てるステートメントを`title`に`jobTitle`では、最初の演算子を使用し、<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>関数呼び出しで、2 つ目は使用します。</span><span class="sxs-lookup"><span data-stu-id="59f73-109">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="59f73-110">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="59f73-110">Compiling the Code</span></span>  
 <span data-ttu-id="59f73-111">使用する演算子を定義クラスまたは構造体を使用していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="59f73-111">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="59f73-112">クラスまたは構造体の定義がすべての演算子はオーバー ロード可能なこととは限りません。</span><span class="sxs-lookup"><span data-stu-id="59f73-112">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="59f73-113">利用可能な演算子の一覧は、次を参照してください。 [Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="59f73-113">For a list of available operators, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="59f73-114">含める、適切な`Imports`、ソース ファイルの先頭に、SQL 文字列の文 (ここでは<xref:System.Data.SqlTypes>)。</span><span class="sxs-lookup"><span data-stu-id="59f73-114">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="59f73-115">プロジェクトには、System.Data、および System.XML への参照をいる必要があります。</span><span class="sxs-lookup"><span data-stu-id="59f73-115">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59f73-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="59f73-116">See Also</span></span>  
 [<span data-ttu-id="59f73-117">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="59f73-117">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="59f73-118">方法 : 演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="59f73-118">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="59f73-119">方法 : 変換演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="59f73-119">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="59f73-120">方法 : 演算子プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="59f73-120">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="59f73-121">Widening</span><span class="sxs-lookup"><span data-stu-id="59f73-121">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="59f73-122">Narrowing</span><span class="sxs-lookup"><span data-stu-id="59f73-122">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="59f73-123">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="59f73-123">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="59f73-124">方法 : 構造体を宣言する</span><span class="sxs-lookup"><span data-stu-id="59f73-124">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="59f73-125">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="59f73-125">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="59f73-126">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="59f73-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
