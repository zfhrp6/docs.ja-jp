---
title: "ToolTip の概要"
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
- ToolTip control [WPF], about ToolTip control
- controls [WPF], ToolTip
ms.assetid: f06c1603-e9cb-4809-8a62-234607fc52f7
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c945d23def3bbf6284e7e0db95d391066256df6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="tooltip-overview"></a><span data-ttu-id="0cb39-102">ToolTip の概要</span><span class="sxs-lookup"><span data-stu-id="0cb39-102">ToolTip Overview</span></span>
<span data-ttu-id="0cb39-103">ツールヒントは、ユーザーなどを超えると、要素の上にマウス ポインターを置いたときに表示される小さいポップアップ ウィンドウ、<xref:System.Windows.Controls.Button>です。</span><span class="sxs-lookup"><span data-stu-id="0cb39-103">A tooltip is a small pop-up window that appears when a user pauses the mouse pointer over an element, such as over a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="0cb39-104">このトピックでは、ツールヒントを紹介し、ツールヒントの内容を作成およびカスタマイズする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0cb39-104">This topic introduces the tooltip and discusses how to create and customize tooltip content.</span></span>  
  
 
  
<a name="what_is_a_tooltip"></a>   
## <a name="what-is-a-tooltip"></a><span data-ttu-id="0cb39-105">ツールヒントとは</span><span class="sxs-lookup"><span data-stu-id="0cb39-105">What Is a Tooltip?</span></span>  
 <span data-ttu-id="0cb39-106">ツールヒントを持つ要素の上にマウス ポインターを置くと、一定の時間、ツールヒントの内容 (たとえば、コントロールの機能を説明するテキスト コンテンツ) を含むウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0cb39-106">When a user moves the mouse pointer over an element that has a tooltip, a window that contains tooltip content (for example, text content that describes the function of a control) appears for a specified amount of time.</span></span> <span data-ttu-id="0cb39-107">コントロールからマウス ポインターを移動すると、ツールヒントの内容がフォーカスを受け取ることができなくなるため、ウィンドウが消えます</span><span class="sxs-lookup"><span data-stu-id="0cb39-107">If the user moves the mouse pointer away from the control, the window disappears because the tooltip content cannot receive focus.</span></span>  
  
 <span data-ttu-id="0cb39-108">ツールヒントの内容は、1 行または複数行のテキスト、イメージ、図形などのビジュアル コンテンツを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="0cb39-108">The content of a tooltip can contain one or more lines of text, images, shapes, or other visual content.</span></span> <span data-ttu-id="0cb39-109">次のプロパティの 1 つをツールヒントの内容に設定することによって、コントロールのツールヒントを定義します。</span><span class="sxs-lookup"><span data-stu-id="0cb39-109">You define a tooltip for a control by setting one of the following properties to the tooltip content.</span></span>  
  
-   <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="0cb39-110">使用するどのプロパティから、ツールヒントを定義するコントロールを継承するかどうかに依存、<xref:System.Windows.FrameworkContentElement>または<xref:System.Windows.FrameworkElement>クラスです。</span><span class="sxs-lookup"><span data-stu-id="0cb39-110">Which property you use depends on whether the control that defines the tooltip inherits from the <xref:System.Windows.FrameworkContentElement> or <xref:System.Windows.FrameworkElement> class.</span></span>  
  
<a name="create_tooltip"></a>   
## <a name="creating-a-tooltip"></a><span data-ttu-id="0cb39-111">ツールヒントの作成</span><span class="sxs-lookup"><span data-stu-id="0cb39-111">Creating a ToolTip</span></span>  
 <span data-ttu-id="0cb39-112">次の例を設定して、単純なツールヒントを作成する方法を示しています、<xref:System.Windows.FrameworkElement.ToolTip%2A>プロパティを<xref:System.Windows.Controls.Button>コントロールにテキスト文字列。</span><span class="sxs-lookup"><span data-stu-id="0cb39-112">The following example shows how to create a simple tooltip by setting the <xref:System.Windows.FrameworkElement.ToolTip%2A> property for a <xref:System.Windows.Controls.Button> control to a text string.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 <span data-ttu-id="0cb39-113">としてのツールヒントを定義することも、<xref:System.Windows.Controls.ToolTip>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0cb39-113">You can also define a tooltip as a <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="0cb39-114">次の例で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を指定する、<xref:System.Windows.Controls.ToolTip>オブジェクトのツールヒントとして、<xref:System.Windows.Controls.TextBox>要素。</span><span class="sxs-lookup"><span data-stu-id="0cb39-114">The following example uses [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to specify a <xref:System.Windows.Controls.ToolTip> object as the tooltip of a <xref:System.Windows.Controls.TextBox> element.</span></span> <span data-ttu-id="0cb39-115">例では、指定、<xref:System.Windows.Controls.ToolTip>を設定して、<xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="0cb39-115">Note that the example specifies the <xref:System.Windows.Controls.ToolTip> by setting the <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> property.</span></span>  
  
 [!code-xaml[ToolTipSimple#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 <span data-ttu-id="0cb39-116">次の例では、コードを使用して、生成する、<xref:System.Windows.Controls.ToolTip>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0cb39-116">The following example uses code to generate a <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="0cb39-117">例は、作成、 <xref:System.Windows.Controls.ToolTip> (`tt`) に関連付けますと、<xref:System.Windows.Controls.Button>です。</span><span class="sxs-lookup"><span data-stu-id="0cb39-117">The example creates a <xref:System.Windows.Controls.ToolTip> (`tt`) and associates it with a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-csharp[ToolTipSimple#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 <span data-ttu-id="0cb39-118">として定義されていないツールヒントのコンテンツを作成することも、<xref:System.Windows.Controls.ToolTip>などをレイアウト要素のツールヒントのコンテンツを囲むことによってオブジェクト、<xref:System.Windows.Controls.DockPanel>です。</span><span class="sxs-lookup"><span data-stu-id="0cb39-118">You can also create tooltip content that is not defined as a <xref:System.Windows.Controls.ToolTip> object by enclosing the tooltip content in a layout element, such as a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="0cb39-119">次の例は、設定する方法を示します、<xref:System.Windows.FrameworkElement.ToolTip%2A>のプロパティ、<xref:System.Windows.Controls.TextBox>で囲まれたコンテンツを<xref:System.Windows.Controls.DockPanel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="0cb39-119">The following example shows how to set the <xref:System.Windows.FrameworkElement.ToolTip%2A> property of a <xref:System.Windows.Controls.TextBox> to content that is enclosed in a <xref:System.Windows.Controls.DockPanel> control.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>   
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a><span data-ttu-id="0cb39-120">ToolTip クラスおよび ToolTipService クラスのプロパティの使用</span><span class="sxs-lookup"><span data-stu-id="0cb39-120">Using the Properties of the ToolTip and ToolTipService Classes</span></span>  
 <span data-ttu-id="0cb39-121">ビジュアル プロパティを設定し、スタイルを適用して、ツールヒントの内容をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="0cb39-121">You can customize tooltip content by setting visual properties and applying styles.</span></span> <span data-ttu-id="0cb39-122">ツールヒントとしてコンテンツを定義する場合、<xref:System.Windows.Controls.ToolTip>オブジェクトのビジュアル プロパティを設定することができます、<xref:System.Windows.Controls.ToolTip>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0cb39-122">If you define the tooltip content as a <xref:System.Windows.Controls.ToolTip> object, you can set the visual properties of the <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="0cb39-123">それ以外の場合でと同等の添付プロパティを設定する必要があります、<xref:System.Windows.Controls.ToolTipService>クラスです。</span><span class="sxs-lookup"><span data-stu-id="0cb39-123">Otherwise, you must set equivalent attached properties on the <xref:System.Windows.Controls.ToolTipService> class.</span></span>  
  
 <span data-ttu-id="0cb39-124">使用して、ツールヒントのコンテンツの位置を指定するためにプロパティを設定する方法の例については、<xref:System.Windows.Controls.ToolTip>と<xref:System.Windows.Controls.ToolTipService>プロパティを参照してください[ツールヒントを配置](../../../../docs/framework/wpf/controls/how-to-position-a-tooltip.md)です。</span><span class="sxs-lookup"><span data-stu-id="0cb39-124">For an example of how to set properties in order to specify the position of tooltip content by using the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> properties, see [Position a ToolTip](../../../../docs/framework/wpf/controls/how-to-position-a-tooltip.md).</span></span>  
  
<a name="StylingToolTip"></a>   
## <a name="styling-a-tooltip"></a><span data-ttu-id="0cb39-125">ツールヒントのスタイル設定</span><span class="sxs-lookup"><span data-stu-id="0cb39-125">Styling a ToolTip</span></span>  
 <span data-ttu-id="0cb39-126">スタイルを設定することができます、<xref:System.Windows.Controls.ToolTip>カスタムを定義することによって<xref:System.Windows.Style>です。</span><span class="sxs-lookup"><span data-stu-id="0cb39-126">You can style a <xref:System.Windows.Controls.ToolTip> by defining a custom <xref:System.Windows.Style>.</span></span> <span data-ttu-id="0cb39-127">次の例では定義、<xref:System.Windows.Style>と呼ばれる`Simple`の配置をオフセットする方法を示す、<xref:System.Windows.Controls.ToolTip>を設定して、外観を変更し、 <xref:System.Windows.Controls.Control.Background%2A>、 <xref:System.Windows.Controls.Control.Foreground%2A>、 <xref:System.Windows.Controls.Control.FontSize%2A>、および<xref:System.Windows.Controls.Control.FontWeight%2A>です。</span><span class="sxs-lookup"><span data-stu-id="0cb39-127">The following example defines a <xref:System.Windows.Style> called `Simple` that shows how to offset the placement of the <xref:System.Windows.Controls.ToolTip> and change its appearance by setting the <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, and <xref:System.Windows.Controls.Control.FontWeight%2A>.</span></span>  
  
 [!code-xaml[ToolTipSimple#Style](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>   
## <a name="using-the-time-interval-properties-of-tooltipservice"></a><span data-ttu-id="0cb39-128">ToolTipService の時間間隔プロパティの使用</span><span class="sxs-lookup"><span data-stu-id="0cb39-128">Using the Time Interval Properties of ToolTipService</span></span>  
 <span data-ttu-id="0cb39-129"><xref:System.Windows.Controls.ToolTipService> 、次のプロパティにツールヒントを設定する時刻を表示するクラスが用意されています: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>、 <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>、および<xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>です。</span><span class="sxs-lookup"><span data-stu-id="0cb39-129">The <xref:System.Windows.Controls.ToolTipService> class provides the following properties for you to set tooltip display times: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>, and <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.</span></span>  
  
 <span data-ttu-id="0cb39-130">使用して、<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>と<xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>プロパティで、遅延を指定する通常の簡単な前に、<xref:System.Windows.Controls.ToolTip>が表示されますおよび期間を指定にも、<xref:System.Windows.Controls.ToolTip>表示されたままです。</span><span class="sxs-lookup"><span data-stu-id="0cb39-130">Use the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> and <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> properties to specify a delay, typically brief, before a <xref:System.Windows.Controls.ToolTip> appears and also to specify how long a <xref:System.Windows.Controls.ToolTip> remains visible.</span></span> <span data-ttu-id="0cb39-131">詳細については、「[ How to: Delay the Display of a ToolTip](http://msdn.microsoft.com/library/618e05ef-f2bf-4a53-a0f4-aacb49918bd7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0cb39-131">For more information, see [How to: Delay the Display of a ToolTip](http://msdn.microsoft.com/library/618e05ef-f2bf-4a53-a0f4-aacb49918bd7).</span></span>  
  
 <span data-ttu-id="0cb39-132"><xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>プロパティ間にマウス ポインターをすばやく移動するときに初期遅延なしのさまざまなコントロールのツールヒントが表示されるかどうかがします。</span><span class="sxs-lookup"><span data-stu-id="0cb39-132">The <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> property determines if tooltips for different controls appear without an initial delay when you move the mouse pointer quickly between them.</span></span> <span data-ttu-id="0cb39-133">詳細については、<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>プロパティを参照してください[BetweenShowDelay プロパティを使用して](../../../../docs/framework/wpf/controls/how-to-use-the-betweenshowdelay-property.md)です。</span><span class="sxs-lookup"><span data-stu-id="0cb39-133">For more information about the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> property, see [Use the BetweenShowDelay Property](../../../../docs/framework/wpf/controls/how-to-use-the-betweenshowdelay-property.md).</span></span>  
  
 <span data-ttu-id="0cb39-134">次の例では、ツールヒントのこれらのプロパティを設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0cb39-134">The following example shows how to set these properties for a tooltip.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a><span data-ttu-id="0cb39-135">参照</span><span class="sxs-lookup"><span data-stu-id="0cb39-135">See Also</span></span>  
 <xref:System.Windows.Controls.ToolTipService>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipEventArgs>  
 <xref:System.Windows.Controls.ToolTipEventHandler>  
 [<span data-ttu-id="0cb39-136">データ バインドに関する「方法」トピック</span><span class="sxs-lookup"><span data-stu-id="0cb39-136">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)
