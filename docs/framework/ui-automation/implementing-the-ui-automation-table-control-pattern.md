---
title: UI オートメーション Table コントロール パターンの実装
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 955d9f005a45ab805012dd43cbef27877a9dfdb4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398581"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a><span data-ttu-id="433cb-102">UI オートメーション Table コントロール パターンの実装</span><span class="sxs-lookup"><span data-stu-id="433cb-102">Implementing the UI Automation Table Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="433cb-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="433cb-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="433cb-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="433cb-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="433cb-105">このトピックでは、プロパティ、メソッド、イベントに関する情報など、<xref:System.Windows.Automation.Provider.ITableProvider> の実装のためのガイドラインと規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="433cb-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="433cb-106">その他のリファレンスへのリンクは、概要の最後に記載します。</span><span class="sxs-lookup"><span data-stu-id="433cb-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="433cb-107"><xref:System.Windows.Automation.TablePattern>コントロール パターンは、子要素のコレクションのコンテナーとして機能するコントロールをサポートするために使用します。</span><span class="sxs-lookup"><span data-stu-id="433cb-107">The <xref:System.Windows.Automation.TablePattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="433cb-108">この要素の子を実装する必要があります<xref:System.Windows.Automation.Provider.ITableItemProvider>行と列で走査可能な 2 次元の論理座標システムで編成するとします。</span><span class="sxs-lookup"><span data-stu-id="433cb-108">The children of this element must implement <xref:System.Windows.Automation.Provider.ITableItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="433cb-109">このコントロール パターンはに似て<xref:System.Windows.Automation.Provider.IGridProvider>を実装するコントロールを除いて、<xref:System.Windows.Automation.Provider.ITableProvider>も、列または行ヘッダーのリレーションシップを各子要素を公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="433cb-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridProvider>, with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableProvider> must also expose a column and/or row header relationship for each child element.</span></span> <span data-ttu-id="433cb-110">このコントロール パターンを実装するコントロールの例については、「 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="433cb-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="433cb-111">実装のガイドラインと規則</span><span class="sxs-lookup"><span data-stu-id="433cb-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="433cb-112">Table コントロール パターンを実装する場合は、次のガイドラインと規則に留意してください。</span><span class="sxs-lookup"><span data-stu-id="433cb-112">When implementing the Table control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="433cb-113">個々 のセルのコンテンツへのアクセスは 2 次元論理座標系または配列の必要な同時実装によって提供されるを通じて<xref:System.Windows.Automation.Provider.IGridProvider>です。</span><span class="sxs-lookup"><span data-stu-id="433cb-113">Access to the content of individual cells is through a two-dimensional logical coordinate system or array provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span>  
  
-   <span data-ttu-id="433cb-114">列ヘッダーまたは行ヘッダーは、テーブル オブジェクト内に含めることも、テーブル オブジェクトに関連付けられた別のヘッダー オブジェクトにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="433cb-114">A column or row header can be contained within a table object or be a separate header object that is associated with a table object.</span></span>  
  
-   <span data-ttu-id="433cb-115">列ヘッダーと行ヘッダーには、プライマリ ヘッダーだけでなく、任意の補助ヘッダーも含めることができます。</span><span class="sxs-lookup"><span data-stu-id="433cb-115">Column and row headers may include both a primary header as well as any supporting headers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="433cb-116">この概念がで明らかになります、[!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)]スプレッドシート ユーザーが [ファースト ネーム] 列が定義されています。</span><span class="sxs-lookup"><span data-stu-id="433cb-116">This concept becomes evident in a [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] spreadsheet where a user has defined a "First name" column.</span></span> <span data-ttu-id="433cb-117">これで、この列のヘッダーは、ユーザーが定義した [ファースト ネーム] ヘッダーとアプリケーションによって割り当てられたその列の英数字指定の 2 つになります。</span><span class="sxs-lookup"><span data-stu-id="433cb-117">This column now has two headers—the "First name" header defined by the user and the alphanumeric designation for that column assigned by the application.</span></span>  
  
-   <span data-ttu-id="433cb-118">参照してください[UI オートメーション Grid コントロール パターンを実装する](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)の関連するグリッド機能します。</span><span class="sxs-lookup"><span data-stu-id="433cb-118">See [Implementing the UI Automation Grid Control Pattern](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md) for related grid functionality.</span></span>  
  
 <span data-ttu-id="433cb-119">![複雑なヘッダー項目を含むテーブルです。] (../../../docs/framework/ui-automation/media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span><span class="sxs-lookup"><span data-stu-id="433cb-119">![Table with complex header items.](../../../docs/framework/ui-automation/media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span></span>  
<span data-ttu-id="433cb-120">列ヘッダーが複雑なテーブルの例</span><span class="sxs-lookup"><span data-stu-id="433cb-120">Example of a Table with Complex Column Headers</span></span>  
  
 <span data-ttu-id="433cb-121">![あいまいな RowOrColumnMajor プロパティを含むテーブル。] (../../../docs/framework/ui-automation/media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span><span class="sxs-lookup"><span data-stu-id="433cb-121">![Table with ambiguous RowOrColumnMajor property.](../../../docs/framework/ui-automation/media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span></span>  
<span data-ttu-id="433cb-122">RowOrColumnMajor プロパティがあいまいなテーブルの例</span><span class="sxs-lookup"><span data-stu-id="433cb-122">Example of a Table with Ambiguous RowOrColumnMajor Property</span></span>  
  
<a name="Required_Members_for_ITableProvider"></a>   
## <a name="required-members-for-itableprovider"></a><span data-ttu-id="433cb-123">ITableProvider の必須メンバー</span><span class="sxs-lookup"><span data-stu-id="433cb-123">Required Members for ITableProvider</span></span>  
 <span data-ttu-id="433cb-124">ITableProvider インターフェイスには、次のプロパティとメソッドが必要です。</span><span class="sxs-lookup"><span data-stu-id="433cb-124">The following properties and methods are required for the ITableProvider interface.</span></span>  
  
|<span data-ttu-id="433cb-125">必須メンバー</span><span class="sxs-lookup"><span data-stu-id="433cb-125">Required members</span></span>|<span data-ttu-id="433cb-126">メンバーの型</span><span class="sxs-lookup"><span data-stu-id="433cb-126">Member type</span></span>|<span data-ttu-id="433cb-127">メモ</span><span class="sxs-lookup"><span data-stu-id="433cb-127">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|<span data-ttu-id="433cb-128">プロパティ</span><span class="sxs-lookup"><span data-stu-id="433cb-128">Property</span></span>|<span data-ttu-id="433cb-129">なし</span><span class="sxs-lookup"><span data-stu-id="433cb-129">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|<span data-ttu-id="433cb-130">メソッド</span><span class="sxs-lookup"><span data-stu-id="433cb-130">Method</span></span>|<span data-ttu-id="433cb-131">なし</span><span class="sxs-lookup"><span data-stu-id="433cb-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|<span data-ttu-id="433cb-132">メソッド</span><span class="sxs-lookup"><span data-stu-id="433cb-132">Method</span></span>|<span data-ttu-id="433cb-133">なし</span><span class="sxs-lookup"><span data-stu-id="433cb-133">None</span></span>|  
  
 <span data-ttu-id="433cb-134">このコントロール パターンには、関連するイベントがありません。</span><span class="sxs-lookup"><span data-stu-id="433cb-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="433cb-135">例外</span><span class="sxs-lookup"><span data-stu-id="433cb-135">Exceptions</span></span>  
 <span data-ttu-id="433cb-136">このコントロール パターンに関連付けられた例外はありません。</span><span class="sxs-lookup"><span data-stu-id="433cb-136">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="433cb-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="433cb-137">See Also</span></span>  
 [<span data-ttu-id="433cb-138">UI Automation コントロール パターンの概要</span><span class="sxs-lookup"><span data-stu-id="433cb-138">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="433cb-139">UI オートメーション プロバイダーでのコントロール パターンのサポート</span><span class="sxs-lookup"><span data-stu-id="433cb-139">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="433cb-140">クライアントの UI オートメーション コントロール パターン</span><span class="sxs-lookup"><span data-stu-id="433cb-140">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="433cb-141">UI オートメーション TableItem コントロール パターンの実装</span><span class="sxs-lookup"><span data-stu-id="433cb-141">Implementing the UI Automation TableItem Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-tableitem-control-pattern.md)  
 [<span data-ttu-id="433cb-142">UI オートメーション Grid コントロール パターンの実装</span><span class="sxs-lookup"><span data-stu-id="433cb-142">Implementing the UI Automation Grid Control Pattern</span></span>](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)  
 [<span data-ttu-id="433cb-143">UI Automation ツリーの概要</span><span class="sxs-lookup"><span data-stu-id="433cb-143">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="433cb-144">UI オートメーションにおけるキャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="433cb-144">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
