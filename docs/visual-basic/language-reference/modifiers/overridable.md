---
title: Overridable (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Overridable
- vb.Overridable
helpviewer_keywords:
- elements [Visual Basic], concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements [Visual Basic], virtual
- virtual [elements VB]
- procedures [Visual Basic], overriding
- concrete [elements VB]
- procedures [Visual Basic], redefining
- Overridable keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
ms.openlocfilehash: 4844bf7f3ecf23335715b950a96be15e54ebc601
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603770"
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="1a791-102">Overridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a791-102">Overridable (Visual Basic)</span></span>
<span data-ttu-id="1a791-103">同じ名前のプロパティまたはプロシージャが派生クラスでオーバーライドできますプロパティまたはプロシージャを指定します。</span><span class="sxs-lookup"><span data-stu-id="1a791-103">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a791-104">コメント</span><span class="sxs-lookup"><span data-stu-id="1a791-104">Remarks</span></span>  
 <span data-ttu-id="1a791-105">`Overridable`修飾子により、派生クラスでオーバーライドするクラスでプロパティまたはメソッドです。</span><span class="sxs-lookup"><span data-stu-id="1a791-105">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="1a791-106">[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)修飾子プロパティまたはメソッドが派生クラスでオーバーライドされないできなくなります。</span><span class="sxs-lookup"><span data-stu-id="1a791-106">The [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="1a791-107">詳細については、「[継承の基本](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a791-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="1a791-108">場合、`Overridable`または`NotOverridable`修飾子が指定されていない、既定の設定は、プロパティまたはメソッドが基底クラスのプロパティまたはメソッドをオーバーライドするかどうかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="1a791-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="1a791-109">プロパティまたはメソッドは、基底クラスのプロパティまたはメソッドをオーバーライドする場合、既定値は`Overridable`です。 それ以外の場合は`NotOverridable`します。</span><span class="sxs-lookup"><span data-stu-id="1a791-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="1a791-110">シャドウまたは継承された要素を再定義するためにオーバーライドすることができますが、2 つの方法に大きな違いがあります。</span><span class="sxs-lookup"><span data-stu-id="1a791-110">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="1a791-111">詳細については、次を参照してください。 [Visual Basic におけるシャドウ](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)です。</span><span class="sxs-lookup"><span data-stu-id="1a791-111">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="1a791-112">オーバーライド可能な要素とも呼ば、*仮想*要素。</span><span class="sxs-lookup"><span data-stu-id="1a791-112">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="1a791-113">をオーバーライドすることができますが、する必要はありません、それとも呼びます、*具象*要素。</span><span class="sxs-lookup"><span data-stu-id="1a791-113">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="1a791-114">`Overridable` は、プロパティまたはプロシージャの宣言ステートメントでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="1a791-114">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="1a791-115">結合された修飾子</span><span class="sxs-lookup"><span data-stu-id="1a791-115">Combined Modifiers</span></span>  
 <span data-ttu-id="1a791-116">指定することはできません`Overridable`または`NotOverridable`の`Private`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="1a791-116">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="1a791-117">指定することはできません`Overridable`と共に`MustOverride`、 `NotOverridable`、または`Shared`同じ宣言内で。</span><span class="sxs-lookup"><span data-stu-id="1a791-117">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="1a791-118">オーバーライドする要素は暗黙的にオーバーライド可能であるため、`Overridable` と `Overrides` を結合することはできません。</span><span class="sxs-lookup"><span data-stu-id="1a791-118">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="1a791-119">使用法</span><span class="sxs-lookup"><span data-stu-id="1a791-119">Usage</span></span>  
 <span data-ttu-id="1a791-120">`Overridable` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="1a791-120">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="1a791-121">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="1a791-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="1a791-122">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="1a791-122">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="1a791-123">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="1a791-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="1a791-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="1a791-124">See Also</span></span>  
 [<span data-ttu-id="1a791-125">修飾子</span><span class="sxs-lookup"><span data-stu-id="1a791-125">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)  
 [<span data-ttu-id="1a791-126">継承の基本</span><span class="sxs-lookup"><span data-stu-id="1a791-126">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="1a791-127">MustOverride</span><span class="sxs-lookup"><span data-stu-id="1a791-127">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [<span data-ttu-id="1a791-128">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="1a791-128">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [<span data-ttu-id="1a791-129">Overrides</span><span class="sxs-lookup"><span data-stu-id="1a791-129">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="1a791-130">キーワード</span><span class="sxs-lookup"><span data-stu-id="1a791-130">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="1a791-131">Visual Basic におけるシャドウ</span><span class="sxs-lookup"><span data-stu-id="1a791-131">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
