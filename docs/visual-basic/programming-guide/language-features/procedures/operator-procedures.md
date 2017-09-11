---
title: "演算子プロシージャ (Visual Basic) |Microsoft ドキュメント"
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
- Visual Basic code, procedures
- procedures, operator
- Visual Basic code, operators
- syntax, Operator procedures
- operators [Visual Basic], overloading
- overloaded operators
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
caps.latest.revision: 17
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
ms.openlocfilehash: 3b2e8466ad355521dcec3cf7b2949037e569eb9a
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="operator-procedures-visual-basic"></a><span data-ttu-id="ecde5-102">演算子プロシージャ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ecde5-102">Operator Procedures (Visual Basic)</span></span>
<span data-ttu-id="ecde5-103">演算子プロシージャは、一連の[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]標準の演算子の動作を定義するステートメント (よう`*`、 `<>`、または`And`) クラスまたは定義した構造体の。</span><span class="sxs-lookup"><span data-stu-id="ecde5-103">An operator procedure is a series of [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] statements that define the behavior of a standard operator (such as `*`, `<>`, or `And`) on a class or structure you have defined.</span></span> <span data-ttu-id="ecde5-104">いいます*演算子のオーバー ロード*します。</span><span class="sxs-lookup"><span data-stu-id="ecde5-104">This is also called *operator overloading*.</span></span>  
  
## <a name="when-to-define-operator-procedures"></a><span data-ttu-id="ecde5-105">演算子プロシージャを定義する場合</span><span class="sxs-lookup"><span data-stu-id="ecde5-105">When to Define Operator Procedures</span></span>  
 <span data-ttu-id="ecde5-106">クラスまたは構造体を定義した場合は、そのクラスまたは構造体の型の変数を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="ecde5-106">When you have defined a class or structure, you can declare variables to be of the type of that class or structure.</span></span> <span data-ttu-id="ecde5-107">このような変数は、式の一部として操作に参加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ecde5-107">Sometimes such a variable needs to participate in an operation as part of an expression.</span></span> <span data-ttu-id="ecde5-108">これを行うには、演算子のオペランドがあります。</span><span class="sxs-lookup"><span data-stu-id="ecde5-108">To do this, it must be an operand of an operator.</span></span>  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="ecde5-109">その基本的なデータ型に対してのみ演算子を定義します。</span><span class="sxs-lookup"><span data-stu-id="ecde5-109"> defines operators only on its fundamental data types.</span></span> <span data-ttu-id="ecde5-110">クラスまたは構造体の型の両方のオペランドまたは演算子と&1; つの動作を定義できます。</span><span class="sxs-lookup"><span data-stu-id="ecde5-110">You can define the behavior of an operator when one or both of the operands are of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="ecde5-111">詳細については、次を参照してください。 [Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="ecde5-111">For more information, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
## <a name="types-of-operator-procedure"></a><span data-ttu-id="ecde5-112">演算子プロシージャの種類</span><span class="sxs-lookup"><span data-stu-id="ecde5-112">Types of Operator Procedure</span></span>  
 <span data-ttu-id="ecde5-113">演算子プロシージャは、次の種類のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="ecde5-113">An operator procedure can be one of the following types:</span></span>  
  
-   <span data-ttu-id="ecde5-114">クラスまたは構造体の型の引数が単項演算子の定義。</span><span class="sxs-lookup"><span data-stu-id="ecde5-114">A definition of a unary operator where the argument is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="ecde5-115">ここで、クラスまたは構造体の型の引数の少なくとも&1; つは二項演算子の定義。</span><span class="sxs-lookup"><span data-stu-id="ecde5-115">A definition of a binary operator where at least one of the arguments is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="ecde5-116">引数がクラスまたは構造体の型の変換演算子の定義。</span><span class="sxs-lookup"><span data-stu-id="ecde5-116">A definition of a conversion operator where the argument is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="ecde5-117">クラスまたは構造体の型を返す変換演算子の定義。</span><span class="sxs-lookup"><span data-stu-id="ecde5-117">A definition of a conversion operator that returns the type of your class or structure.</span></span>  
  
 <span data-ttu-id="ecde5-118">変換演算子は、単項演算子では常に、常に使用する`CType`として定義する演算子です。</span><span class="sxs-lookup"><span data-stu-id="ecde5-118">Conversion operators are always unary, and you always use `CType` as the operator you are defining.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="ecde5-119">宣言の構文</span><span class="sxs-lookup"><span data-stu-id="ecde5-119">Declaration Syntax</span></span>  
 <span data-ttu-id="ecde5-120">演算子プロシージャを宣言する構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ecde5-120">The syntax for declaring an operator procedure is as follows:</span></span>  
  
 <span data-ttu-id="ecde5-121">`Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol*  `(` *operand1*  `[,`  *operand2* `]) As`  *datatype*</span><span class="sxs-lookup"><span data-stu-id="ecde5-121">`Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol*  `(` *operand1*  `[,`  *operand2* `]) As`  *datatype*</span></span>  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 <span data-ttu-id="ecde5-122">使用する、`Widening`または`Narrowing`型変換演算子でのみキーワードです。</span><span class="sxs-lookup"><span data-stu-id="ecde5-122">You use the `Widening` or `Narrowing` keyword only on a type conversion operator.</span></span> <span data-ttu-id="ecde5-123">演算子記号は常に[CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)型変換演算子のです。</span><span class="sxs-lookup"><span data-stu-id="ecde5-123">The operator symbol is always [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) for a type conversion operator.</span></span>  
  
 <span data-ttu-id="ecde5-124">二項演算子を定義する&2; つのオペランドを宣言し、型変換演算子を含む、単項演算子を定義する&1; つのオペランドを宣言します。</span><span class="sxs-lookup"><span data-stu-id="ecde5-124">You declare two operands to define a binary operator, and you declare one operand to define a unary operator, including a type conversion operator.</span></span> <span data-ttu-id="ecde5-125">すべてのオペランドを宣言する必要があります`ByVal`します。</span><span class="sxs-lookup"><span data-stu-id="ecde5-125">All operands must be declared `ByVal`.</span></span>  
  
 <span data-ttu-id="ecde5-126">各オペランドを宣言すると、同様のパラメーターを宣言する[Sub プロシージャ](./sub-procedures.md)します。</span><span class="sxs-lookup"><span data-stu-id="ecde5-126">You declare each operand the same way you declare parameters for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="ecde5-127">データの種類</span><span class="sxs-lookup"><span data-stu-id="ecde5-127">Data Type</span></span>  
 <span data-ttu-id="ecde5-128">クラスまたは構造体を定義した演算子を定義しているために、そのクラスまたは構造体のデータ型のオペランドの少なくとも&1; つがあります。</span><span class="sxs-lookup"><span data-stu-id="ecde5-128">Because you are defining an operator on a class or structure you have defined, at least one of the operands must be of the data type of that class or structure.</span></span> <span data-ttu-id="ecde5-129">型変換演算子のオペランドまたは戻り値の型がクラスまたは構造体のデータ型でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="ecde5-129">For a type conversion operator, either the operand or the return type must be of the data type of the class or structure.</span></span>  
  
 <span data-ttu-id="ecde5-130">詳細については、次を参照してください。 [Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="ecde5-130">For more details, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="ecde5-131">呼び出し構文</span><span class="sxs-lookup"><span data-stu-id="ecde5-131">Calling Syntax</span></span>  
 <span data-ttu-id="ecde5-132">演算子プロシージャは、式の中で演算子のシンボルを使用して暗黙的を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ecde5-132">You invoke an operator procedure implicitly by using the operator symbol in an expression.</span></span> <span data-ttu-id="ecde5-133">定義済みの演算子の場合と同じ方法で、オペランドを指定します。</span><span class="sxs-lookup"><span data-stu-id="ecde5-133">You supply the operands the same way you do for predefined operators.</span></span>  
  
 <span data-ttu-id="ecde5-134">演算子プロシージャへの暗黙の呼び出しの構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ecde5-134">The syntax for an implicit call to an operator procedure is as follows:</span></span>  
  
 <span data-ttu-id="ecde5-135">`Dim testStruct As`  *structurename*</span><span class="sxs-lookup"><span data-stu-id="ecde5-135">`Dim testStruct As`  *structurename*</span></span>  
  
 <span data-ttu-id="ecde5-136">`Dim testNewStruct As`  *structurename*`= testStruct`*operatorsymbol    *  `10`</span><span class="sxs-lookup"><span data-stu-id="ecde5-136">`Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="ecde5-137">宣言と呼び出しの図</span><span class="sxs-lookup"><span data-stu-id="ecde5-137">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="ecde5-138">次の構造は、上位および下位の構成要素として、128 ビットの符号付き整数値を格納します。</span><span class="sxs-lookup"><span data-stu-id="ecde5-138">The following structure stores a signed 128-bit integer value as the constituent high-order and low-order parts.</span></span> <span data-ttu-id="ecde5-139">定義、`+`演算子を&2; つ`veryLong`値であり、その結果を生成`veryLong`値。</span><span class="sxs-lookup"><span data-stu-id="ecde5-139">It defines the `+` operator to add two `veryLong` values and generate a resulting `veryLong` value.</span></span>  
  
 <span data-ttu-id="ecde5-140">[!code-vb[VbVbcnProcedures 第&23;](./codesnippet/VisualBasic/operator-procedures_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ecde5-140">[!code-vb[VbVbcnProcedures#23](./codesnippet/VisualBasic/operator-procedures_1.vb)]</span></span>  
  
 <span data-ttu-id="ecde5-141">次の例では、一般的な呼び出しを`+`で定義されたオペレーター`veryLong`します。</span><span class="sxs-lookup"><span data-stu-id="ecde5-141">The following example shows a typical call to the `+` operator defined on `veryLong`.</span></span>  
  
 <span data-ttu-id="ecde5-142">[!code-vb[VbVbcnProcedures #&24;](./codesnippet/VisualBasic/operator-procedures_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="ecde5-142">[!code-vb[VbVbcnProcedures#24](./codesnippet/VisualBasic/operator-procedures_2.vb)]</span></span>  
  
 <span data-ttu-id="ecde5-143">詳細と例については、次を参照してください。 [Visual Basic 2005 の演算子のオーバー ロード](http://go.microsoft.com/fwlink/?LinkId=101703)します。</span><span class="sxs-lookup"><span data-stu-id="ecde5-143">For more information and examples, see [Operator Overloading in Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecde5-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="ecde5-144">See Also</span></span>  
 <span data-ttu-id="ecde5-145">[手順](./index.md) </span><span class="sxs-lookup"><span data-stu-id="ecde5-145">[Procedures](./index.md) </span></span>  
<span data-ttu-id="ecde5-146"> [Sub プロシージャ](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="ecde5-146"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="ecde5-147"> [Function プロシージャ](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="ecde5-147"> [Function Procedures](./function-procedures.md) </span></span>  
<span data-ttu-id="ecde5-148"> [プロパティ プロシージャ](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="ecde5-148"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="ecde5-149"> [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="ecde5-149"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="ecde5-150"> [Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md) </span><span class="sxs-lookup"><span data-stu-id="ecde5-150"> [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md) </span></span>  
<span data-ttu-id="ecde5-151"> [方法: 演算子を定義](./how-to-define-an-operator.md) </span><span class="sxs-lookup"><span data-stu-id="ecde5-151"> [How to: Define an Operator](./how-to-define-an-operator.md) </span></span>  
<span data-ttu-id="ecde5-152"> [方法: 変換演算子を定義します。](./how-to-define-a-conversion-operator.md) </span><span class="sxs-lookup"><span data-stu-id="ecde5-152"> [How to: Define a Conversion Operator](./how-to-define-a-conversion-operator.md) </span></span>  
<span data-ttu-id="ecde5-153"> [方法: 演算子プロシージャを呼び出す](./how-to-call-an-operator-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="ecde5-153"> [How to: Call an Operator Procedure](./how-to-call-an-operator-procedure.md) </span></span>  
<span data-ttu-id="ecde5-154"> [方法: 演算子を定義するクラスを使用する](./how-to-use-a-class-that-defines-operators.md)</span><span class="sxs-lookup"><span data-stu-id="ecde5-154"> [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md)</span></span>
