---
title: "方法: 演算子を定義する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 51921ee38204fd528ed19436806fc9433abbdc5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-an-operator-visual-basic"></a><span data-ttu-id="c0deb-102">方法: 演算子を定義する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0deb-102">How to: Define an Operator (Visual Basic)</span></span>
<span data-ttu-id="c0deb-103">標準の演算子の動作を定義するクラスまたは構造体を定義している場合 (など`*`、 `<>`、または`And`) 1 つまたは両方のオペランドがクラスまたは構造体の型であるときです。</span><span class="sxs-lookup"><span data-stu-id="c0deb-103">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="c0deb-104">クラスまたは構造体で演算子プロシージャとして標準の演算子を定義します。</span><span class="sxs-lookup"><span data-stu-id="c0deb-104">Define the standard operator as an operator procedure within the class or structure.</span></span> <span data-ttu-id="c0deb-105">演算子のすべてのプロシージャである必要があります`Public``Shared`です。</span><span class="sxs-lookup"><span data-stu-id="c0deb-105">All operator procedures must be `Public` `Shared`.</span></span>  
  
 <span data-ttu-id="c0deb-106">クラスまたは構造体で演算子を定義とも呼びます*オーバー ロード*演算子。</span><span class="sxs-lookup"><span data-stu-id="c0deb-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0deb-107">例</span><span class="sxs-lookup"><span data-stu-id="c0deb-107">Example</span></span>  
 <span data-ttu-id="c0deb-108">次の例では定義、`+`構造体の演算子と呼ばれる`height`です。</span><span class="sxs-lookup"><span data-stu-id="c0deb-108">The following example defines the `+` operator for a structure called `height`.</span></span> <span data-ttu-id="c0deb-109">構造体は、フィートおよびインチ単位の高さを使用します。</span><span class="sxs-lookup"><span data-stu-id="c0deb-109">The structure uses heights measured in feet and inches.</span></span> <span data-ttu-id="c0deb-110">1 つ*インチ*2.54 センチメートル、および 1 つは、 *foot* 12 インチです。</span><span class="sxs-lookup"><span data-stu-id="c0deb-110">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span></span> <span data-ttu-id="c0deb-111">コンス トラクターを実行するのには、正規化された値 (インチ < 12.0)*剰余*12 の演算です。</span><span class="sxs-lookup"><span data-stu-id="c0deb-111">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span></span> <span data-ttu-id="c0deb-112">`+`演算子では、コンス トラクターを使用して、正規化された値を生成します。</span><span class="sxs-lookup"><span data-stu-id="c0deb-112">The `+` operator uses the constructor to generate normalized values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#25](./codesnippet/VisualBasic/how-to-define-an-operator_1.vb)]  
  
 <span data-ttu-id="c0deb-113">構造体をテストする`height`を次のコード。</span><span class="sxs-lookup"><span data-stu-id="c0deb-113">You can test the structure `height` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#26](./codesnippet/VisualBasic/how-to-define-an-operator_2.vb)]  
  
 <span data-ttu-id="c0deb-114">使用例を含む詳細については、「[Visual Basic 2005 での演算子のオーバーロード](http://go.microsoft.com/fwlink/?LinkId=101703)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0deb-114">For more information and examples, see [Operator Overloading in Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0deb-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0deb-115">See Also</span></span>  
 [<span data-ttu-id="c0deb-116">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="c0deb-116">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="c0deb-117">方法 : 変換演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="c0deb-117">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="c0deb-118">方法 : 演算子プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="c0deb-118">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="c0deb-119">方法: 演算子を定義するクラスを使用する</span><span class="sxs-lookup"><span data-stu-id="c0deb-119">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)  
 [<span data-ttu-id="c0deb-120">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="c0deb-120">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="c0deb-121">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="c0deb-121">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="c0deb-122">方法 : 構造体を宣言する</span><span class="sxs-lookup"><span data-stu-id="c0deb-122">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="c0deb-123">Mod 演算子</span><span class="sxs-lookup"><span data-stu-id="c0deb-123">Mod Operator</span></span>](../../../../visual-basic/language-reference/operators/mod-operator.md)
