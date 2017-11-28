---
title: "シール"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8caa253a3f17c58f542317de579c4f7832c4efac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sealing"></a><span data-ttu-id="20cb8-102">シール</span><span class="sxs-lookup"><span data-stu-id="20cb8-102">Sealing</span></span>
<span data-ttu-id="20cb8-103">オブジェクト指向フレームワークの機能の 1 つは、開発者が拡張およびフレームワークの設計者によって予期しない方法でカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="20cb8-103">One of the features of object-oriented frameworks is that developers can extend and customize them in ways unanticipated by the framework designers.</span></span> <span data-ttu-id="20cb8-104">これは、両方の電源および拡張可能なデザインの危険性です。</span><span class="sxs-lookup"><span data-stu-id="20cb8-104">This is both the power and danger of extensible design.</span></span> <span data-ttu-id="20cb8-105">フレームワークをデザインするときは、そのため、非常に重要が必要な場合、機能拡張を慎重に設計して危険である場合は、機能拡張を制限します。</span><span class="sxs-lookup"><span data-stu-id="20cb8-105">When you design your framework, it is, therefore, very important to carefully design for extensibility when it is desired, and to limit extensibility when it is dangerous.</span></span>  
  
 <span data-ttu-id="20cb8-106">拡張機能のことを防ぐ強力なメカニズムをシールするとします。</span><span class="sxs-lookup"><span data-stu-id="20cb8-106">A powerful mechanism that prevents extensibility is sealing.</span></span> <span data-ttu-id="20cb8-107">クラスまたは個々 のメンバーのいずれかを封印することができます。</span><span class="sxs-lookup"><span data-stu-id="20cb8-107">You can seal either the class or individual members.</span></span> <span data-ttu-id="20cb8-108">クラスをシールすると、ユーザーがクラスから継承できなくなります。</span><span class="sxs-lookup"><span data-stu-id="20cb8-108">Sealing a class prevents users from inheriting from the class.</span></span> <span data-ttu-id="20cb8-109">メンバーをシールすると、ユーザーが特定のメンバーをオーバーライドするできなくなります。</span><span class="sxs-lookup"><span data-stu-id="20cb8-109">Sealing a member prevents users from overriding a particular member.</span></span>  
  
 <span data-ttu-id="20cb8-110">**X しないで**これを行うには相応の理由をしなくてもクラスをシールします。</span><span class="sxs-lookup"><span data-stu-id="20cb8-110">**X DO NOT** seal classes without having a good reason to do so.</span></span>  
  
 <span data-ttu-id="20cb8-111">機能拡張シナリオを検討することはできませんので、クラスをシールが妥当な理由です。</span><span class="sxs-lookup"><span data-stu-id="20cb8-111">Sealing a class because you cannot think of an extensibility scenario is not a good reason.</span></span> <span data-ttu-id="20cb8-112">Framework ユーザーなどの便利なメンバーの追加など、さまざまな明確な理由のクラスから継承します。</span><span class="sxs-lookup"><span data-stu-id="20cb8-112">Framework users like to inherit from classes for various nonobvious reasons, like adding convenience members.</span></span> <span data-ttu-id="20cb8-113">参照してください[封印されていないクラス](../../../docs/standard/design-guidelines/unsealed-classes.md)明確な理由の例についてはユーザーが、型から継承します。</span><span class="sxs-lookup"><span data-stu-id="20cb8-113">See [Unsealed Classes](../../../docs/standard/design-guidelines/unsealed-classes.md) for examples of nonobvious reasons users want to inherit from a type.</span></span>  
  
 <span data-ttu-id="20cb8-114">クラスをシールする理由は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="20cb8-114">Good reasons for sealing a class include the following:</span></span>  
  
-   <span data-ttu-id="20cb8-115">クラスは、静的クラスです。</span><span class="sxs-lookup"><span data-stu-id="20cb8-115">The class is a static class.</span></span> <span data-ttu-id="20cb8-116">参照してください[静的クラスのデザイン](../../../docs/standard/design-guidelines/static-class.md)です。</span><span class="sxs-lookup"><span data-stu-id="20cb8-116">See [Static Class Design](../../../docs/standard/design-guidelines/static-class.md).</span></span>  
  
-   <span data-ttu-id="20cb8-117">クラスは、継承されたプロテクト メンバーにセキュリティ上重要な機密情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="20cb8-117">The class stores security-sensitive secrets in inherited protected members.</span></span>  
  
-   <span data-ttu-id="20cb8-118">クラスは多くの仮想メンバーを継承し、それらを個別に封印のコストは封印されていないクラスを残すことの利点を上回ります。</span><span class="sxs-lookup"><span data-stu-id="20cb8-118">The class inherits many virtual members and the cost of sealing them individually would outweigh the benefits of leaving the class unsealed.</span></span>  
  
-   <span data-ttu-id="20cb8-119">クラスは、非常に高速なランタイム ルックアップが必要な属性です。</span><span class="sxs-lookup"><span data-stu-id="20cb8-119">The class is an attribute that requires very fast runtime look-up.</span></span> <span data-ttu-id="20cb8-120">Sealed 属性では、封印されていないものよりもわずかに高いパフォーマンス レベルがあります。</span><span class="sxs-lookup"><span data-stu-id="20cb8-120">Sealed attributes have slightly higher performance levels than unsealed ones.</span></span> <span data-ttu-id="20cb8-121">参照してください[属性](../../../docs/standard/design-guidelines/attributes.md)です。</span><span class="sxs-lookup"><span data-stu-id="20cb8-121">See [Attributes](../../../docs/standard/design-guidelines/attributes.md).</span></span>  
  
 <span data-ttu-id="20cb8-122">**X しないで**sealed 型でプロテクト メンバーまたは仮想メンバーを宣言します。</span><span class="sxs-lookup"><span data-stu-id="20cb8-122">**X DO NOT** declare protected or virtual members on sealed types.</span></span>  
  
 <span data-ttu-id="20cb8-123">定義上、シールされた型から継承できません。</span><span class="sxs-lookup"><span data-stu-id="20cb8-123">By definition, sealed types cannot be inherited from.</span></span> <span data-ttu-id="20cb8-124">つまり、sealed 型でプロテクト メンバーを呼び出すことはできません、sealed 型で仮想メソッドをオーバーライドすることはできません。</span><span class="sxs-lookup"><span data-stu-id="20cb8-124">This means that protected members on sealed types cannot be called, and virtual methods on sealed types cannot be overridden.</span></span>  
  
 <span data-ttu-id="20cb8-125">**✓ を検討してください**をオーバーライドするメンバーをシールします。</span><span class="sxs-lookup"><span data-stu-id="20cb8-125">**✓ CONSIDER** sealing members that you override.</span></span>  
  
 <span data-ttu-id="20cb8-126">仮想メンバーの概要に起因する問題 (で説明した[仮想メンバー](../../../docs/standard/design-guidelines/virtual-members.md)) 若干程度が同様に、上書きを適用します。</span><span class="sxs-lookup"><span data-stu-id="20cb8-126">Problems that can result from introducing virtual members (discussed in [Virtual Members](../../../docs/standard/design-guidelines/virtual-members.md)) apply to overrides as well, although to a slightly lesser degree.</span></span> <span data-ttu-id="20cb8-127">上書きが封印、継承階層の時点からこれらの問題から保護します。</span><span class="sxs-lookup"><span data-stu-id="20cb8-127">Sealing an override shields you from these problems starting from that point in the inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="20cb8-128">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="20cb8-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="20cb8-129">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="20cb8-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20cb8-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="20cb8-130">See Also</span></span>  
 [<span data-ttu-id="20cb8-131">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="20cb8-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="20cb8-132">機能拡張のための設計</span><span class="sxs-lookup"><span data-stu-id="20cb8-132">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [<span data-ttu-id="20cb8-133">封印されていないクラス</span><span class="sxs-lookup"><span data-stu-id="20cb8-133">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)
