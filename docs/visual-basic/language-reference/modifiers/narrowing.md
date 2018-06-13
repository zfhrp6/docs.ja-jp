---
title: Narrowing (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
ms.openlocfilehash: 54a18d0cc10e42829b48b0ef75bb77ab0d47b45f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597459"
---
# <a name="narrowing-visual-basic"></a><span data-ttu-id="b7aee-102">Narrowing (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7aee-102">Narrowing (Visual Basic)</span></span>
<span data-ttu-id="b7aee-103">示します変換演算子 (`CType`) クラスまたは構造体を元のクラスまたは構造体の有効値の一部を保持することができない可能性がある型に変換します。</span><span class="sxs-lookup"><span data-stu-id="b7aee-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-narrowing-keyword"></a><span data-ttu-id="b7aee-104">縮小のキーワードを使用して変換します。</span><span class="sxs-lookup"><span data-stu-id="b7aee-104">Converting with the Narrowing Keyword</span></span>  
 <span data-ttu-id="b7aee-105">変換のプロシージャを指定する必要があります`Public Shared`に加えて`Narrowing`です。</span><span class="sxs-lookup"><span data-stu-id="b7aee-105">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span></span>  
  
 <span data-ttu-id="b7aee-106">縮小変換は常にではありません、実行時に成功し失敗したり、データの損失を伴うできます。</span><span class="sxs-lookup"><span data-stu-id="b7aee-106">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="b7aee-107">例としては、`Long`に`Integer`、`String`に`Date`、および派生型に基本型です。</span><span class="sxs-lookup"><span data-stu-id="b7aee-107">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span></span> <span data-ttu-id="b7aee-108">基本データ型が派生型のすべてのメンバーを含めることはできず、そのため、派生型のインスタンスではないために、この最後の変換は縮小します。</span><span class="sxs-lookup"><span data-stu-id="b7aee-108">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span></span>  
  
 <span data-ttu-id="b7aee-109">場合`Option Strict`は`On`では、使用コードを使用する必要があります`CType`のすべての縮小変換します。</span><span class="sxs-lookup"><span data-stu-id="b7aee-109">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span></span>  
  
 <span data-ttu-id="b7aee-110">`Narrowing`キーワードは、このコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="b7aee-110">The `Narrowing` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="b7aee-111">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="b7aee-111">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="b7aee-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7aee-112">See Also</span></span>  
 [<span data-ttu-id="b7aee-113">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="b7aee-113">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="b7aee-114">Widening</span><span class="sxs-lookup"><span data-stu-id="b7aee-114">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="b7aee-115">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="b7aee-115">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="b7aee-116">方法 : 演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="b7aee-116">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="b7aee-117">CType 関数</span><span class="sxs-lookup"><span data-stu-id="b7aee-117">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [<span data-ttu-id="b7aee-118">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="b7aee-118">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
