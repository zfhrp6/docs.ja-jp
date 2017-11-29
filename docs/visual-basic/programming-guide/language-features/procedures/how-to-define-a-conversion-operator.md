---
title: "方法: 変換演算子を定義する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b0f9e63ba039a48226186fa4ce118d3e47b5673e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="822a0-102">方法: 変換演算子を定義する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="822a0-102">How to: Define a Conversion Operator (Visual Basic)</span></span>
<span data-ttu-id="822a0-103">クラスまたは構造体を定義している場合は、クラスまたは構造体の型と別のデータ型の型変換演算子を定義することができます (など`Integer`、 `Double`、または`String`)。</span><span class="sxs-lookup"><span data-stu-id="822a0-103">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="822a0-104">として型の変換を定義、 [CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)クラスまたは構造内のプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="822a0-104">Define the type conversion as a [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="822a0-105">変換のすべてのプロシージャである必要があります`Public Shared`、どちらか 1 つを指定する必要がありますと[Widening](../../../../visual-basic/language-reference/modifiers/widening.md)または[Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)です。</span><span class="sxs-lookup"><span data-stu-id="822a0-105">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) or [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="822a0-106">クラスまたは構造体で演算子を定義とも呼びます*オーバー ロード*演算子。</span><span class="sxs-lookup"><span data-stu-id="822a0-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="822a0-107">例</span><span class="sxs-lookup"><span data-stu-id="822a0-107">Example</span></span>  
 <span data-ttu-id="822a0-108">次の例と呼ばれる構造との間の変換演算子を定義する`digit`と`Byte`です。</span><span class="sxs-lookup"><span data-stu-id="822a0-108">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#27](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_1.vb)]  
  
 <span data-ttu-id="822a0-109">構造体をテストする`digit`を次のコード。</span><span class="sxs-lookup"><span data-stu-id="822a0-109">You can test the structure `digit` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#28](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="822a0-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="822a0-110">See Also</span></span>  
 [<span data-ttu-id="822a0-111">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="822a0-111">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="822a0-112">方法 : 演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="822a0-112">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="822a0-113">方法 : 演算子プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="822a0-113">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="822a0-114">方法: 演算子を定義するクラスを使用する</span><span class="sxs-lookup"><span data-stu-id="822a0-114">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)  
 [<span data-ttu-id="822a0-115">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="822a0-115">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="822a0-116">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="822a0-116">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="822a0-117">方法 : 構造体を宣言する</span><span class="sxs-lookup"><span data-stu-id="822a0-117">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="822a0-118">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="822a0-118">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="822a0-119">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="822a0-119">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
