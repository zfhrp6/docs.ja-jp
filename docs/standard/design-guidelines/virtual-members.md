---
title: 仮想メンバー
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fa4227fc4476b86f07216650b22fccc25af7dd98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="virtual-members"></a><span data-ttu-id="f3314-102">仮想メンバー</span><span class="sxs-lookup"><span data-stu-id="f3314-102">Virtual Members</span></span>
<span data-ttu-id="f3314-103">したがって、サブクラスの動作を変更する、仮想メンバーをオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="f3314-103">Virtual members can be overridden, thus changing the behavior of the subclass.</span></span> <span data-ttu-id="f3314-104">それらは、拡張性の観点からのコールバックを非常に似ていますが、実行のパフォーマンスとメモリ消費量の観点から優れています。</span><span class="sxs-lookup"><span data-stu-id="f3314-104">They are quite similar to callbacks in terms of the extensibility they provide, but they are better in terms of execution performance and memory consumption.</span></span> <span data-ttu-id="f3314-105">また、仮想メンバーは、特殊な既存の型 (特殊化) の種類を作成する必要があるシナリオで複数な操作です。</span><span class="sxs-lookup"><span data-stu-id="f3314-105">Also, virtual members feel more natural in scenarios that require creating a special kind of an existing type (specialization).</span></span>  
  
 <span data-ttu-id="f3314-106">仮想メンバーはコールバックとイベントをよりパフォーマンスが向上しますが、非仮想メソッドをより実行しません。</span><span class="sxs-lookup"><span data-stu-id="f3314-106">Virtual members perform better than callbacks and events, but do not perform better than non-virtual methods.</span></span>  
  
 <span data-ttu-id="f3314-107">仮想メンバーの主な欠点は、仮想メンバーの動作はコンパイル時にのみ変更できます。</span><span class="sxs-lookup"><span data-stu-id="f3314-107">The main disadvantage of virtual members is that the behavior of a virtual member can only be modified at the time of compilation.</span></span> <span data-ttu-id="f3314-108">実行時に、コールバックの動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="f3314-108">The behavior of a callback can be modified at runtime.</span></span>  
  
 <span data-ttu-id="f3314-109">コールバック (やその他のコールバックより) と同様に、仮想メンバーは、設計、テスト、および仮想メンバーへの呼び出しが予測できない方法でオーバーライドされることができ、任意のコードを実行できるため維持にコストがかかる。</span><span class="sxs-lookup"><span data-stu-id="f3314-109">Virtual members, like callbacks (and maybe more than callbacks), are costly to design, test, and maintain because any call to a virtual member can be overridden in unpredictable ways and can execute arbitrary code.</span></span> <span data-ttu-id="f3314-110">またより多くの労力は通常、設計およびそれらを文書化のコストが高いため、仮想メンバーの契約を明確に定義する要求されます。</span><span class="sxs-lookup"><span data-stu-id="f3314-110">Also, much more effort is usually required to clearly define the contract of virtual members, so the cost of designing and documenting them is higher.</span></span>  
  
 <span data-ttu-id="f3314-111">**X しないで**これを行うには相応の理由があり、デザイン、テスト、および仮想メンバーを保守に関連するすべてのコストを認識している限り、メンバーを仮想にすることです。</span><span class="sxs-lookup"><span data-stu-id="f3314-111">**X DO NOT** make members virtual unless you have a good reason to do so and you are aware of all the costs related to designing, testing, and maintaining virtual members.</span></span>  
  
 <span data-ttu-id="f3314-112">仮想メンバーは、互換性の問題なしに作成できる変更の観点からありました。</span><span class="sxs-lookup"><span data-stu-id="f3314-112">Virtual members are less forgiving in terms of changes that can be made to them without breaking compatibility.</span></span> <span data-ttu-id="f3314-113">また、これらはよりも遅い非仮想メンバーは、仮想メンバーへの呼び出しはインライン関数ではないため、ほとんどの場合です。</span><span class="sxs-lookup"><span data-stu-id="f3314-113">Also, they are slower than non-virtual members, mostly because calls to virtual members are not inlined.</span></span>  
  
 <span data-ttu-id="f3314-114">**✓ を検討してください**に何がどうしても必要なだけの機能拡張を制限します。</span><span class="sxs-lookup"><span data-stu-id="f3314-114">**✓ CONSIDER** limiting extensibility to only what is absolutely necessary.</span></span>  
  
 <span data-ttu-id="f3314-115">**✓ しないで**仮想メンバーのアクセシビリティは public で保護されたアクセシビリティを優先します。</span><span class="sxs-lookup"><span data-stu-id="f3314-115">**✓ DO** prefer protected accessibility over public accessibility for virtual members.</span></span> <span data-ttu-id="f3314-116">パブリック メンバーは拡張機能を提供 (必要な場合) プロテクト仮想メンバーを呼び出すことによってです。</span><span class="sxs-lookup"><span data-stu-id="f3314-116">Public members should provide extensibility (if required) by calling into a protected virtual member.</span></span>  
  
 <span data-ttu-id="f3314-117">クラスのパブリック メンバーは、そのクラスの直接のコンシューマーを適切な機能のセットを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3314-117">The public members of a class should provide the right set of functionality for direct consumers of that class.</span></span> <span data-ttu-id="f3314-118">仮想メンバーは、サブクラスでオーバーライドされるように設計されていて、保護されたアクセシビリティがスコープを使用する場所のすべての仮想機能拡張ポイントを有効にします。</span><span class="sxs-lookup"><span data-stu-id="f3314-118">Virtual members are designed to be overridden in subclasses, and protected accessibility is a great way to scope all virtual extensibility points to where they can be used.</span></span>  
  
 <span data-ttu-id="f3314-119">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="f3314-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="f3314-120">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="f3314-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3314-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3314-121">See Also</span></span>  
 [<span data-ttu-id="f3314-122">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="f3314-122">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="f3314-123">機能拡張のデザイン</span><span class="sxs-lookup"><span data-stu-id="f3314-123">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
