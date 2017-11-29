---
title: NotOverridable (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.NotOverridable
- NotOverridable
helpviewer_keywords:
- sealed methods [Visual Basic]
- NotOverridable keyword [Visual Basic]
- properties [Visual Basic], redefining
- elements [Visual Basic], sealed
- sealed [elements VB]
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- methods [Visual Basic], sealed
- properties [Visual Basic], overriding
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6fc5fb006b36cda1b6ad0e128604bc3bb427fd94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="notoverridable-visual-basic"></a><span data-ttu-id="a1ce1-102">NotOverridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1ce1-102">NotOverridable (Visual Basic)</span></span>
<span data-ttu-id="a1ce1-103">プロパティまたはプロシージャを派生クラスでオーバーライドできないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="a1ce1-103">Specifies that a property or procedure cannot be overridden in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1ce1-104">コメント</span><span class="sxs-lookup"><span data-stu-id="a1ce1-104">Remarks</span></span>  
 <span data-ttu-id="a1ce1-105">`NotOverridable`修飾子プロパティまたはメソッドが派生クラスでオーバーライドされないできなくなります。</span><span class="sxs-lookup"><span data-stu-id="a1ce1-105">The `NotOverridable` modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="a1ce1-106">[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)修飾子により、派生クラスでオーバーライドするクラスでプロパティまたはメソッドです。</span><span class="sxs-lookup"><span data-stu-id="a1ce1-106">The [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="a1ce1-107">詳細については、「[継承の基本](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1ce1-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="a1ce1-108">場合、`Overridable`または`NotOverridable`修飾子が指定されていない、既定の設定は、プロパティまたはメソッドが基底クラスのプロパティまたはメソッドをオーバーライドするかどうかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="a1ce1-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="a1ce1-109">プロパティまたはメソッドは、基底クラスのプロパティまたはメソッドをオーバーライドする場合、既定値は`Overridable`です。 それ以外の場合は`NotOverridable`します。</span><span class="sxs-lookup"><span data-stu-id="a1ce1-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="a1ce1-110">上書きできないように要素と呼ぶことが、*シール*要素。</span><span class="sxs-lookup"><span data-stu-id="a1ce1-110">An element that cannot be overridden is sometimes called a *sealed* element.</span></span>  
  
 <span data-ttu-id="a1ce1-111">`NotOverridable` は、プロパティまたはプロシージャの宣言ステートメントでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a1ce1-111">You can use `NotOverridable` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="a1ce1-112">指定できます`NotOverridable`プロパティまたはとの組み合わせでのみ、つまり、別のプロパティまたはプロシージャをオーバーライドするプロシージャでのみ`Overrides`です。</span><span class="sxs-lookup"><span data-stu-id="a1ce1-112">You can specify `NotOverridable` only on a property or procedure that overrides another property or procedure, that is, only in combination with `Overrides`.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="a1ce1-113">結合された修飾子</span><span class="sxs-lookup"><span data-stu-id="a1ce1-113">Combined Modifiers</span></span>  
 <span data-ttu-id="a1ce1-114">指定することはできません`Overridable`または`NotOverridable`の`Private`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="a1ce1-114">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="a1ce1-115">指定することはできません`NotOverridable`と共に`MustOverride`、 `Overridable`、または`Shared`同じ宣言内で。</span><span class="sxs-lookup"><span data-stu-id="a1ce1-115">You cannot specify `NotOverridable` together with `MustOverride`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="a1ce1-116">使用方法</span><span class="sxs-lookup"><span data-stu-id="a1ce1-116">Usage</span></span>  
 <span data-ttu-id="a1ce1-117">`NotOverridable` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="a1ce1-117">The `NotOverridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="a1ce1-118">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="a1ce1-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="a1ce1-119">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="a1ce1-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="a1ce1-120">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="a1ce1-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="a1ce1-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1ce1-121">See Also</span></span>  
 [<span data-ttu-id="a1ce1-122">修飾子</span><span class="sxs-lookup"><span data-stu-id="a1ce1-122">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)  
 [<span data-ttu-id="a1ce1-123">継承の基本</span><span class="sxs-lookup"><span data-stu-id="a1ce1-123">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="a1ce1-124">MustOverride</span><span class="sxs-lookup"><span data-stu-id="a1ce1-124">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [<span data-ttu-id="a1ce1-125">Overridable</span><span class="sxs-lookup"><span data-stu-id="a1ce1-125">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [<span data-ttu-id="a1ce1-126">Overrides</span><span class="sxs-lookup"><span data-stu-id="a1ce1-126">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="a1ce1-127">キーワード</span><span class="sxs-lookup"><span data-stu-id="a1ce1-127">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="a1ce1-128">Visual Basic におけるシャドウ</span><span class="sxs-lookup"><span data-stu-id="a1ce1-128">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
