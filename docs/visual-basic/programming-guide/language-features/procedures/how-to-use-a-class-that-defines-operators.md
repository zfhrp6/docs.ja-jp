---
title: "方法: 演算子 (Visual Basic) を定義するクラスを使用して |Microsoft ドキュメント"
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
- procedures, calling
- examples [Visual Basic], CType
- syntax, Operator procedures
- operators [Visual Basic], overloading
- return values, Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
caps.latest.revision: 21
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
ms.openlocfilehash: e4d76788346e08123102d56088c0a1e0f5f2238f
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="00600-102">方法: 演算子を定義するクラスを使用する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00600-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="00600-103">クラスまたは独自の演算子を定義する構造体を使用している場合からこれらの演算子をアクセスすることができます[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="00600-103">If you are using a class or structure that defines its own operators, you can access those operators from [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
 <span data-ttu-id="00600-104">クラスまたは構造体で、演算子を定義することと呼ばれる*オーバー ロード*演算子。</span><span class="sxs-lookup"><span data-stu-id="00600-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00600-105">例</span><span class="sxs-lookup"><span data-stu-id="00600-105">Example</span></span>  
 <span data-ttu-id="00600-106">次の例では、SQL 構造<xref:System.Data.SqlTypes.SqlString>、変換演算子を定義する ([CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md))、SQL 文字列の両方向で、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]文字列</xref:System.Data.SqlTypes.SqlString>。</span><span class="sxs-lookup"><span data-stu-id="00600-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) in both directions between a SQL string and a [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] string.</span></span> <span data-ttu-id="00600-107">使用`CType(` *SQL 文字列式*、`String)`への SQL 文字列に変換する、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]文字列、および`CType(` *Visual Basic の文字列式*、<xref:System.Data.SqlTypes.SqlString>`)`逆方向に変換する</xref:System.Data.SqlTypes.SqlString>。</span><span class="sxs-lookup"><span data-stu-id="00600-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 <span data-ttu-id="00600-108">[!code-vb[VbVbcnProcedures #&30;](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="00600-108">[!code-vb[VbVbcnProcedures#30](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]</span></span>  
  
 <span data-ttu-id="00600-109">[!code-vb[VbVbcnProcedures #&31;](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="00600-109">[!code-vb[VbVbcnProcedures#31](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]</span></span>  
  
 <span data-ttu-id="00600-110"><xref:System.Data.SqlTypes.SqlString>構造体定義の変換演算子 ([CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)) から`String`に<xref:System.Data.SqlTypes.SqlString>とから<xref:System.Data.SqlTypes.SqlString>に`String`</xref:System.Data.SqlTypes.SqlString></xref:System.Data.SqlTypes.SqlString></xref:System.Data.SqlTypes.SqlString>。</span><span class="sxs-lookup"><span data-stu-id="00600-110">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="00600-111">代入するステートメント`title`に`jobTitle`では、最初の演算子では、使用、および<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>関数の呼び出しは、もう&1; つを使用して</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>。</span><span class="sxs-lookup"><span data-stu-id="00600-111">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="00600-112">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="00600-112">Compiling the Code</span></span>  
 <span data-ttu-id="00600-113">使用する演算子を定義、クラスまたは構造体を使用していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="00600-113">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="00600-114">クラスまたは構造体と、オーバー ロード可能なすべてのオペレーターが定義されているとは限りません。</span><span class="sxs-lookup"><span data-stu-id="00600-114">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="00600-115">使用可能な演算子の一覧は、次を参照してください。 [Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="00600-115">For a list of available operators, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="00600-116">含める、適切な`Imports`ソース ファイルの先頭に、SQL 文字列の文 (ここで<xref:System.Data.SqlTypes>).</xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="00600-116">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="00600-117">プロジェクトは、System.Data および System.XML への参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="00600-117">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00600-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="00600-118">See Also</span></span>  
 <span data-ttu-id="00600-119">[演算子プロシージャ](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="00600-119">[Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="00600-120"> [方法: 演算子を定義](./how-to-define-an-operator.md) </span><span class="sxs-lookup"><span data-stu-id="00600-120"> [How to: Define an Operator](./how-to-define-an-operator.md) </span></span>  
<span data-ttu-id="00600-121"> [方法: 変換演算子を定義します。](./how-to-define-a-conversion-operator.md) </span><span class="sxs-lookup"><span data-stu-id="00600-121"> [How to: Define a Conversion Operator](./how-to-define-a-conversion-operator.md) </span></span>  
<span data-ttu-id="00600-122"> [方法: 演算子プロシージャを呼び出す](./how-to-call-an-operator-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="00600-122"> [How to: Call an Operator Procedure](./how-to-call-an-operator-procedure.md) </span></span>  
<span data-ttu-id="00600-123"> [拡大変換](../../../../visual-basic/language-reference/modifiers/widening.md) </span><span class="sxs-lookup"><span data-stu-id="00600-123"> [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) </span></span>  
<span data-ttu-id="00600-124"> [縮小変換](../../../../visual-basic/language-reference/modifiers/narrowing.md) </span><span class="sxs-lookup"><span data-stu-id="00600-124"> [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md) </span></span>  
<span data-ttu-id="00600-125"> [Structure ステートメント](../../../../visual-basic/language-reference/statements/structure-statement.md) </span><span class="sxs-lookup"><span data-stu-id="00600-125"> [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md) </span></span>  
<span data-ttu-id="00600-126"> [方法: 構造体を宣言](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md) </span><span class="sxs-lookup"><span data-stu-id="00600-126"> [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md) </span></span>  
<span data-ttu-id="00600-127"> [明示的および暗黙的な変換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="00600-127"> [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span></span>  
<span data-ttu-id="00600-128"> [拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)</span><span class="sxs-lookup"><span data-stu-id="00600-128"> [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)</span></span>
