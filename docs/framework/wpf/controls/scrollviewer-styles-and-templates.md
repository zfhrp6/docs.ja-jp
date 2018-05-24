---
title: ScrollViewer のスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ScrollViewer
- states [WPF], ScrollViewer
- styles [WPF], ScrollViewer
- templates [WPF], ScrollViewer
- ControlTemplate [WPF], ScrollViewer
- ScrollViewer [WPF], styles and templates
ms.assetid: dffdd822-ae69-4946-abaf-710860cd65b2
ms.openlocfilehash: 5ad3738972ae9b33764d3b710077f6d4a0526a13
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="scrollviewer-styles-and-templates"></a><span data-ttu-id="7b513-102">ScrollViewer のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="7b513-102">ScrollViewer Styles and Templates</span></span>
<span data-ttu-id="7b513-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.ScrollViewer>コントロール。</span><span class="sxs-lookup"><span data-stu-id="7b513-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span> <span data-ttu-id="7b513-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="7b513-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="7b513-105">詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b513-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollviewer-parts"></a><span data-ttu-id="7b513-106">ScrollViewer 部分</span><span class="sxs-lookup"><span data-stu-id="7b513-106">ScrollViewer Parts</span></span>  
 <span data-ttu-id="7b513-107">次の表に、名前付きのパーツの<xref:System.Windows.Controls.ScrollViewer>コントロール。</span><span class="sxs-lookup"><span data-stu-id="7b513-107">The following table lists the named parts for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="7b513-108">パーツ</span><span class="sxs-lookup"><span data-stu-id="7b513-108">Part</span></span>|<span data-ttu-id="7b513-109">型</span><span class="sxs-lookup"><span data-stu-id="7b513-109">Type</span></span>|<span data-ttu-id="7b513-110">説明</span><span class="sxs-lookup"><span data-stu-id="7b513-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="7b513-111">PART_ScrollContentPresenter</span><span class="sxs-lookup"><span data-stu-id="7b513-111">PART_ScrollContentPresenter</span></span>|<xref:System.Windows.Controls.ScrollContentPresenter>|<span data-ttu-id="7b513-112">内のコンテンツのプレース ホルダー、<xref:System.Windows.Controls.ScrollViewer>です。</span><span class="sxs-lookup"><span data-stu-id="7b513-112">The placeholder for content in the <xref:System.Windows.Controls.ScrollViewer>.</span></span>|  
|<span data-ttu-id="7b513-113">PART_HorizontalScrollBar</span><span class="sxs-lookup"><span data-stu-id="7b513-113">PART_HorizontalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="7b513-114"><xref:System.Windows.Controls.Primitives.ScrollBar>コンテンツを水平方向にスクロールするために使用します。</span><span class="sxs-lookup"><span data-stu-id="7b513-114">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content horizontally.</span></span>|  
|<span data-ttu-id="7b513-115">PART_VerticalScrollBar</span><span class="sxs-lookup"><span data-stu-id="7b513-115">PART_VerticalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="7b513-116"><xref:System.Windows.Controls.Primitives.ScrollBar>コンテンツを垂直方向にスクロールするために使用します。</span><span class="sxs-lookup"><span data-stu-id="7b513-116">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content vertically.</span></span>|  
  
## <a name="scrollviewer-states"></a><span data-ttu-id="7b513-117">ScrollViewer 状態</span><span class="sxs-lookup"><span data-stu-id="7b513-117">ScrollViewer States</span></span>  
 <span data-ttu-id="7b513-118">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.ScrollViewer>コントロール。</span><span class="sxs-lookup"><span data-stu-id="7b513-118">The following table lists the visual states for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="7b513-119">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="7b513-119">VisualState Name</span></span>|<span data-ttu-id="7b513-120">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="7b513-120">VisualStateGroup Name</span></span>|<span data-ttu-id="7b513-121">説明</span><span class="sxs-lookup"><span data-stu-id="7b513-121">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="7b513-122">有効</span><span class="sxs-lookup"><span data-stu-id="7b513-122">Valid</span></span>|<span data-ttu-id="7b513-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7b513-123">ValidationStates</span></span>|<span data-ttu-id="7b513-124">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="7b513-124">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="7b513-125">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="7b513-125">InvalidFocused</span></span>|<span data-ttu-id="7b513-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7b513-126">ValidationStates</span></span>|<span data-ttu-id="7b513-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="7b513-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="7b513-128">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="7b513-128">InvalidUnfocused</span></span>|<span data-ttu-id="7b513-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7b513-129">ValidationStates</span></span>|<span data-ttu-id="7b513-130"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="7b513-130">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollviewer-controltemplate-example"></a><span data-ttu-id="7b513-131">ScrollViewer ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="7b513-131">ScrollViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="7b513-132">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.ScrollViewer>コントロール。</span><span class="sxs-lookup"><span data-stu-id="7b513-132">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollviewer.xaml#scrollviewer)]  
  
 <span data-ttu-id="7b513-133">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="7b513-133">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="7b513-134">完全なサンプルについては、[Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b513-134">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b513-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b513-135">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="7b513-136">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="7b513-136">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="7b513-137">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="7b513-137">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="7b513-138">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="7b513-138">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="7b513-139">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="7b513-139">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
