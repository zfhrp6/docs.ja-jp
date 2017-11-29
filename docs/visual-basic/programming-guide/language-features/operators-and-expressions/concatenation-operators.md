---
title: "Visual Basic の連結演算子"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators [Visual Basic]
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators [Visual Basic]
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3a444cca76fbc41807b0c8b69bcbaedbd75c36eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="concatenation-operators-in-visual-basic"></a><span data-ttu-id="115f2-102">Visual Basic の連結演算子</span><span class="sxs-lookup"><span data-stu-id="115f2-102">Concatenation Operators in Visual Basic</span></span>
<span data-ttu-id="115f2-103">連結演算子は、複数の文字列を結合して 1 つの文字列にします。</span><span class="sxs-lookup"><span data-stu-id="115f2-103">Concatenation operators join multiple strings into a single string.</span></span> <span data-ttu-id="115f2-104">連結演算子には、`+` と `&` の 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="115f2-104">There are two concatenation operators, `+` and `&`.</span></span> <span data-ttu-id="115f2-105">どちらの演算子も、次の例に示すように基本的な連結演算を行います。</span><span class="sxs-lookup"><span data-stu-id="115f2-105">Both carry out the basic concatenation operation, as the following example shows.</span></span>  
  
```vb
Dim x As String = "Mic" & "ro" & "soft" 
Dim y As String = "Mic" + "ro" + "soft" 
' The preceding statements set both x and y to "Microsoft".
```  
  
 <span data-ttu-id="115f2-106">これらの演算子は、次のように `String` 型の変数を連結することもできます。</span><span class="sxs-lookup"><span data-stu-id="115f2-106">These operators can also concatenate `String` variables, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrOperators#76](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operators_1.vb)]  
  
## <a name="differences-between-the-two-concatenation-operators"></a><span data-ttu-id="115f2-107">2 つの連結演算子の相違点</span><span class="sxs-lookup"><span data-stu-id="115f2-107">Differences Between the Two Concatenation Operators</span></span>  
 <span data-ttu-id="115f2-108">[+ 演算子](../../../../visual-basic/language-reference/operators/addition-operator.md)が 2 つの数値を追加することの主な目的です。</span><span class="sxs-lookup"><span data-stu-id="115f2-108">The [+ Operator](../../../../visual-basic/language-reference/operators/addition-operator.md) has the primary purpose of adding two numbers.</span></span> <span data-ttu-id="115f2-109">ただし、数値オペランドを文字列オペランドに連結することもできます。</span><span class="sxs-lookup"><span data-stu-id="115f2-109">However, it can also concatenate numeric operands with string operands.</span></span> <span data-ttu-id="115f2-110">`+` 演算子は、一連の複雑な規則に従って、加算、連結、コンパイル エラーのシグナルの送信、ランタイム <xref:System.InvalidCastException> 例外のスローのどれを行うかを決定します。</span><span class="sxs-lookup"><span data-stu-id="115f2-110">The `+` operator has a complex set of rules that determine whether to add, concatenate, signal a compiler error, or throw a run-time <xref:System.InvalidCastException> exception.</span></span>  
  
 <span data-ttu-id="115f2-111">[& 演算子](../../../../visual-basic/language-reference/operators/concatenation-operator.md)に対してのみ定義`String`オペランド、および、常に拡大変換するには、そのオペランド`String`の設定に関係なく、`Option Strict`です。</span><span class="sxs-lookup"><span data-stu-id="115f2-111">The [& Operator](../../../../visual-basic/language-reference/operators/concatenation-operator.md) is defined only for `String` operands, and it always widens its operands to `String`, regardless of the setting of `Option Strict`.</span></span> <span data-ttu-id="115f2-112">文字列の連結には `&` 演算子を使用することをお勧めします。この演算子は文字列専用として定義されているため、意図しない変換が発生する可能性を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="115f2-112">The `&` operator is recommended for string concatenation because it is defined exclusively for strings and reduces your chances of generating an unintended conversion.</span></span>  
  
## <a name="performance-string-and-stringbuilder"></a><span data-ttu-id="115f2-113">パフォーマンス: 文字列と StringBuilder</span><span class="sxs-lookup"><span data-stu-id="115f2-113">Performance: String and StringBuilder</span></span>  
 <span data-ttu-id="115f2-114">連結、削除、置換などの文字列操作を何度も行う場合は、<xref:System.Text.StringBuilder> 名前空間の <xref:System.Text> クラスを使用するとパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="115f2-114">If you do a significant number of manipulations on a string, such as concatenations, deletions, and replacements, your performance might profit from the <xref:System.Text.StringBuilder> class in the <xref:System.Text> namespace.</span></span> <span data-ttu-id="115f2-115"><xref:System.Text.StringBuilder> オブジェクトを作成して初期化するには追加の命令が必要であり、最終的な値を `String` に変換するにはまた別の命令が必要になりますが、<xref:System.Text.StringBuilder> は高速に実行できるため、この時間を埋め合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="115f2-115">It takes an extra instruction to create and initialize a <xref:System.Text.StringBuilder> object, and another instruction to convert its final value to a `String`, but you might recover this time because <xref:System.Text.StringBuilder> can perform faster.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="115f2-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="115f2-116">See Also</span></span>  
 [<span data-ttu-id="115f2-117">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="115f2-117">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="115f2-118">Visual Basic における文字列操作メソッドの型</span><span class="sxs-lookup"><span data-stu-id="115f2-118">Types of String Manipulation Methods in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)  
 [<span data-ttu-id="115f2-119">Visual Basic における算術演算子</span><span class="sxs-lookup"><span data-stu-id="115f2-119">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="115f2-120">Visual Basic における比較演算子</span><span class="sxs-lookup"><span data-stu-id="115f2-120">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="115f2-121">Visual Basic における論理/ビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="115f2-121">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
