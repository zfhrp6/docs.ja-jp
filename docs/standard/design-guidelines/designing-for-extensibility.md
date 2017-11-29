---
title: "機能拡張のデザイン"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dbee2fb24b9acf9bc2512b399e3a74e66720cc3c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="designing-for-extensibility"></a><span data-ttu-id="5bcd7-102">機能拡張のデザイン</span><span class="sxs-lookup"><span data-stu-id="5bcd7-102">Designing for Extensibility</span></span>
<span data-ttu-id="5bcd7-103">フレームワーク設計の 1 つの重要な側面を行って、フレームワークの拡張性が慎重に考慮されていることを確認しています。</span><span class="sxs-lookup"><span data-stu-id="5bcd7-103">One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered.</span></span> <span data-ttu-id="5bcd7-104">これは、コストとさまざまな機能拡張メカニズムに関連付けられている利点を理解することが必要です。</span><span class="sxs-lookup"><span data-stu-id="5bcd7-104">This requires that you understand the costs and benefits associated with various extensibility mechanisms.</span></span> <span data-ttu-id="5bcd7-105">この章では、機能拡張メカニズムを判断するのに役立ちます: サブクラス化、イベント、仮想メンバー、コールバック、およびなど —、framework の要件を満たす最適なことができます。</span><span class="sxs-lookup"><span data-stu-id="5bcd7-105">This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.</span></span>  
  
 <span data-ttu-id="5bcd7-106">フレームワークの機能拡張を許可する方法はたくさんあります。</span><span class="sxs-lookup"><span data-stu-id="5bcd7-106">There are many ways to allow extensibility in frameworks.</span></span> <span data-ttu-id="5bcd7-107">コストが非常に強力に低コストの低いから範囲です。</span><span class="sxs-lookup"><span data-stu-id="5bcd7-107">They range from less powerful but less costly to very powerful but expensive.</span></span> <span data-ttu-id="5bcd7-108">、特定の機能拡張必要条件については、要件を満たす低コストの機能拡張メカニズムを選択してください。</span><span class="sxs-lookup"><span data-stu-id="5bcd7-108">For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements.</span></span> <span data-ttu-id="5bcd7-109">通常、後で、複数の機能拡張を追加することが可能であるが、重大な変更を導入することがなく離れた実行しないことができますに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5bcd7-109">Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5bcd7-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="5bcd7-110">In This Section</span></span>  
 [<span data-ttu-id="5bcd7-111">封印されていないクラス</span><span class="sxs-lookup"><span data-stu-id="5bcd7-111">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [<span data-ttu-id="5bcd7-112">保護されたメンバー</span><span class="sxs-lookup"><span data-stu-id="5bcd7-112">Protected Members</span></span>](../../../docs/standard/design-guidelines/protected-members.md)  
 [<span data-ttu-id="5bcd7-113">イベントやコールバック</span><span class="sxs-lookup"><span data-stu-id="5bcd7-113">Events and Callbacks</span></span>](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [<span data-ttu-id="5bcd7-114">仮想メンバー</span><span class="sxs-lookup"><span data-stu-id="5bcd7-114">Virtual Members</span></span>](../../../docs/standard/design-guidelines/virtual-members.md)  
 [<span data-ttu-id="5bcd7-115">抽象クラス (抽象型とインターフェイス)</span><span class="sxs-lookup"><span data-stu-id="5bcd7-115">Abstractions (Abstract Types and Interfaces)</span></span>](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [<span data-ttu-id="5bcd7-116">抽象化を実装するための基本クラス</span><span class="sxs-lookup"><span data-stu-id="5bcd7-116">Base Classes for Implementing Abstractions</span></span>](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [<span data-ttu-id="5bcd7-117">封印</span><span class="sxs-lookup"><span data-stu-id="5bcd7-117">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)  
 <span data-ttu-id="5bcd7-118">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="5bcd7-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="5bcd7-119">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="5bcd7-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bcd7-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="5bcd7-120">See Also</span></span>  
 [<span data-ttu-id="5bcd7-121">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="5bcd7-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
