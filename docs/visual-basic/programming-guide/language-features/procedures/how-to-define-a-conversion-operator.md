---
title: '方法: 変換演算子を定義する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: 24bbe41af67f757cae661a78d482a423ff0ffd85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648474"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="22864-102">方法: 変換演算子を定義する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22864-102">How to: Define a Conversion Operator (Visual Basic)</span></span>
<span data-ttu-id="22864-103">クラスまたは構造体を定義している場合は、クラスまたは構造体の型と別のデータ型の型変換演算子を定義することができます (など`Integer`、 `Double`、または`String`)。</span><span class="sxs-lookup"><span data-stu-id="22864-103">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="22864-104">として型の変換を定義、 [CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)クラスまたは構造内のプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="22864-104">Define the type conversion as a [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="22864-105">変換のすべてのプロシージャである必要があります`Public Shared`、どちらか 1 つを指定する必要がありますと[Widening](../../../../visual-basic/language-reference/modifiers/widening.md)または[Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)です。</span><span class="sxs-lookup"><span data-stu-id="22864-105">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) or [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="22864-106">クラスまたは構造体で演算子を定義とも呼びます*オーバー ロード*演算子。</span><span class="sxs-lookup"><span data-stu-id="22864-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22864-107">例</span><span class="sxs-lookup"><span data-stu-id="22864-107">Example</span></span>  
 <span data-ttu-id="22864-108">次の例と呼ばれる構造との間の変換演算子を定義する`digit`と`Byte`です。</span><span class="sxs-lookup"><span data-stu-id="22864-108">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#27](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_1.vb)]  
  
 <span data-ttu-id="22864-109">構造体をテストする`digit`を次のコード。</span><span class="sxs-lookup"><span data-stu-id="22864-109">You can test the structure `digit` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#28](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="22864-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="22864-110">See Also</span></span>  
 [<span data-ttu-id="22864-111">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="22864-111">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="22864-112">方法 : 演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="22864-112">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="22864-113">方法 : 演算子プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="22864-113">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="22864-114">方法: 演算子を定義するクラスを使用する</span><span class="sxs-lookup"><span data-stu-id="22864-114">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)  
 [<span data-ttu-id="22864-115">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="22864-115">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="22864-116">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="22864-116">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="22864-117">方法 : 構造体を宣言する</span><span class="sxs-lookup"><span data-stu-id="22864-117">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="22864-118">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="22864-118">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="22864-119">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="22864-119">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
