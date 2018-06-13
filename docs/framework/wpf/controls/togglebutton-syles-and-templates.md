---
title: ToggleButton のスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], ToggleButton
- ToggleButton [WPF], styles and templates
- ControlTemplate [WPF], ToggleButton
- styles [WPF], ToggleButton
- templates [WPF], ToggleButton
- parts [WPF], ToggleButton
ms.assetid: 54f23f30-4bcb-4f09-8ce4-376a13a255a1
ms.openlocfilehash: b2f3593fbfd2d1fabe2034570813538013623b8b
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457119"
---
# <a name="togglebutton-syles-and-templates"></a><span data-ttu-id="00c55-102">ToggleButton のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="00c55-102">ToggleButton Syles and Templates</span></span>
<span data-ttu-id="00c55-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.Primitives.ToggleButton>コントロール。</span><span class="sxs-lookup"><span data-stu-id="00c55-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span> <span data-ttu-id="00c55-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="00c55-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="00c55-105">詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00c55-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="togglebutton-parts"></a><span data-ttu-id="00c55-106">トグル ボタンのパーツ</span><span class="sxs-lookup"><span data-stu-id="00c55-106">ToggleButton Parts</span></span>  
 <span data-ttu-id="00c55-107"><xref:System.Windows.Controls.Primitives.ToggleButton>コントロールには、その名前付きの部分はありません。</span><span class="sxs-lookup"><span data-stu-id="00c55-107">The <xref:System.Windows.Controls.Primitives.ToggleButton> control does not have any named parts.</span></span>  
  
## <a name="togglebutton-states"></a><span data-ttu-id="00c55-108">トグル ボタンの状態</span><span class="sxs-lookup"><span data-stu-id="00c55-108">ToggleButton States</span></span>  
 <span data-ttu-id="00c55-109">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.Primitives.ToggleButton>コントロール。</span><span class="sxs-lookup"><span data-stu-id="00c55-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>  
  
|<span data-ttu-id="00c55-110">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="00c55-110">VisualState Name</span></span>|<span data-ttu-id="00c55-111">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="00c55-111">VisualStateGroup Name</span></span>|<span data-ttu-id="00c55-112">説明</span><span class="sxs-lookup"><span data-stu-id="00c55-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="00c55-113">標準</span><span class="sxs-lookup"><span data-stu-id="00c55-113">Normal</span></span>|<span data-ttu-id="00c55-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="00c55-114">CommonStates</span></span>|<span data-ttu-id="00c55-115">既定の状態です。</span><span class="sxs-lookup"><span data-stu-id="00c55-115">The default state.</span></span>|  
|<span data-ttu-id="00c55-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="00c55-116">MouseOver</span></span>|<span data-ttu-id="00c55-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="00c55-117">CommonStates</span></span>|<span data-ttu-id="00c55-118">マウス ポインターがコントロール上に配置されています。</span><span class="sxs-lookup"><span data-stu-id="00c55-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="00c55-119">押されている</span><span class="sxs-lookup"><span data-stu-id="00c55-119">Pressed</span></span>|<span data-ttu-id="00c55-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="00c55-120">CommonStates</span></span>|<span data-ttu-id="00c55-121">コントロールが押されています。</span><span class="sxs-lookup"><span data-stu-id="00c55-121">The control is pressed.</span></span>|  
|<span data-ttu-id="00c55-122">無効</span><span class="sxs-lookup"><span data-stu-id="00c55-122">Disabled</span></span>|<span data-ttu-id="00c55-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="00c55-123">CommonStates</span></span>|<span data-ttu-id="00c55-124">コントロールが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="00c55-124">The control is disabled.</span></span>|  
|<span data-ttu-id="00c55-125">フォーカスされている</span><span class="sxs-lookup"><span data-stu-id="00c55-125">Focused</span></span>|<span data-ttu-id="00c55-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="00c55-126">FocusStates</span></span>|<span data-ttu-id="00c55-127">コントロールにフォーカスがあります。</span><span class="sxs-lookup"><span data-stu-id="00c55-127">The control has focus.</span></span>|  
|<span data-ttu-id="00c55-128">フォーカスされていない</span><span class="sxs-lookup"><span data-stu-id="00c55-128">Unfocused</span></span>|<span data-ttu-id="00c55-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="00c55-129">FocusStates</span></span>|<span data-ttu-id="00c55-130">コントロールにフォーカスがありません。</span><span class="sxs-lookup"><span data-stu-id="00c55-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="00c55-131">チェック済み</span><span class="sxs-lookup"><span data-stu-id="00c55-131">Checked</span></span>|<span data-ttu-id="00c55-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="00c55-132">CheckStates</span></span>|<span data-ttu-id="00c55-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> は `true` です。</span><span class="sxs-lookup"><span data-stu-id="00c55-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|  
|<span data-ttu-id="00c55-134">オンになっていません。</span><span class="sxs-lookup"><span data-stu-id="00c55-134">Unchecked</span></span>|<span data-ttu-id="00c55-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="00c55-135">CheckStates</span></span>|<span data-ttu-id="00c55-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> は `false` です。</span><span class="sxs-lookup"><span data-stu-id="00c55-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|  
|<span data-ttu-id="00c55-137">不確定です</span><span class="sxs-lookup"><span data-stu-id="00c55-137">Indeterminate</span></span>|<span data-ttu-id="00c55-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="00c55-138">CheckStates</span></span>|<span data-ttu-id="00c55-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> `true`、および<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>は`null`します。</span><span class="sxs-lookup"><span data-stu-id="00c55-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|  
|<span data-ttu-id="00c55-140">有効</span><span class="sxs-lookup"><span data-stu-id="00c55-140">Valid</span></span>|<span data-ttu-id="00c55-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="00c55-141">ValidationStates</span></span>|<span data-ttu-id="00c55-142">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="00c55-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="00c55-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="00c55-143">InvalidFocused</span></span>|<span data-ttu-id="00c55-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="00c55-144">ValidationStates</span></span>|<span data-ttu-id="00c55-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="00c55-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="00c55-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="00c55-146">InvalidUnfocused</span></span>|<span data-ttu-id="00c55-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="00c55-147">ValidationStates</span></span>|<span data-ttu-id="00c55-148"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="00c55-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="00c55-149">コントロール テンプレートで不確定な表示状態が存在しない場合、未チェックの表示状態は、既定の状態として使用されます。</span><span class="sxs-lookup"><span data-stu-id="00c55-149">If the Indeterminate visual state does not exist in your control template, then the Unchecked visual state will be used as default visual state.</span></span>  
  
## <a name="togglebutton-controltemplate-example"></a><span data-ttu-id="00c55-150">トグル ボタン ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="00c55-150">ToggleButton ControlTemplate Example</span></span>  
 <span data-ttu-id="00c55-151">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Primitives.ToggleButton>コントロール。</span><span class="sxs-lookup"><span data-stu-id="00c55-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToggleButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]  
  
 <span data-ttu-id="00c55-152">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="00c55-152">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="00c55-153">完全なサンプルについては、[Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00c55-153">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00c55-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="00c55-154">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="00c55-155">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="00c55-155">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="00c55-156">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="00c55-156">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="00c55-157">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="00c55-157">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="00c55-158">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="00c55-158">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
