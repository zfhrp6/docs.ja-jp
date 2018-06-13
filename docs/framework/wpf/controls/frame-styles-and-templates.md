---
title: フレームのスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], Frame
- templates [WPF], Frame
- ControlTemplate [WPF], Frame
- Frame [WPF], styles and templates
- states [WPF], Frame
- styles [WPF], Frame
ms.assetid: a01c32e2-c951-46a0-a82f-2614ca241f0b
ms.openlocfilehash: 78bbeb915e17bcd59480b921efa1b6a51fa67762
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457892"
---
# <a name="frame-styles-and-templates"></a><span data-ttu-id="9299b-102">フレームのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="9299b-102">Frame Styles and Templates</span></span>
<span data-ttu-id="9299b-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.Frame>コントロール。</span><span class="sxs-lookup"><span data-stu-id="9299b-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Frame> control.</span></span> <span data-ttu-id="9299b-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="9299b-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="9299b-105">詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9299b-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="frame-parts"></a><span data-ttu-id="9299b-106">フレームのパーツ</span><span class="sxs-lookup"><span data-stu-id="9299b-106">Frame Parts</span></span>  
 <span data-ttu-id="9299b-107">次の表に、名前付きのパーツの<xref:System.Windows.Controls.Frame>コントロール。</span><span class="sxs-lookup"><span data-stu-id="9299b-107">The following table lists the named parts for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="9299b-108">パーツ</span><span class="sxs-lookup"><span data-stu-id="9299b-108">Part</span></span>|<span data-ttu-id="9299b-109">型</span><span class="sxs-lookup"><span data-stu-id="9299b-109">Type</span></span>|<span data-ttu-id="9299b-110">説明</span><span class="sxs-lookup"><span data-stu-id="9299b-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="9299b-111">PART_FrameCP</span><span class="sxs-lookup"><span data-stu-id="9299b-111">PART_FrameCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="9299b-112">コンテンツ領域です。</span><span class="sxs-lookup"><span data-stu-id="9299b-112">The content area.</span></span>|  
  
## <a name="frame-states"></a><span data-ttu-id="9299b-113">フレームの状態</span><span class="sxs-lookup"><span data-stu-id="9299b-113">Frame States</span></span>  
 <span data-ttu-id="9299b-114">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.Frame>コントロール。</span><span class="sxs-lookup"><span data-stu-id="9299b-114">The following table lists the visual states for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="9299b-115">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="9299b-115">VisualState Name</span></span>|<span data-ttu-id="9299b-116">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="9299b-116">VisualStateGroup Name</span></span>|<span data-ttu-id="9299b-117">説明</span><span class="sxs-lookup"><span data-stu-id="9299b-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="9299b-118">有効</span><span class="sxs-lookup"><span data-stu-id="9299b-118">Valid</span></span>|<span data-ttu-id="9299b-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9299b-119">ValidationStates</span></span>|<span data-ttu-id="9299b-120">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="9299b-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="9299b-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="9299b-121">InvalidFocused</span></span>|<span data-ttu-id="9299b-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9299b-122">ValidationStates</span></span>|<span data-ttu-id="9299b-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="9299b-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="9299b-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="9299b-124">InvalidUnfocused</span></span>|<span data-ttu-id="9299b-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9299b-125">ValidationStates</span></span>|<span data-ttu-id="9299b-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="9299b-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="frame-controltemplate-example"></a><span data-ttu-id="9299b-127">フレーム ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="9299b-127">Frame ControlTemplate Example</span></span>  
 <span data-ttu-id="9299b-128">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Frame>コントロール。</span><span class="sxs-lookup"><span data-stu-id="9299b-128">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Frame](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/frame.xaml#frame)]  
  
 <span data-ttu-id="9299b-129">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="9299b-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="9299b-130">完全なサンプルについては、[Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9299b-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9299b-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="9299b-131">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="9299b-132">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="9299b-132">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="9299b-133">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="9299b-133">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="9299b-134">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="9299b-134">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="9299b-135">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="9299b-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
