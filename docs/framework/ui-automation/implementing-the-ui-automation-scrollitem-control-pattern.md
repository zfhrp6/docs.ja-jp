---
title: "UI オートメーション ScrollItem コントロール パターンの実装"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Scroll Item
- UI Automation, Scroll Item control pattern
- Scroll Item control pattern
ms.assetid: 903bab5c-80c1-44d7-bdc2-0a418893b987
caps.latest.revision: "16"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 92c3b4fad775dcd04299e18da126107d8fbb4471
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-scrollitem-control-pattern"></a><span data-ttu-id="cc646-102">UI オートメーション ScrollItem コントロール パターンの実装</span><span class="sxs-lookup"><span data-stu-id="cc646-102">Implementing the UI Automation ScrollItem Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="cc646-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="cc646-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="cc646-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc646-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="cc646-105">このトピックのガイドラインと規則を実装するための紹介、<xref:System.Windows.Automation.Provider.IScrollItemProvider>プロパティ、メソッド、およびイベントに関する情報などです。</span><span class="sxs-lookup"><span data-stu-id="cc646-105">This topic introduces guidelines and conventions for implementing the <xref:System.Windows.Automation.Provider.IScrollItemProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="cc646-106">その他のリファレンスへのリンクは、トピックの最後に記載します。</span><span class="sxs-lookup"><span data-stu-id="cc646-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="cc646-107"><xref:System.Windows.Automation.ScrollItemPattern>コントロール パターンを実装するコンテナーの各子コントロールをサポートするために使用<xref:System.Windows.Automation.Provider.IScrollProvider>です。</span><span class="sxs-lookup"><span data-stu-id="cc646-107">The <xref:System.Windows.Automation.ScrollItemPattern> control pattern is used to support individual child controls of containers that implement <xref:System.Windows.Automation.Provider.IScrollProvider>.</span></span> <span data-ttu-id="cc646-108">このコントロール パターンは、子コントロールとそのコンテナーの間の通信チャネルとして機能することで、ビューポート内に現在表示されているコンテンツ (または領域) がコンテナーによって確実に変更され、子コントロールが表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="cc646-108">This control pattern acts as a communication channel between a child control and its container to ensure that the container can change the currently visible content (or region) within its viewport to display the child control.</span></span> <span data-ttu-id="cc646-109">このコントロール パターンを実装するコントロールの例については、「 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cc646-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="cc646-110">実装のガイドラインと規則</span><span class="sxs-lookup"><span data-stu-id="cc646-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="cc646-111">スクロール項目コントロール パターンを実装する場合は、次のガイドラインと規則にご留意ください。</span><span class="sxs-lookup"><span data-stu-id="cc646-111">When implementing the Scroll Item control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="cc646-112">ウィンドウ コントロールまたはキャンバス コントロール内の項目で、IScrollItemProvider インターフェイスを実装する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="cc646-112">Items contained within a Window or Canvas control are not required to implement the IScrollItemProvider interface.</span></span> <span data-ttu-id="cc646-113">代わりに、ただし、必要がありますを公開している有効な場所、<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>です。</span><span class="sxs-lookup"><span data-stu-id="cc646-113">As an alternative, however, they must expose a valid location for the <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.</span></span> <span data-ttu-id="cc646-114">これによりを使用する UI オートメーション クライアント アプリケーション、<xref:System.Windows.Automation.ScrollPattern>子項目を表示するコンテナーでのパターンのメソッドを制御します。</span><span class="sxs-lookup"><span data-stu-id="cc646-114">This will allow a UI Automation client application to use the <xref:System.Windows.Automation.ScrollPattern> control pattern methods on the container to display the child item.</span></span>  
  
<a name="Required_Members_for_IScrollItemProvider"></a>   
## <a name="required-members-for-iscrollitemprovider"></a><span data-ttu-id="cc646-115">IScrollItemProvider の必須メンバー</span><span class="sxs-lookup"><span data-stu-id="cc646-115">Required Members for IScrollItemProvider</span></span>  
 <span data-ttu-id="cc646-116">IScrollProvider インターフェイスを実装するには、次のメソッドが必要です。</span><span class="sxs-lookup"><span data-stu-id="cc646-116">The following method is required for implementing the IScrollProvider interface.</span></span>  
  
|<span data-ttu-id="cc646-117">必須メンバー</span><span class="sxs-lookup"><span data-stu-id="cc646-117">Required members</span></span>|<span data-ttu-id="cc646-118">メンバーの型</span><span class="sxs-lookup"><span data-stu-id="cc646-118">Member type</span></span>|<span data-ttu-id="cc646-119">メモ</span><span class="sxs-lookup"><span data-stu-id="cc646-119">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider.ScrollIntoView%2A>|<span data-ttu-id="cc646-120">メソッド</span><span class="sxs-lookup"><span data-stu-id="cc646-120">-   Method</span></span>|<span data-ttu-id="cc646-121">なし</span><span class="sxs-lookup"><span data-stu-id="cc646-121">None</span></span>|  
  
 <span data-ttu-id="cc646-122">このコントロール パターンに関連付けられるプロパティやイベントはありません。</span><span class="sxs-lookup"><span data-stu-id="cc646-122">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="cc646-123">例外</span><span class="sxs-lookup"><span data-stu-id="cc646-123">Exceptions</span></span>  
 <span data-ttu-id="cc646-124">プロバイダーは、次の例外をスローする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc646-124">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="cc646-125">例外の種類</span><span class="sxs-lookup"><span data-stu-id="cc646-125">Exception Type</span></span>|<span data-ttu-id="cc646-126">状態</span><span class="sxs-lookup"><span data-stu-id="cc646-126">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<span data-ttu-id="cc646-127">項目をビューにスクロールできない場合:</span><span class="sxs-lookup"><span data-stu-id="cc646-127">If an item cannot be scrolled into view:</span></span><br /><br /> -   <xref:System.Windows.Automation.ScrollItemPattern.ScrollIntoView%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="cc646-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc646-128">See Also</span></span>  
 [<span data-ttu-id="cc646-129">UI オートメーション コントロール パターンの概要</span><span class="sxs-lookup"><span data-stu-id="cc646-129">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="cc646-130">UI オートメーション プロバイダーでコントロール パターンをサポートします。</span><span class="sxs-lookup"><span data-stu-id="cc646-130">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="cc646-131">クライアントの UI オートメーション コントロール パターン</span><span class="sxs-lookup"><span data-stu-id="cc646-131">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="cc646-132">UI オートメーション ツリーの概要</span><span class="sxs-lookup"><span data-stu-id="cc646-132">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="cc646-133">UI オートメーションにおけるキャッシュを使用します。</span><span class="sxs-lookup"><span data-stu-id="cc646-133">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
