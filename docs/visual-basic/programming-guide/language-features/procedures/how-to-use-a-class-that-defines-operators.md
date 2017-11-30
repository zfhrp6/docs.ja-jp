---
title: "方法: 演算子を定義するクラスを使用する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 223b3fc84fe75d1d530cd182c9332e5c663aa519
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="e298c-102">方法: 演算子を定義するクラスを使用する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e298c-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="e298c-103">クラスまたは独自の演算子を定義する構造体を使用している場合のこれらの演算子にアクセスできます[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="e298c-103">If you are using a class or structure that defines its own operators, you can access those operators from [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 <span data-ttu-id="e298c-104">クラスまたは構造体で演算子を定義とも呼びます*オーバー ロード*演算子。</span><span class="sxs-lookup"><span data-stu-id="e298c-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e298c-105">例</span><span class="sxs-lookup"><span data-stu-id="e298c-105">Example</span></span>  
 <span data-ttu-id="e298c-106">次の例では、SQL 構造<xref:System.Data.SqlTypes.SqlString>、変換演算子を定義する ([CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)) SQL 文字列間の双方向で、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]文字列。</span><span class="sxs-lookup"><span data-stu-id="e298c-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) in both directions between a SQL string and a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] string.</span></span> <span data-ttu-id="e298c-107">使用して`CType(` *SQL 文字列式*、`String)`への SQL 文字列を変換する、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]文字列、および`CType(` *Visual Basic の文字列式*、 <xref:System.Data.SqlTypes.SqlString>`)`に逆方向に変換します。</span><span class="sxs-lookup"><span data-stu-id="e298c-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#31](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]  
  
 <span data-ttu-id="e298c-108"><xref:System.Data.SqlTypes.SqlString>変換演算子を定義する構造体 ([CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)) から`String`に<xref:System.Data.SqlTypes.SqlString>とから<xref:System.Data.SqlTypes.SqlString>に`String`です。</span><span class="sxs-lookup"><span data-stu-id="e298c-108">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="e298c-109">割り当てるステートメントを`title`に`jobTitle`では、最初の演算子を使用し、<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>関数呼び出しで、2 つ目は使用します。</span><span class="sxs-lookup"><span data-stu-id="e298c-109">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e298c-110">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="e298c-110">Compiling the Code</span></span>  
 <span data-ttu-id="e298c-111">使用する演算子を定義クラスまたは構造体を使用していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e298c-111">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="e298c-112">クラスまたは構造体の定義がすべての演算子はオーバー ロード可能なこととは限りません。</span><span class="sxs-lookup"><span data-stu-id="e298c-112">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="e298c-113">利用可能な演算子の一覧は、次を参照してください。 [Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="e298c-113">For a list of available operators, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="e298c-114">含める、適切な`Imports`、ソース ファイルの先頭に、SQL 文字列の文 (ここでは<xref:System.Data.SqlTypes>)。</span><span class="sxs-lookup"><span data-stu-id="e298c-114">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="e298c-115">プロジェクトには、System.Data、および System.XML への参照をいる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e298c-115">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e298c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="e298c-116">See Also</span></span>  
 [<span data-ttu-id="e298c-117">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="e298c-117">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="e298c-118">方法 : 演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="e298c-118">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="e298c-119">方法 : 変換演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="e298c-119">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="e298c-120">方法 : 演算子プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="e298c-120">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="e298c-121">Widening</span><span class="sxs-lookup"><span data-stu-id="e298c-121">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="e298c-122">Narrowing</span><span class="sxs-lookup"><span data-stu-id="e298c-122">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="e298c-123">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="e298c-123">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="e298c-124">方法 : 構造体を宣言する</span><span class="sxs-lookup"><span data-stu-id="e298c-124">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="e298c-125">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="e298c-125">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="e298c-126">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="e298c-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
