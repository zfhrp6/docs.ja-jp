---
title: "ToggleButton のスタイルとテンプレート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], ToggleButton
- ToggleButton [WPF], styles and templates
- ControlTemplate [WPF], ToggleButton
- styles [WPF], ToggleButton
- templates [WPF], ToggleButton
- parts [WPF], ToggleButton
ms.assetid: 54f23f30-4bcb-4f09-8ce4-376a13a255a1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5c143717b691e79771fbaa55724d9d9748259e3f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="togglebutton-syles-and-templates"></a><span data-ttu-id="dd2ae-102">ToggleButton のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="dd2ae-102">ToggleButton Syles and Templates</span></span>
<span data-ttu-id="dd2ae-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.Primitives.ToggleButton>コントロール。</span><span class="sxs-lookup"><span data-stu-id="dd2ae-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span> <span data-ttu-id="dd2ae-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="dd2ae-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="dd2ae-105">詳細については、「[Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd2ae-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="togglebutton-parts"></a><span data-ttu-id="dd2ae-106">トグル ボタンのパーツ</span><span class="sxs-lookup"><span data-stu-id="dd2ae-106">ToggleButton Parts</span></span>  
 <span data-ttu-id="dd2ae-107"><xref:System.Windows.Controls.Primitives.ToggleButton>コントロールには、その名前付きの部分はありません。</span><span class="sxs-lookup"><span data-stu-id="dd2ae-107">The <xref:System.Windows.Controls.Primitives.ToggleButton> control does not have any named parts.</span></span>  
  
## <a name="togglebutton-states"></a><span data-ttu-id="dd2ae-108">トグル ボタンの状態</span><span class="sxs-lookup"><span data-stu-id="dd2ae-108">ToggleButton States</span></span>  
 <span data-ttu-id="dd2ae-109">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.Primitives.ToggleButton>コントロール。</span><span class="sxs-lookup"><span data-stu-id="dd2ae-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>  
  
|<span data-ttu-id="dd2ae-110">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="dd2ae-110">VisualState Name</span></span>|<span data-ttu-id="dd2ae-111">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="dd2ae-111">VisualStateGroup Name</span></span>|<span data-ttu-id="dd2ae-112">説明</span><span class="sxs-lookup"><span data-stu-id="dd2ae-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="dd2ae-113">標準</span><span class="sxs-lookup"><span data-stu-id="dd2ae-113">Normal</span></span>|<span data-ttu-id="dd2ae-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="dd2ae-114">CommonStates</span></span>|<span data-ttu-id="dd2ae-115">既定の状態です。</span><span class="sxs-lookup"><span data-stu-id="dd2ae-115">The default state.</span></span>|  
|<span data-ttu-id="dd2ae-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="dd2ae-116">MouseOver</span></span>|<span data-ttu-id="dd2ae-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="dd2ae-117">CommonStates</span></span>|<span data-ttu-id="dd2ae-118">マウス ポインターがコントロール上に配置されています。</span><span class="sxs-lookup"><span data-stu-id="dd2ae-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="dd2ae-119">押されている</span><span class="sxs-lookup"><span data-stu-id="dd2ae-119">Pressed</span></span>|<span data-ttu-id="dd2ae-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="dd2ae-120">CommonStates</span></span>|<span data-ttu-id="dd2ae-121">コントロールが押されています。</span><span class="sxs-lookup"><span data-stu-id="dd2ae-121">The control is pressed.</span></span>|  
|<span data-ttu-id="dd2ae-122">無効</span><span class="sxs-lookup"><span data-stu-id="dd2ae-122">Disabled</span></span>|<span data-ttu-id="dd2ae-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="dd2ae-123">CommonStates</span></span>|<span data-ttu-id="dd2ae-124">コントロールが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="dd2ae-124">The control is disabled.</span></span>|  
|<span data-ttu-id="dd2ae-125">フォーカスされている</span><span class="sxs-lookup"><span data-stu-id="dd2ae-125">Focused</span></span>|<span data-ttu-id="dd2ae-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="dd2ae-126">FocusStates</span></span>|<span data-ttu-id="dd2ae-127">コントロールにフォーカスがあります。</span><span class="sxs-lookup"><span data-stu-id="dd2ae-127">The control has focus.</span></span>|  
|<span data-ttu-id="dd2ae-128">フォーカスされていない</span><span class="sxs-lookup"><span data-stu-id="dd2ae-128">Unfocused</span></span>|<span data-ttu-id="dd2ae-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="dd2ae-129">FocusStates</span></span>|<span data-ttu-id="dd2ae-130">コントロールにフォーカスがありません。</span><span class="sxs-lookup"><span data-stu-id="dd2ae-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="dd2ae-131">チェック済み</span><span class="sxs-lookup"><span data-stu-id="dd2ae-131">Checked</span></span>|<span data-ttu-id="dd2ae-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="dd2ae-132">CheckStates</span></span>|<span data-ttu-id="dd2ae-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> は `true` です。</span><span class="sxs-lookup"><span data-stu-id="dd2ae-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|  
|<span data-ttu-id="dd2ae-134">オンになっていません。</span><span class="sxs-lookup"><span data-stu-id="dd2ae-134">Unchecked</span></span>|<span data-ttu-id="dd2ae-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="dd2ae-135">CheckStates</span></span>|<span data-ttu-id="dd2ae-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> は `false` です。</span><span class="sxs-lookup"><span data-stu-id="dd2ae-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|  
|<span data-ttu-id="dd2ae-137">不確定です</span><span class="sxs-lookup"><span data-stu-id="dd2ae-137">Indeterminate</span></span>|<span data-ttu-id="dd2ae-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="dd2ae-138">CheckStates</span></span>|<span data-ttu-id="dd2ae-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A>is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span><span class="sxs-lookup"><span data-stu-id="dd2ae-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|  
|<span data-ttu-id="dd2ae-140">有効</span><span class="sxs-lookup"><span data-stu-id="dd2ae-140">Valid</span></span>|<span data-ttu-id="dd2ae-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="dd2ae-141">ValidationStates</span></span>|<span data-ttu-id="dd2ae-142">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="dd2ae-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="dd2ae-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="dd2ae-143">InvalidFocused</span></span>|<span data-ttu-id="dd2ae-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="dd2ae-144">ValidationStates</span></span>|<span data-ttu-id="dd2ae-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="dd2ae-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="dd2ae-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="dd2ae-146">InvalidUnfocused</span></span>|<span data-ttu-id="dd2ae-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="dd2ae-147">ValidationStates</span></span>|<span data-ttu-id="dd2ae-148"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="dd2ae-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="dd2ae-149">コントロール テンプレートで不確定な表示状態が存在しない場合、未チェックの表示状態は、既定の状態として使用されます。</span><span class="sxs-lookup"><span data-stu-id="dd2ae-149">If the Indeterminate visual state does not exist in your control template, then the Unchecked visual state will be used as default visual state.</span></span>  
  
## <a name="togglebutton-controltemplate-example"></a><span data-ttu-id="dd2ae-150">トグル ボタン ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="dd2ae-150">ToggleButton ControlTemplate Example</span></span>  
 <span data-ttu-id="dd2ae-151">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Primitives.ToggleButton>コントロール。</span><span class="sxs-lookup"><span data-stu-id="dd2ae-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToggleButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]  
  
 <span data-ttu-id="dd2ae-152">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="dd2ae-152">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="dd2ae-153">完全なサンプルについては、[Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd2ae-153">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd2ae-154">参照</span><span class="sxs-lookup"><span data-stu-id="dd2ae-154">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="dd2ae-155">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="dd2ae-155">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="dd2ae-156">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="dd2ae-156">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="dd2ae-157">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="dd2ae-157">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="dd2ae-158">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="dd2ae-158">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
