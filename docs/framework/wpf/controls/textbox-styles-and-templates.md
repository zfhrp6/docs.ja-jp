---
title: TextBox のスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TextBox
- parts [WPF], TextBox
- states [WPF], TextBox
- styles [WPF], TextBox
- templates [WPF], TextBox
- TextBox [WPF], styles and templates
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
ms.openlocfilehash: b18aa6798c2d7c66eaca6cb98b55e9050868f258
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="ffd26-102">TextBox のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="ffd26-102">TextBox Styles and Templates</span></span>
<span data-ttu-id="ffd26-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.TextBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="ffd26-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="ffd26-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="ffd26-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="ffd26-105">詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffd26-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="ffd26-106">テキスト ボックスの部分</span><span class="sxs-lookup"><span data-stu-id="ffd26-106">TextBox Parts</span></span>  
 <span data-ttu-id="ffd26-107">次の表に、名前付きのパーツの<xref:System.Windows.Controls.TextBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="ffd26-107">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="ffd26-108">パーツ</span><span class="sxs-lookup"><span data-stu-id="ffd26-108">Part</span></span>|<span data-ttu-id="ffd26-109">型</span><span class="sxs-lookup"><span data-stu-id="ffd26-109">Type</span></span>|<span data-ttu-id="ffd26-110">説明</span><span class="sxs-lookup"><span data-stu-id="ffd26-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ffd26-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="ffd26-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="ffd26-112">視覚的要素を含むことができます、<xref:System.Windows.FrameworkElement>です。</span><span class="sxs-lookup"><span data-stu-id="ffd26-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="ffd26-113">テキスト、<xref:System.Windows.Controls.TextBox>はこの要素に表示されます。</span><span class="sxs-lookup"><span data-stu-id="ffd26-113">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="ffd26-114">テキスト ボックスの状態</span><span class="sxs-lookup"><span data-stu-id="ffd26-114">TextBox States</span></span>  
 <span data-ttu-id="ffd26-115">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.TextBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="ffd26-115">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="ffd26-116">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="ffd26-116">VisualState Name</span></span>|<span data-ttu-id="ffd26-117">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="ffd26-117">VisualStateGroup Name</span></span>|<span data-ttu-id="ffd26-118">説明</span><span class="sxs-lookup"><span data-stu-id="ffd26-118">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="ffd26-119">標準</span><span class="sxs-lookup"><span data-stu-id="ffd26-119">Normal</span></span>|<span data-ttu-id="ffd26-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ffd26-120">CommonStates</span></span>|<span data-ttu-id="ffd26-121">既定の状態です。</span><span class="sxs-lookup"><span data-stu-id="ffd26-121">The default state.</span></span>|  
|<span data-ttu-id="ffd26-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="ffd26-122">MouseOver</span></span>|<span data-ttu-id="ffd26-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ffd26-123">CommonStates</span></span>|<span data-ttu-id="ffd26-124">マウス ポインターがコントロール上に配置されます。</span><span class="sxs-lookup"><span data-stu-id="ffd26-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="ffd26-125">無効</span><span class="sxs-lookup"><span data-stu-id="ffd26-125">Disabled</span></span>|<span data-ttu-id="ffd26-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ffd26-126">CommonStates</span></span>|<span data-ttu-id="ffd26-127">コントロールが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="ffd26-127">The control is disabled.</span></span>|  
|<span data-ttu-id="ffd26-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="ffd26-128">ReadOnly</span></span>|<span data-ttu-id="ffd26-129">CommonStates</span><span class="sxs-lookup"><span data-stu-id="ffd26-129">CommonStates</span></span>|<span data-ttu-id="ffd26-130">ユーザーが内のテキストを変更できない、<xref:System.Windows.Controls.TextBox>です。</span><span class="sxs-lookup"><span data-stu-id="ffd26-130">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="ffd26-131">フォーカスされている</span><span class="sxs-lookup"><span data-stu-id="ffd26-131">Focused</span></span>|<span data-ttu-id="ffd26-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="ffd26-132">FocusStates</span></span>|<span data-ttu-id="ffd26-133">コントロールにフォーカスがあります。</span><span class="sxs-lookup"><span data-stu-id="ffd26-133">The control has focus.</span></span>|  
|<span data-ttu-id="ffd26-134">フォーカスされていない</span><span class="sxs-lookup"><span data-stu-id="ffd26-134">Unfocused</span></span>|<span data-ttu-id="ffd26-135">FocusStates</span><span class="sxs-lookup"><span data-stu-id="ffd26-135">FocusStates</span></span>|<span data-ttu-id="ffd26-136">コントロールにフォーカスがありません。</span><span class="sxs-lookup"><span data-stu-id="ffd26-136">The control does not have focus.</span></span>|  
|<span data-ttu-id="ffd26-137">有効</span><span class="sxs-lookup"><span data-stu-id="ffd26-137">Valid</span></span>|<span data-ttu-id="ffd26-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ffd26-138">ValidationStates</span></span>|<span data-ttu-id="ffd26-139">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="ffd26-139">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ffd26-140">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="ffd26-140">InvalidFocused</span></span>|<span data-ttu-id="ffd26-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ffd26-141">ValidationStates</span></span>|<span data-ttu-id="ffd26-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="ffd26-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="ffd26-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="ffd26-143">InvalidUnfocused</span></span>|<span data-ttu-id="ffd26-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ffd26-144">ValidationStates</span></span>|<span data-ttu-id="ffd26-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="ffd26-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="ffd26-146">TextBox ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="ffd26-146">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="ffd26-147">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.TextBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="ffd26-147">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="ffd26-148">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="ffd26-148">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="ffd26-149">完全なサンプルについては、[Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ffd26-149">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffd26-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="ffd26-150">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="ffd26-151">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="ffd26-151">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="ffd26-152">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="ffd26-152">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="ffd26-153">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="ffd26-153">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="ffd26-154">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="ffd26-154">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
