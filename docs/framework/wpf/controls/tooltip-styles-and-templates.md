---
title: ToolTip のスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ToolTip
- styles [WPF], ToolTip
- states [WPF], ToolTip
- ToolTip [WPF], styles and templates
- ControlTemplate [WPF], ToolTip
- templates [WPF], ToolTip
ms.assetid: 405fe385-4de9-49ee-a448-d8f4d1f740dd
ms.openlocfilehash: 53b21f610ba957370fac70b79e6a827d624b6473
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457295"
---
# <a name="tooltip-styles-and-templates"></a><span data-ttu-id="d851d-102">ToolTip のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="d851d-102">ToolTip Styles and Templates</span></span>
<span data-ttu-id="d851d-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.ToolTip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="d851d-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolTip> control.</span></span> <span data-ttu-id="d851d-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="d851d-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d851d-105">詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d851d-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="tooltip-parts"></a><span data-ttu-id="d851d-106">ツールヒントのパーツ</span><span class="sxs-lookup"><span data-stu-id="d851d-106">ToolTip Parts</span></span>  
 <span data-ttu-id="d851d-107"><xref:System.Windows.Controls.ToolTip>コントロールには、その名前付きの部分はありません。</span><span class="sxs-lookup"><span data-stu-id="d851d-107">The <xref:System.Windows.Controls.ToolTip> control does not have any named parts.</span></span>  
  
## <a name="tooltip-states"></a><span data-ttu-id="d851d-108">ツール ヒントの状態</span><span class="sxs-lookup"><span data-stu-id="d851d-108">ToolTip States</span></span>  
 <span data-ttu-id="d851d-109">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.ToolTip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="d851d-109">The following table lists the visual states for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
|<span data-ttu-id="d851d-110">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="d851d-110">VisualState Name</span></span>|<span data-ttu-id="d851d-111">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="d851d-111">VisualStateGroup Name</span></span>|<span data-ttu-id="d851d-112">説明</span><span class="sxs-lookup"><span data-stu-id="d851d-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d851d-113">Closed</span><span class="sxs-lookup"><span data-stu-id="d851d-113">Closed</span></span>|<span data-ttu-id="d851d-114">OpenStates</span><span class="sxs-lookup"><span data-stu-id="d851d-114">OpenStates</span></span>|<span data-ttu-id="d851d-115">既定の状態です。</span><span class="sxs-lookup"><span data-stu-id="d851d-115">The default state.</span></span>|  
|<span data-ttu-id="d851d-116">開く</span><span class="sxs-lookup"><span data-stu-id="d851d-116">Open</span></span>|<span data-ttu-id="d851d-117">OpenStates</span><span class="sxs-lookup"><span data-stu-id="d851d-117">OpenStates</span></span>|<span data-ttu-id="d851d-118"><xref:System.Windows.Controls.ToolTip>が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d851d-118">The <xref:System.Windows.Controls.ToolTip> is visible.</span></span>|  
|<span data-ttu-id="d851d-119">有効</span><span class="sxs-lookup"><span data-stu-id="d851d-119">Valid</span></span>|<span data-ttu-id="d851d-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d851d-120">ValidationStates</span></span>|<span data-ttu-id="d851d-121">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="d851d-121">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d851d-122">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d851d-122">InvalidFocused</span></span>|<span data-ttu-id="d851d-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d851d-123">ValidationStates</span></span>|<span data-ttu-id="d851d-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="d851d-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d851d-125">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d851d-125">InvalidUnfocused</span></span>|<span data-ttu-id="d851d-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d851d-126">ValidationStates</span></span>|<span data-ttu-id="d851d-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="d851d-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tooltip-controltemplate-example"></a><span data-ttu-id="d851d-128">ツールヒント ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="d851d-128">ToolTip ControlTemplate Example</span></span>  
 <span data-ttu-id="d851d-129">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.ToolTip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="d851d-129">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tooltip.xaml#tooltip)]  
  
 <span data-ttu-id="d851d-130">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="d851d-130">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="d851d-131">完全なサンプルについては、[Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d851d-131">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d851d-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="d851d-132">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="d851d-133">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="d851d-133">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="d851d-134">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="d851d-134">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="d851d-135">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="d851d-135">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="d851d-136">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="d851d-136">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
