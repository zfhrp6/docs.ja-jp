---
title: スライダーのスタイルとテンプレート
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parts [WPF], Slider
- states [WPF], Slider
- Slider [WPF], styles and templates
- styles [WPF], Slider
- templates [WPF], Slider
- ControlTemplate [WPF], Slider
ms.assetid: d89aa97b-075a-4752-9c41-9679df65c491
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9ffbc5d2aa6e401dffb06f1695a5299a99ef90a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="slider-styles-and-templates"></a><span data-ttu-id="301d3-102">スライダーのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="301d3-102">Slider Styles and Templates</span></span>
<span data-ttu-id="301d3-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.Slider>コントロール。</span><span class="sxs-lookup"><span data-stu-id="301d3-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Slider> control.</span></span> <span data-ttu-id="301d3-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="301d3-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="301d3-105">詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="301d3-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="slider-parts"></a><span data-ttu-id="301d3-106">スライダーのパーツ</span><span class="sxs-lookup"><span data-stu-id="301d3-106">Slider Parts</span></span>  
 <span data-ttu-id="301d3-107">次の表に、名前付きのパーツの<xref:System.Windows.Controls.Slider>コントロール。</span><span class="sxs-lookup"><span data-stu-id="301d3-107">The following table lists the named parts for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="301d3-108">パーツ</span><span class="sxs-lookup"><span data-stu-id="301d3-108">Part</span></span>|<span data-ttu-id="301d3-109">型</span><span class="sxs-lookup"><span data-stu-id="301d3-109">Type</span></span>|<span data-ttu-id="301d3-110">説明</span><span class="sxs-lookup"><span data-stu-id="301d3-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="301d3-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="301d3-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="301d3-112">要素の位置を示すためのコンテナー、<xref:System.Windows.Controls.Slider>です。</span><span class="sxs-lookup"><span data-stu-id="301d3-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Slider>.</span></span>|  
|<span data-ttu-id="301d3-113">PART_SelectionRange</span><span class="sxs-lookup"><span data-stu-id="301d3-113">PART_SelectionRange</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="301d3-114">に沿って選択範囲を表示する要素、<xref:System.Windows.Controls.Slider>です。</span><span class="sxs-lookup"><span data-stu-id="301d3-114">The element that displays a selection range along the <xref:System.Windows.Controls.Slider>.</span></span>  <span data-ttu-id="301d3-115">選択範囲が表示されている場合にのみ、<xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A>プロパティは`true`します。</span><span class="sxs-lookup"><span data-stu-id="301d3-115">The selection range is visible only if the <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> property is `true`.</span></span>|  
  
## <a name="slider-states"></a><span data-ttu-id="301d3-116">スライダーの状態</span><span class="sxs-lookup"><span data-stu-id="301d3-116">Slider States</span></span>  
 <span data-ttu-id="301d3-117">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.Slider>コントロール。</span><span class="sxs-lookup"><span data-stu-id="301d3-117">The following table lists the visual states for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="301d3-118">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="301d3-118">VisualState Name</span></span>|<span data-ttu-id="301d3-119">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="301d3-119">VisualStateGroup Name</span></span>|<span data-ttu-id="301d3-120">説明</span><span class="sxs-lookup"><span data-stu-id="301d3-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="301d3-121">標準</span><span class="sxs-lookup"><span data-stu-id="301d3-121">Normal</span></span>|<span data-ttu-id="301d3-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="301d3-122">CommonStates</span></span>|<span data-ttu-id="301d3-123">既定の状態です。</span><span class="sxs-lookup"><span data-stu-id="301d3-123">The default state.</span></span>|  
|<span data-ttu-id="301d3-124">MouseOver</span><span class="sxs-lookup"><span data-stu-id="301d3-124">MouseOver</span></span>|<span data-ttu-id="301d3-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="301d3-125">CommonStates</span></span>|<span data-ttu-id="301d3-126">マウス ポインターがコントロール上に配置されます。</span><span class="sxs-lookup"><span data-stu-id="301d3-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="301d3-127">無効</span><span class="sxs-lookup"><span data-stu-id="301d3-127">Disabled</span></span>|<span data-ttu-id="301d3-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="301d3-128">CommonStates</span></span>|<span data-ttu-id="301d3-129">コントロールが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="301d3-129">The control is disabled.</span></span>|  
|<span data-ttu-id="301d3-130">フォーカスされている</span><span class="sxs-lookup"><span data-stu-id="301d3-130">Focused</span></span>|<span data-ttu-id="301d3-131">FocusStates</span><span class="sxs-lookup"><span data-stu-id="301d3-131">FocusStates</span></span>|<span data-ttu-id="301d3-132">コントロールにフォーカスがあります。</span><span class="sxs-lookup"><span data-stu-id="301d3-132">The control has focus.</span></span>|  
|<span data-ttu-id="301d3-133">フォーカスされていない</span><span class="sxs-lookup"><span data-stu-id="301d3-133">Unfocused</span></span>|<span data-ttu-id="301d3-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="301d3-134">FocusStates</span></span>|<span data-ttu-id="301d3-135">コントロールにフォーカスがありません。</span><span class="sxs-lookup"><span data-stu-id="301d3-135">The control does not have focus.</span></span>|  
|<span data-ttu-id="301d3-136">有効</span><span class="sxs-lookup"><span data-stu-id="301d3-136">Valid</span></span>|<span data-ttu-id="301d3-137">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="301d3-137">ValidationStates</span></span>|<span data-ttu-id="301d3-138">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="301d3-138">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="301d3-139">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="301d3-139">InvalidFocused</span></span>|<span data-ttu-id="301d3-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="301d3-140">ValidationStates</span></span>|<span data-ttu-id="301d3-141"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="301d3-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="301d3-142">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="301d3-142">InvalidUnfocused</span></span>|<span data-ttu-id="301d3-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="301d3-143">ValidationStates</span></span>|<span data-ttu-id="301d3-144"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="301d3-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="slider-controltemplate-example"></a><span data-ttu-id="301d3-145">スライダー ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="301d3-145">Slider ControlTemplate Example</span></span>  
 <span data-ttu-id="301d3-146">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Slider>コントロール。</span><span class="sxs-lookup"><span data-stu-id="301d3-146">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Slider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#slider)]  
  
 <span data-ttu-id="301d3-147">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="301d3-147">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="301d3-148">完全なサンプルについては、[Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="301d3-148">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="301d3-149">参照</span><span class="sxs-lookup"><span data-stu-id="301d3-149">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="301d3-150">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="301d3-150">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="301d3-151">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="301d3-151">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="301d3-152">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="301d3-152">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="301d3-153">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="301d3-153">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
