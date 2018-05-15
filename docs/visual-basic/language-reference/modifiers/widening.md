---
title: Widening (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
ms.openlocfilehash: 2323aa38c81ce4e027f256d0e29c069f7ec77c00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="widening-visual-basic"></a><span data-ttu-id="9158f-102">Widening (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9158f-102">Widening (Visual Basic)</span></span>
<span data-ttu-id="9158f-103">示します変換演算子 (`CType`) クラスまたは構造体を元のクラスまたは構造体のすべての可能な値を保持できる型に変換します。</span><span class="sxs-lookup"><span data-stu-id="9158f-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="9158f-104">拡大のキーワードを使用して変換します。</span><span class="sxs-lookup"><span data-stu-id="9158f-104">Converting with the Widening Keyword</span></span>  
 <span data-ttu-id="9158f-105">変換のプロシージャを指定する必要があります`Public Shared`に加えて`Widening`です。</span><span class="sxs-lookup"><span data-stu-id="9158f-105">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="9158f-106">拡大変換は実行時に常に成功して、データの損失が発生することはありません。</span><span class="sxs-lookup"><span data-stu-id="9158f-106">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="9158f-107">例としては、`Single`に`Double`、`Char`に`String`、およびその基本型を派生型です。</span><span class="sxs-lookup"><span data-stu-id="9158f-107">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="9158f-108">この最後の変換は、派生型は、基本型のすべてのメンバーが含まれており、したがって、基本データ型のインスタンスに拡大変換がします。</span><span class="sxs-lookup"><span data-stu-id="9158f-108">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="9158f-109">コンシューマー コードが使用する必要はありません`CType`拡大変換、たとえ`Option Strict`は`On`します。</span><span class="sxs-lookup"><span data-stu-id="9158f-109">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="9158f-110">`Widening`キーワードは、このコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="9158f-110">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="9158f-111">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="9158f-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 <span data-ttu-id="9158f-112">たとえば拡大変換と縮小変換演算子の定義を参照してください[する方法: 変換演算子を定義する](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)です。</span><span class="sxs-lookup"><span data-stu-id="9158f-112">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9158f-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="9158f-113">See Also</span></span>  
 [<span data-ttu-id="9158f-114">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="9158f-114">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="9158f-115">Narrowing</span><span class="sxs-lookup"><span data-stu-id="9158f-115">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="9158f-116">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="9158f-116">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="9158f-117">方法 : 演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="9158f-117">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="9158f-118">CType 関数</span><span class="sxs-lookup"><span data-stu-id="9158f-118">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [<span data-ttu-id="9158f-119">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="9158f-119">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="9158f-120">方法 : 変換演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="9158f-120">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
