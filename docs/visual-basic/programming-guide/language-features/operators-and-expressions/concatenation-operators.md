---
title: "Visual Basic の連結演算子 |Microsoft ドキュメント"
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
- '& operator [Visual Basic], concatenation'
- concatenation operators
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators, Visual Basic strings
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
caps.latest.revision: 18
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
ms.openlocfilehash: f255e168b9eb794ef846e0cc18dbbdba5941bec5
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="concatenation-operators-in-visual-basic"></a><span data-ttu-id="27fca-102">Visual Basic の連結演算子</span><span class="sxs-lookup"><span data-stu-id="27fca-102">Concatenation Operators in Visual Basic</span></span>
<span data-ttu-id="27fca-103">連結演算子は、複数の文字列を結合して&1; つの文字列にします。</span><span class="sxs-lookup"><span data-stu-id="27fca-103">Concatenation operators join multiple strings into a single string.</span></span> <span data-ttu-id="27fca-104">連結演算子には、`+` と `&` の&2; つがあります。</span><span class="sxs-lookup"><span data-stu-id="27fca-104">There are two concatenation operators, `+` and `&`.</span></span> <span data-ttu-id="27fca-105">どちらの演算子も、次の例に示すように基本的な連結演算を行います。</span><span class="sxs-lookup"><span data-stu-id="27fca-105">Both carry out the basic concatenation operation, as the following example shows.</span></span>  
  
```vb
Dim x As String = "Mic" & "ro" & "soft" 
Dim y As String = "Mic" + "ro" + "soft" 
' The preceding statements set both x and y to "Microsoft".
```  
  
 <span data-ttu-id="27fca-106">これらの演算子は、次のように `String` 型の変数を連結することもできます。</span><span class="sxs-lookup"><span data-stu-id="27fca-106">These operators can also concatenate `String` variables, as the following example shows.</span></span>  
  
 <span data-ttu-id="27fca-107">[!code-vb[VbVbalrOperators #&76;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operators_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="27fca-107">[!code-vb[VbVbalrOperators#76](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operators_1.vb)]</span></span>  
  
## <a name="differences-between-the-two-concatenation-operators"></a><span data-ttu-id="27fca-108">2 つの連結演算子の相違点</span><span class="sxs-lookup"><span data-stu-id="27fca-108">Differences Between the Two Concatenation Operators</span></span>  
 <span data-ttu-id="27fca-109">[+ 演算子](../../../../visual-basic/language-reference/operators/addition-operator.md)が&2; つの数値を追加する主な目的です。</span><span class="sxs-lookup"><span data-stu-id="27fca-109">The [+ Operator](../../../../visual-basic/language-reference/operators/addition-operator.md) has the primary purpose of adding two numbers.</span></span> <span data-ttu-id="27fca-110">ただし、数値オペランドを文字列オペランドに連結することもできます。</span><span class="sxs-lookup"><span data-stu-id="27fca-110">However, it can also concatenate numeric operands with string operands.</span></span> <span data-ttu-id="27fca-111">`+`演算子は、複雑な一連のルールを追加、連結、コンパイラ エラーを報告または実行時にスローするかどうかを決定する<xref:System.InvalidCastException>例外</xref:System.InvalidCastException>。</span><span class="sxs-lookup"><span data-stu-id="27fca-111">The `+` operator has a complex set of rules that determine whether to add, concatenate, signal a compiler error, or throw a run-time <xref:System.InvalidCastException> exception.</span></span>  
  
 <span data-ttu-id="27fca-112">[&Gt;/documents/report1.rdl」の演算子](../../../../visual-basic/language-reference/operators/concatenation-operator.md)に対してのみ定義`String`オペランド、および、常に拡大変換するには、そのオペランド`String`の設定に関係なく、`Option Strict`です。</span><span class="sxs-lookup"><span data-stu-id="27fca-112">The [& Operator](../../../../visual-basic/language-reference/operators/concatenation-operator.md) is defined only for `String` operands, and it always widens its operands to `String`, regardless of the setting of `Option Strict`.</span></span> <span data-ttu-id="27fca-113">文字列の連結には `&` 演算子を使用することをお勧めします。この演算子は文字列専用として定義されているため、意図しない変換が発生する可能性を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="27fca-113">The `&` operator is recommended for string concatenation because it is defined exclusively for strings and reduces your chances of generating an unintended conversion.</span></span>  
  
## <a name="performance-string-and-stringbuilder"></a><span data-ttu-id="27fca-114">パフォーマンス: 文字列と StringBuilder</span><span class="sxs-lookup"><span data-stu-id="27fca-114">Performance: String and StringBuilder</span></span>  
 <span data-ttu-id="27fca-115">パフォーマンスが向上する非常に多くの連結、削除、置換などの文字列操作の操作を行う場合、<xref:System.Text.StringBuilder>クラス、<xref:System.Text>名前空間</xref:System.Text></xref:System.Text.StringBuilder>。</span><span class="sxs-lookup"><span data-stu-id="27fca-115">If you do a significant number of manipulations on a string, such as concatenations, deletions, and replacements, your performance might profit from the <xref:System.Text.StringBuilder> class in the <xref:System.Text> namespace.</span></span> <span data-ttu-id="27fca-116">作成および初期化するには追加の命令を受け取り、<xref:System.Text.StringBuilder>オブジェクト、および別の命令を最終的な値に変換する、 `String`、ために、この時間を埋め合わせることがありますが、<xref:System.Text.StringBuilder>高速に実行できます</xref:System.Text.StringBuilder></xref:System.Text.StringBuilder>。</span><span class="sxs-lookup"><span data-stu-id="27fca-116">It takes an extra instruction to create and initialize a <xref:System.Text.StringBuilder> object, and another instruction to convert its final value to a `String`, but you might recover this time because <xref:System.Text.StringBuilder> can perform faster.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27fca-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="27fca-117">See Also</span></span>  
 <span data-ttu-id="27fca-118">[Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="27fca-118">[Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="27fca-119"> [Visual Basic で文字列操作メソッドの種類](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md) </span><span class="sxs-lookup"><span data-stu-id="27fca-119"> [Types of String Manipulation Methods in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md) </span></span>  
<span data-ttu-id="27fca-120"> [Visual Basic における算術演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="27fca-120"> [Arithmetic Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) </span></span>  
<span data-ttu-id="27fca-121"> [Visual Basic における比較演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="27fca-121"> [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span></span>  
<span data-ttu-id="27fca-122"> [Visual Basic での論理/ビット処理演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span><span class="sxs-lookup"><span data-stu-id="27fca-122"> [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span></span>
