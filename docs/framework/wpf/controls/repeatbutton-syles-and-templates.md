---
title: RepeatButton のスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatButton [WPF], styles and templates
- styles [WPF], RepeatButton
- templates [WPF], RepeatButton
- parts [WPF], RepeatButton
- ControlTemplate [WPF], RepeatButton
- states [WPF], RepeatButton
ms.assetid: fd340743-f44f-4990-9077-085301469670
ms.openlocfilehash: d5edea14c1ea4184fda67e9b64887f192420b413
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="repeatbutton-syles-and-templates"></a><span data-ttu-id="84ff2-102">RepeatButton のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="84ff2-102">RepeatButton Syles and Templates</span></span>
<span data-ttu-id="84ff2-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.Primitives.RepeatButton>コントロール。</span><span class="sxs-lookup"><span data-stu-id="84ff2-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span> <span data-ttu-id="84ff2-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="84ff2-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="84ff2-105">詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84ff2-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="repeatbutton-parts"></a><span data-ttu-id="84ff2-106">RepeatButton 部分</span><span class="sxs-lookup"><span data-stu-id="84ff2-106">RepeatButton Parts</span></span>  
 <span data-ttu-id="84ff2-107"><xref:System.Windows.Controls.Primitives.RepeatButton>コントロールには、その名前付きの部分はありません。</span><span class="sxs-lookup"><span data-stu-id="84ff2-107">The <xref:System.Windows.Controls.Primitives.RepeatButton> control does not have any named parts.</span></span>  
  
## <a name="repeatbutton-states"></a><span data-ttu-id="84ff2-108">RepeatButton 状態</span><span class="sxs-lookup"><span data-stu-id="84ff2-108">RepeatButton States</span></span>  
 <span data-ttu-id="84ff2-109">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.Primitives.RepeatButton>コントロール。</span><span class="sxs-lookup"><span data-stu-id="84ff2-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span>  
  
|<span data-ttu-id="84ff2-110">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="84ff2-110">VisualState Name</span></span>|<span data-ttu-id="84ff2-111">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="84ff2-111">VisualStateGroup Name</span></span>|<span data-ttu-id="84ff2-112">説明</span><span class="sxs-lookup"><span data-stu-id="84ff2-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="84ff2-113">標準</span><span class="sxs-lookup"><span data-stu-id="84ff2-113">Normal</span></span>|<span data-ttu-id="84ff2-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="84ff2-114">CommonStates</span></span>|<span data-ttu-id="84ff2-115">既定の状態です。</span><span class="sxs-lookup"><span data-stu-id="84ff2-115">The default state.</span></span>|  
|<span data-ttu-id="84ff2-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="84ff2-116">MouseOver</span></span>|<span data-ttu-id="84ff2-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="84ff2-117">CommonStates</span></span>|<span data-ttu-id="84ff2-118">マウス ポインターがコントロール上に配置されています。</span><span class="sxs-lookup"><span data-stu-id="84ff2-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="84ff2-119">押されている</span><span class="sxs-lookup"><span data-stu-id="84ff2-119">Pressed</span></span>|<span data-ttu-id="84ff2-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="84ff2-120">CommonStates</span></span>|<span data-ttu-id="84ff2-121">コントロールが押されています。</span><span class="sxs-lookup"><span data-stu-id="84ff2-121">The control is pressed.</span></span>|  
|<span data-ttu-id="84ff2-122">無効</span><span class="sxs-lookup"><span data-stu-id="84ff2-122">Disabled</span></span>|<span data-ttu-id="84ff2-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="84ff2-123">CommonStates</span></span>|<span data-ttu-id="84ff2-124">コントロールが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="84ff2-124">The control is disabled.</span></span>|  
|<span data-ttu-id="84ff2-125">フォーカスされている</span><span class="sxs-lookup"><span data-stu-id="84ff2-125">Focused</span></span>|<span data-ttu-id="84ff2-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="84ff2-126">FocusStates</span></span>|<span data-ttu-id="84ff2-127">コントロールにフォーカスがあります。</span><span class="sxs-lookup"><span data-stu-id="84ff2-127">The control has focus.</span></span>|  
|<span data-ttu-id="84ff2-128">フォーカスされていない</span><span class="sxs-lookup"><span data-stu-id="84ff2-128">Unfocused</span></span>|<span data-ttu-id="84ff2-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="84ff2-129">FocusStates</span></span>|<span data-ttu-id="84ff2-130">コントロールにフォーカスがありません。</span><span class="sxs-lookup"><span data-stu-id="84ff2-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="84ff2-131">有効</span><span class="sxs-lookup"><span data-stu-id="84ff2-131">Valid</span></span>|<span data-ttu-id="84ff2-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="84ff2-132">ValidationStates</span></span>|<span data-ttu-id="84ff2-133">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="84ff2-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="84ff2-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="84ff2-134">InvalidFocused</span></span>|<span data-ttu-id="84ff2-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="84ff2-135">ValidationStates</span></span>|<span data-ttu-id="84ff2-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="84ff2-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="84ff2-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="84ff2-137">InvalidUnfocused</span></span>|<span data-ttu-id="84ff2-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="84ff2-138">ValidationStates</span></span>|<span data-ttu-id="84ff2-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="84ff2-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="repeatbutton-controltemplate-example"></a><span data-ttu-id="84ff2-140">RepeatButton ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="84ff2-140">RepeatButton ControlTemplate Example</span></span>  
 <span data-ttu-id="84ff2-141">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Primitives.RepeatButton>コントロール。</span><span class="sxs-lookup"><span data-stu-id="84ff2-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#RepeatButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#repeatbutton)]  
  
 <span data-ttu-id="84ff2-142">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="84ff2-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="84ff2-143">完全なサンプルについては、[Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84ff2-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84ff2-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="84ff2-144">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="84ff2-145">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="84ff2-145">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="84ff2-146">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="84ff2-146">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="84ff2-147">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="84ff2-147">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="84ff2-148">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="84ff2-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
