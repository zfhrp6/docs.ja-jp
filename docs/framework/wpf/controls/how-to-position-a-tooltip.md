---
title: "方法 : ToolTip を配置する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62e86f2adfbe8f8aac000d653e955555c7def750
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-position-a-tooltip"></a><span data-ttu-id="de666-102">方法 : ToolTip を配置する</span><span class="sxs-lookup"><span data-stu-id="de666-102">How to: Position a ToolTip</span></span>
<span data-ttu-id="de666-103">この例では、画面のツールヒントの位置を指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="de666-103">This example shows how to specify the position of a tooltip on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de666-104">例</span><span class="sxs-lookup"><span data-stu-id="de666-104">Example</span></span>  
 <span data-ttu-id="de666-105">ツールヒントを配置するには、両方で定義されている 5 つのプロパティのセットを使用して、<xref:System.Windows.Controls.ToolTip>と<xref:System.Windows.Controls.ToolTipService>クラスです。</span><span class="sxs-lookup"><span data-stu-id="de666-105">You can position a tooltip by using a set of five properties that are defined in both the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> classes.</span></span> <span data-ttu-id="de666-106">次の表は、5 つのプロパティのこれら 2 つのセットを表示し、クラスに基づいて、リファレンス ドキュメントへのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="de666-106">The following table shows these two sets of five properties and provides links to their reference documentation according to class.</span></span>  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a><span data-ttu-id="de666-107">対応するツールヒント プロパティ クラス</span><span class="sxs-lookup"><span data-stu-id="de666-107">Corresponding tooltip properties according to class</span></span>  
  
|<span data-ttu-id="de666-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType>クラスのプロパティ</span><span class="sxs-lookup"><span data-stu-id="de666-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> class properties</span></span>|<span data-ttu-id="de666-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType>クラスのプロパティ</span><span class="sxs-lookup"><span data-stu-id="de666-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> class properties</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="de666-110">使用して、ツールヒントの内容を定義するかどうか、<xref:System.Windows.Controls.ToolTip>オブジェクトのいずれかのクラス プロパティを使用することができます。 ただし、、<xref:System.Windows.Controls.ToolTipService>プロパティも優先されます。</span><span class="sxs-lookup"><span data-stu-id="de666-110">If you define the contents of a tooltip by using a <xref:System.Windows.Controls.ToolTip> object, you can use the properties of either class; however, the <xref:System.Windows.Controls.ToolTipService> properties take precedence.</span></span> <span data-ttu-id="de666-111">使用して、<xref:System.Windows.Controls.ToolTipService>プロパティとして定義されていないツールヒントを<xref:System.Windows.Controls.ToolTip>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="de666-111">Use the <xref:System.Windows.Controls.ToolTipService> properties for tooltips that are not defined as <xref:System.Windows.Controls.ToolTip> objects.</span></span>  
  
 <span data-ttu-id="de666-112">次の図は、これらのプロパティを使用して、ツールヒントを配置する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="de666-112">The following illustrations show how to position a tooltip by using these properties.</span></span> <span data-ttu-id="de666-113">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]これらの図の例で定義されているプロパティを設定する方法を示して、<xref:System.Windows.Controls.ToolTip>クラスの対応するプロパティ、<xref:System.Windows.Controls.ToolTipService>クラスが同じレイアウト規則に従います。</span><span class="sxs-lookup"><span data-stu-id="de666-113">Although, the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples in these illustrations show how to set the properties that are defined by the <xref:System.Windows.Controls.ToolTip> class, the corresponding properties of the <xref:System.Windows.Controls.ToolTipService> class follow the same layout rules.</span></span> <span data-ttu-id="de666-114">配置のプロパティの値の詳細については、次を参照してください。[ポップアップ配置動作](../../../../docs/framework/wpf/controls/popup-placement-behavior.md)です。</span><span class="sxs-lookup"><span data-stu-id="de666-114">For more information about the possible values for the Placement property, see [Popup Placement Behavior](../../../../docs/framework/wpf/controls/popup-placement-behavior.md).</span></span>  
  
 <span data-ttu-id="de666-115">![ツールヒント配置](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")</span><span class="sxs-lookup"><span data-stu-id="de666-115">![ToolTip placement](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")</span></span>  
<span data-ttu-id="de666-116">配置のプロパティを使用して、ツールヒントの配置</span><span class="sxs-lookup"><span data-stu-id="de666-116">ToolTip placement by using the Placement property</span></span>  
  
 <span data-ttu-id="de666-117">![配置四角形を使用して、ツールヒントの配置](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")</span><span class="sxs-lookup"><span data-stu-id="de666-117">![Placing a ToolTip by using a placement rectangle](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")</span></span>  
<span data-ttu-id="de666-118">配置および PlacementRectangle の各プロパティを使用して、ツールヒントの配置</span><span class="sxs-lookup"><span data-stu-id="de666-118">ToolTip placement by using the Placement and PlacementRectangle properties</span></span>  
  
 <span data-ttu-id="de666-119">![ツールヒント配置のダイアグラム](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")</span><span class="sxs-lookup"><span data-stu-id="de666-119">![ToolTip placement diagram](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")</span></span>  
<span data-ttu-id="de666-120">オフセットの配置、および PlacementRectangle、プロパティを使用して、ツールヒントの配置</span><span class="sxs-lookup"><span data-stu-id="de666-120">ToolTip placement by using the Placement, PlacementRectangle, and Offset properties</span></span>  
  
 <span data-ttu-id="de666-121">次の例を使用する方法を示しています、<xref:System.Windows.Controls.ToolTip>プロパティが表示されるツールヒントの位置を指定する、<xref:System.Windows.Controls.ToolTip>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="de666-121">The following example shows how to use the <xref:System.Windows.Controls.ToolTip> properties to specify the position of a tooltip whose content is a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 <span data-ttu-id="de666-122">次の例を使用する方法を示しています、<xref:System.Windows.Controls.ToolTipService>プロパティの内容がツールヒントの位置を指定する、<xref:System.Windows.Controls.ToolTip>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="de666-122">The following example shows how to use the <xref:System.Windows.Controls.ToolTipService> properties to specify the position of a tooltip whose content is not a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a><span data-ttu-id="de666-123">参照</span><span class="sxs-lookup"><span data-stu-id="de666-123">See Also</span></span>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [<span data-ttu-id="de666-124">方法トピック</span><span class="sxs-lookup"><span data-stu-id="de666-124">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)  
 [<span data-ttu-id="de666-125">ToolTip の概要</span><span class="sxs-lookup"><span data-stu-id="de666-125">ToolTip Overview</span></span>](../../../../docs/framework/wpf/controls/tooltip-overview.md)  
 [<span data-ttu-id="de666-126">ContextMenuService と全体を使用します。</span><span class="sxs-lookup"><span data-stu-id="de666-126">Use the ContextMenuService and ToolTipService</span></span>](http://msdn.microsoft.com/en-us/809b0e9c-d612-4cda-b8af-1a698c68f4d1)
