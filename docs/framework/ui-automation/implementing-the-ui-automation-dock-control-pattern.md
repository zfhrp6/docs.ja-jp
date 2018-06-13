---
title: UI オートメーション Dock コントロール パターンの実装
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 9e04814885ae0963d4da99acecf00dc646ecc96f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400732"
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a><span data-ttu-id="14a55-102">UI オートメーション Dock コントロール パターンの実装</span><span class="sxs-lookup"><span data-stu-id="14a55-102">Implementing the UI Automation Dock Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="14a55-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="14a55-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="14a55-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14a55-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="14a55-105">ここでは、プロパティに関する情報など、 <xref:System.Windows.Automation.Provider.IDockProvider>を実装するガイドラインと規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="14a55-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IDockProvider>, including information about properties.</span></span> <span data-ttu-id="14a55-106">その他のリファレンスへのリンクは、トピックの最後に記載します。</span><span class="sxs-lookup"><span data-stu-id="14a55-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="14a55-107"><xref:System.Windows.Automation.DockPattern> コントロール パターンは、ドッキング コンテナー内のコントロールのドッキング プロパティを公開するために使用します。</span><span class="sxs-lookup"><span data-stu-id="14a55-107">The <xref:System.Windows.Automation.DockPattern> control pattern is used to expose the dock properties of a control within a docking container.</span></span> <span data-ttu-id="14a55-108">ドッキング コンテナーは、子要素を互いに水平方向または垂直方向に整列できるコントロールです。</span><span class="sxs-lookup"><span data-stu-id="14a55-108">A docking container is a control that allows you to arrange child elements horizontally and vertically, relative to each other.</span></span> <span data-ttu-id="14a55-109">このコントロール パターンを実装するコントロールの例については、「 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="14a55-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
 <span data-ttu-id="14a55-110">![ドッキング コンテナーは、ドッキングされた 2 つの子にします。] (../../../docs/framework/ui-automation/media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")</span><span class="sxs-lookup"><span data-stu-id="14a55-110">![Docking container with two docked children.](../../../docs/framework/ui-automation/media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")</span></span>  
<span data-ttu-id="14a55-111">"Class View" ウィンドウが DockPosition.Right に "Error List" ウィンドウが DockPosition.Bottom にそれぞれ配置された Visual Studio のドッキングの例</span><span class="sxs-lookup"><span data-stu-id="14a55-111">Docking Example from Visual Studio Where "Class View" Window Is DockPosition.Right and "Error List" Window Is DockPosition.Bottom</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="14a55-112">実装のガイドラインと規則</span><span class="sxs-lookup"><span data-stu-id="14a55-112">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="14a55-113">Dock コントロール パターンを実装する場合は、次のガイドラインと規則に注意してください。</span><span class="sxs-lookup"><span data-stu-id="14a55-113">When implementing the Dock control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="14a55-114"><xref:System.Windows.Automation.Provider.IDockProvider> は、ドッキング コンテナーのプロパティや、ドッキング コンテナー内の現在のコントロールに隣接してドッキングされるコントロールのプロパティは公開しません。</span><span class="sxs-lookup"><span data-stu-id="14a55-114"><xref:System.Windows.Automation.Provider.IDockProvider> does not expose any properties of the docking container or any properties of controls that are docked adjacent to the current control within the docking container.</span></span>  
  
-   <span data-ttu-id="14a55-115">コントロールは、現在の重ね順に基づき、互いを基準としてドッキングされます。重ね順が上位であるほど、指定されたドッキング コンテナーの端から離れた位置に配置されます。</span><span class="sxs-lookup"><span data-stu-id="14a55-115">Controls are docked relative to each other based on their current z-order; the higher their z-order placement, the farther they are placed from the specified edge of the docking container.</span></span>  
  
-   <span data-ttu-id="14a55-116">ドッキング コンテナーのサイズを変更すると、コンテナー内にドッキングされているコントロールは、もともとドッキングされていたのと同じ端に合わせて再配置されます。</span><span class="sxs-lookup"><span data-stu-id="14a55-116">If the docking container is resized, any docked controls within the container will be repositioned flush to the same edge to which they were originally docked.</span></span> <span data-ttu-id="14a55-117">また、ドッキングされているコントロールは、 <xref:System.Windows.Automation.DockPosition>のドッキング動作に従って、コンテナー内のスペースを埋めるようにサイズ変更されます。</span><span class="sxs-lookup"><span data-stu-id="14a55-117">The docked controls will also resize to fill any space within the container according to the docking behavior of their <xref:System.Windows.Automation.DockPosition>.</span></span> <span data-ttu-id="14a55-118">たとえば、 <xref:System.Windows.Automation.DockPosition.Top> が指定されている場合は、コントロールの左側と右側が広がって、使用できるスペースを埋めます。</span><span class="sxs-lookup"><span data-stu-id="14a55-118">For example, if <xref:System.Windows.Automation.DockPosition.Top> is specified, the left and right sides of the control will expand to fill any available space.</span></span> <span data-ttu-id="14a55-119"><xref:System.Windows.Automation.DockPosition.Fill> が指定されている場合は、コントロールの 4 つの側面すべてが広がって、使用できるスペースを埋めます。</span><span class="sxs-lookup"><span data-stu-id="14a55-119">If <xref:System.Windows.Automation.DockPosition.Fill> is specified, all four sides of the control will expand to fill any available space.</span></span>  
  
-   <span data-ttu-id="14a55-120">マルチモニター システムでは、コントロールは現在のモニターの左側または右側にドッキングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="14a55-120">On a multi-monitor system, controls should dock to the left or right side of the current monitor.</span></span> <span data-ttu-id="14a55-121">それが不可能な場合は、左端のモニターの左側、または右端のモニターの右側にドッキングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="14a55-121">If that is not possible, they should dock to the left side of the leftmost monitor or the right side of the rightmost monitor.</span></span>  
  
<a name="Required_Members_for_IDockProvider"></a>   
## <a name="required-members-for-idockprovider"></a><span data-ttu-id="14a55-122">IDockProvider の必須メンバー</span><span class="sxs-lookup"><span data-stu-id="14a55-122">Required Members for IDockProvider</span></span>  
 <span data-ttu-id="14a55-123">次のプロパティとメソッドは、IDockProvider インターフェイスの実装時に必要です。</span><span class="sxs-lookup"><span data-stu-id="14a55-123">The following properties and methods are required for implementing the IDockProvider interface.</span></span>  
  
|<span data-ttu-id="14a55-124">必須メンバー</span><span class="sxs-lookup"><span data-stu-id="14a55-124">Required members</span></span>|<span data-ttu-id="14a55-125">メンバーの型</span><span class="sxs-lookup"><span data-stu-id="14a55-125">Member type</span></span>|<span data-ttu-id="14a55-126">メモ</span><span class="sxs-lookup"><span data-stu-id="14a55-126">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|<span data-ttu-id="14a55-127">プロパティ</span><span class="sxs-lookup"><span data-stu-id="14a55-127">Property</span></span>|<span data-ttu-id="14a55-128">なし</span><span class="sxs-lookup"><span data-stu-id="14a55-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|<span data-ttu-id="14a55-129">メソッド</span><span class="sxs-lookup"><span data-stu-id="14a55-129">Method</span></span>|<span data-ttu-id="14a55-130">なし</span><span class="sxs-lookup"><span data-stu-id="14a55-130">None</span></span>|  
  
 <span data-ttu-id="14a55-131">このコントロール パターンには、関連するイベントがありません。</span><span class="sxs-lookup"><span data-stu-id="14a55-131">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="14a55-132">例外</span><span class="sxs-lookup"><span data-stu-id="14a55-132">Exceptions</span></span>  
 <span data-ttu-id="14a55-133">プロバイダーは、次の例外をスローする必要があります。</span><span class="sxs-lookup"><span data-stu-id="14a55-133">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="14a55-134">例外の種類</span><span class="sxs-lookup"><span data-stu-id="14a55-134">Exception type</span></span>|<span data-ttu-id="14a55-135">条件</span><span class="sxs-lookup"><span data-stu-id="14a55-135">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> <span data-ttu-id="14a55-136">場合、コントロールは、要求されたドッキング スタイルを実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="14a55-136">-   When a control is not able to execute the requested dock style.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14a55-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="14a55-137">See Also</span></span>  
 [<span data-ttu-id="14a55-138">UI Automation コントロール パターンの概要</span><span class="sxs-lookup"><span data-stu-id="14a55-138">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="14a55-139">UI オートメーション プロバイダーでのコントロール パターンのサポート</span><span class="sxs-lookup"><span data-stu-id="14a55-139">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="14a55-140">クライアントの UI オートメーション コントロール パターン</span><span class="sxs-lookup"><span data-stu-id="14a55-140">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="14a55-141">UI Automation ツリーの概要</span><span class="sxs-lookup"><span data-stu-id="14a55-141">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="14a55-142">UI オートメーションにおけるキャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="14a55-142">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
