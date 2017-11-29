---
title: "クライアントの UI オートメーション コントロール パターン"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
caps.latest.revision: "24"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 1d556b3da13b70a0a5e69eb72905e04a01dffa9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ui-automation-control-patterns-for-clients"></a><span data-ttu-id="5b50c-102">クライアントの UI オートメーション コントロール パターン</span><span class="sxs-lookup"><span data-stu-id="5b50c-102">UI Automation Control Patterns for Clients</span></span>
> [!NOTE]
>  <span data-ttu-id="5b50c-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="5b50c-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="5b50c-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](http://go.microsoft.com/fwlink/?LinkID=156746)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5b50c-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="5b50c-105">この概要では、UI オートメーション クライアントのコントロール パターンについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5b50c-105">This overview introduces control patterns for UI Automation clients.</span></span> <span data-ttu-id="5b50c-106">また、UI オートメーション クライアントがコントロール パターンを使用して、 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]の情報にアクセスするしくみについても説明します。</span><span class="sxs-lookup"><span data-stu-id="5b50c-106">It includes information on how a UI Automation client can use control patterns to access information about the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="5b50c-107">コントロール パターンは、コントロール型や外観に関係なく、コントロールの機能を分類したり公開したりするための手段です。</span><span class="sxs-lookup"><span data-stu-id="5b50c-107">Control patterns provide a way to categorize and expose a control's functionality independent of the control type or the appearance of the control.</span></span> <span data-ttu-id="5b50c-108">UI オートメーション クライアントは、 <xref:System.Windows.Automation.AutomationElement> を調べてどのコントロール パターンがサポートされているかを特定し、そのコントロールの動作を確実に実行することができます。</span><span class="sxs-lookup"><span data-stu-id="5b50c-108">UI Automation clients can examine an <xref:System.Windows.Automation.AutomationElement> to determine which control patterns are supported and be assured of the behavior of the control.</span></span>  
  
 <span data-ttu-id="5b50c-109">コントロール パターンの完全なリストについては、「 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5b50c-109">For a complete list of control patterns, see [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).</span></span>  
  
<a name="uiautomation_getting_control_patterns"></a>   
## <a name="getting-control-patterns"></a><span data-ttu-id="5b50c-110">コントロール パターンの取得</span><span class="sxs-lookup"><span data-stu-id="5b50c-110">Getting Control Patterns</span></span>  
 <span data-ttu-id="5b50c-111">クライアントは、<xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> または <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType> を呼び出して、<xref:System.Windows.Automation.AutomationElement> からコントロール パターンを取得します。</span><span class="sxs-lookup"><span data-stu-id="5b50c-111">Clients retrieve a control pattern from an <xref:System.Windows.Automation.AutomationElement> by calling either <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> or <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="5b50c-112">クライアントは、 <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> メソッドまたは個別の `IsPatternAvailable` プロパティ ( <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>など) を使用して、パターンまたはパターンのグループが <xref:System.Windows.Automation.AutomationElement>でサポートされているかどうかを特定できます。</span><span class="sxs-lookup"><span data-stu-id="5b50c-112">Clients can use the <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> method or an individual `IsPatternAvailable` property (for example, <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>) to determine if a pattern or group of patterns is supported on the <xref:System.Windows.Automation.AutomationElement>.</span></span> <span data-ttu-id="5b50c-113">ただし、サポートされているプロパティを確認してコントロール パターンを取得するよりも、コントロール パターンを取得して `null` 参照に対するテストを試行する方が、プロセス間呼び出しが少なくなるため効率的です。</span><span class="sxs-lookup"><span data-stu-id="5b50c-113">However, it is more efficient to attempt to get the control pattern and test for a `null` reference than to check the supported properties and retrieve the control pattern since it results in fewer cross-process calls.</span></span>  
  
 <span data-ttu-id="5b50c-114"><xref:System.Windows.Automation.TextPattern> から <xref:System.Windows.Automation.AutomationElement>コントロール パターンを取得する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="5b50c-114">The following example demonstrates how to get a <xref:System.Windows.Automation.TextPattern> control pattern from an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>   
## <a name="retrieving-properties-on-control-patterns"></a><span data-ttu-id="5b50c-115">コントロール パターンのプロパティの取得</span><span class="sxs-lookup"><span data-stu-id="5b50c-115">Retrieving Properties on Control Patterns</span></span>  
 <span data-ttu-id="5b50c-116">クライアントは、<xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> または <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> を呼び出し、返されたオブジェクトを適切な型にキャストすることで、コントロール パターンのプロパティ値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="5b50c-116">Clients can retrieve the property values on control patterns by calling either <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> or <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> and casting the object returned to an appropriate type.</span></span> <span data-ttu-id="5b50c-117">詳細については[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]プロパティを参照してください[クライアントの UI オートメーション プロパティ](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)です。</span><span class="sxs-lookup"><span data-stu-id="5b50c-117">For more information on [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] properties, see [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).</span></span>  
  
 <span data-ttu-id="5b50c-118">`GetPropertyValue` メソッドに加え、 [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] アクセサーを介してパターンの [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティにアクセスすることで、プロパティ値を取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="5b50c-118">In addition to the `GetPropertyValue` methods, property values can be retrieved through the [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] accessors to access the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] properties on a pattern.</span></span>  
  
<a name="uiautomation_with_variable_patterns"></a>   
## <a name="controls-with-variable-patterns"></a><span data-ttu-id="5b50c-119">変数パターンを持つコントロール</span><span class="sxs-lookup"><span data-stu-id="5b50c-119">Controls with Variable Patterns</span></span>  
 <span data-ttu-id="5b50c-120">一部のコントロール型は、状態やコントロールの使用方法に応じた複数のパターンをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="5b50c-120">Some control types support different patterns depending on their state or the manner in which the control is being used.</span></span> <span data-ttu-id="5b50c-121">変数パターンを持つコントロールの例としては、リスト ビュー (サムネイル、タイル、アイコン、リスト、詳細)、 [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] グラフ (円、線、横棒、式を使用するセル値)、 [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)]のドキュメント領域 (標準、Web レイアウト、アウトライン、印刷レイアウト、印刷プレビュー)、 [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] スキンなどがあります。</span><span class="sxs-lookup"><span data-stu-id="5b50c-121">Examples of controls that can have variable patterns are list views (thumbnails, tiles, icons, list, details), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] Charts (Pie, Line, Bar, Cell Value with a formula), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)]'s document area (Normal, Web Layout, Outline, Print Layout, Print Preview), and [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] skins.</span></span>  
  
 <span data-ttu-id="5b50c-122">カスタム コントロール型を実装するコントロールは、機能を表すために必要なコントロール パターンの任意のセットを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="5b50c-122">Controls implementing custom control types can have any set of control patterns that are needed to represent their functionality.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b50c-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="5b50c-123">See Also</span></span>  
 [<span data-ttu-id="5b50c-124">UI オートメーション コントロール パターン</span><span class="sxs-lookup"><span data-stu-id="5b50c-124">UI Automation Control Patterns</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns.md)  
 [<span data-ttu-id="5b50c-125">UI オートメーション テキスト パターン</span><span class="sxs-lookup"><span data-stu-id="5b50c-125">UI Automation Text Pattern</span></span>](../../../docs/framework/ui-automation/ui-automation-text-pattern.md)  
 [<span data-ttu-id="5b50c-126">UI オートメーションを使用したコントロールを呼び出し</span><span class="sxs-lookup"><span data-stu-id="5b50c-126">Invoke a Control Using UI Automation</span></span>](../../../docs/framework/ui-automation/invoke-a-control-using-ui-automation.md)  
 [<span data-ttu-id="5b50c-127">UI オートメーションを使用する チェック ボックスのトグル状態の取得します。</span><span class="sxs-lookup"><span data-stu-id="5b50c-127">Get the Toggle State of a Check Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)  
 [<span data-ttu-id="5b50c-128">UI オートメーション クライアントのコントロール パターン マッピング</span><span class="sxs-lookup"><span data-stu-id="5b50c-128">Control Pattern Mapping for UI Automation Clients</span></span>](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
 [<span data-ttu-id="5b50c-129">TextPattern の挿入テキスト サンプル</span><span class="sxs-lookup"><span data-stu-id="5b50c-129">TextPattern Insert Text Sample</span></span>](http://msdn.microsoft.com/en-us/67353f93-7ee2-42f2-ab76-5c078cf6ca16)  
 [<span data-ttu-id="5b50c-130">TextPattern の検索と選択のサンプル</span><span class="sxs-lookup"><span data-stu-id="5b50c-130">TextPattern Search and Selection Sample</span></span>](http://msdn.microsoft.com/en-us/0a3bca57-8b72-489d-a57c-da85b7a22c7f)  
 [<span data-ttu-id="5b50c-131">InvokePattern および ExpandCollapsePattern メニュー項目のサンプル</span><span class="sxs-lookup"><span data-stu-id="5b50c-131">InvokePattern and ExpandCollapsePattern Menu Item Sample</span></span>](http://msdn.microsoft.com/en-us/b7fa141c-e2d1-4da2-a27f-81a7d1172210)
