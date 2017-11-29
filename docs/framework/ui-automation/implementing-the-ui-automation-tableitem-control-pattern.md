---
title: "UI オートメーション TableItem コントロール パターンの実装"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
caps.latest.revision: "14"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 5861ab24627f9b78cd20f97fcdb1b1b3d681991a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a><span data-ttu-id="8ba69-102">UI オートメーション TableItem コントロール パターンの実装</span><span class="sxs-lookup"><span data-stu-id="8ba69-102">Implementing the UI Automation TableItem Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="8ba69-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="8ba69-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8ba69-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](http://go.microsoft.com/fwlink/?LinkID=156746)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8ba69-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="8ba69-105">このトピックのガイドラインと規則を実装するための導入<xref:System.Windows.Automation.Provider.ITableItemProvider>、イベントおよびプロパティに関する情報も含まれます。</span><span class="sxs-lookup"><span data-stu-id="8ba69-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableItemProvider>, including information about events and properties.</span></span> <span data-ttu-id="8ba69-106">その他のリファレンスへのリンクは、概要の最後に記載します。</span><span class="sxs-lookup"><span data-stu-id="8ba69-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="8ba69-107"><xref:System.Windows.Automation.TableItemPattern>コントロール パターンを実装するコンテナーの子コントロールをサポートするために使用<xref:System.Windows.Automation.Provider.ITableProvider>です。</span><span class="sxs-lookup"><span data-stu-id="8ba69-107">The <xref:System.Windows.Automation.TableItemPattern> control pattern is used to support child controls of containers that implement <xref:System.Windows.Automation.Provider.ITableProvider>.</span></span> <span data-ttu-id="8ba69-108">個々 のセル機能へのアクセスが必要な同時実装によって提供される<xref:System.Windows.Automation.Provider.IGridItemProvider>です。</span><span class="sxs-lookup"><span data-stu-id="8ba69-108">Access to individual cell functionality is provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridItemProvider>.</span></span> <span data-ttu-id="8ba69-109">このコントロール パターンはに似て<xref:System.Windows.Automation.Provider.IGridItemProvider>を実装するコントロールを除いて、<xref:System.Windows.Automation.Provider.ITableItemProvider>プログラムによって、個々 のセルとその行および列情報間のリレーションシップを公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ba69-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridItemProvider> with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableItemProvider> must programmatically expose the relationship between the individual cell and its row and column information.</span></span> <span data-ttu-id="8ba69-110">このコントロール パターンを実装するコントロールの例については、「 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8ba69-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="8ba69-111">実装のガイドラインと規則</span><span class="sxs-lookup"><span data-stu-id="8ba69-111">Implementation Guidelines and Conventions</span></span>  
  
-   <span data-ttu-id="8ba69-112">関連するグリッド項目機能では、次を参照してください。 [UI オートメーション GridItem コントロール パターンを実装する](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)です。</span><span class="sxs-lookup"><span data-stu-id="8ba69-112">For related grid item functionality, see [Implementing the UI Automation GridItem Control Pattern](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md).</span></span>  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a><span data-ttu-id="8ba69-113">ITableItemProvider の必須メンバー</span><span class="sxs-lookup"><span data-stu-id="8ba69-113">Required Members for ITableItemProvider</span></span>  
  
|<span data-ttu-id="8ba69-114">必須メンバー</span><span class="sxs-lookup"><span data-stu-id="8ba69-114">Required member</span></span>|<span data-ttu-id="8ba69-115">メンバーの型</span><span class="sxs-lookup"><span data-stu-id="8ba69-115">Member type</span></span>|<span data-ttu-id="8ba69-116">ノート</span><span class="sxs-lookup"><span data-stu-id="8ba69-116">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|<span data-ttu-id="8ba69-117">メソッド</span><span class="sxs-lookup"><span data-stu-id="8ba69-117">Method</span></span>|<span data-ttu-id="8ba69-118">なし</span><span class="sxs-lookup"><span data-stu-id="8ba69-118">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|<span data-ttu-id="8ba69-119">メソッド</span><span class="sxs-lookup"><span data-stu-id="8ba69-119">Method</span></span>|<span data-ttu-id="8ba69-120">なし</span><span class="sxs-lookup"><span data-stu-id="8ba69-120">None</span></span>|  
  
 <span data-ttu-id="8ba69-121">このコントロール パターンに関連付けられるプロパティやイベントはありません。</span><span class="sxs-lookup"><span data-stu-id="8ba69-121">This control pattern has no associated properties or events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="8ba69-122">例外</span><span class="sxs-lookup"><span data-stu-id="8ba69-122">Exceptions</span></span>  
 <span data-ttu-id="8ba69-123">このコントロール パターンに関連付けられた例外はありません。</span><span class="sxs-lookup"><span data-stu-id="8ba69-123">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ba69-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ba69-124">See Also</span></span>  
 [<span data-ttu-id="8ba69-125">UI オートメーション コントロール パターンの概要</span><span class="sxs-lookup"><span data-stu-id="8ba69-125">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="8ba69-126">UI オートメーション プロバイダーでコントロール パターンをサポートします。</span><span class="sxs-lookup"><span data-stu-id="8ba69-126">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="8ba69-127">クライアントの UI オートメーション コントロール パターン</span><span class="sxs-lookup"><span data-stu-id="8ba69-127">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="8ba69-128">UI オートメーション Table コントロール パターンを実装します。</span><span class="sxs-lookup"><span data-stu-id="8ba69-128">Implementing the UI Automation Table Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-table-control-pattern.md)  
 [<span data-ttu-id="8ba69-129">UI オートメーション GridItem コントロール パターンの実装</span><span class="sxs-lookup"><span data-stu-id="8ba69-129">Implementing the UI Automation GridItem Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)  
 [<span data-ttu-id="8ba69-130">UI オートメーション ツリーの概要</span><span class="sxs-lookup"><span data-stu-id="8ba69-130">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="8ba69-131">UI オートメーションにおけるキャッシュを使用します。</span><span class="sxs-lookup"><span data-stu-id="8ba69-131">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
