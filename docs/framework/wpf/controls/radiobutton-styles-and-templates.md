---
title: "RadioButton のスタイルとテンプレート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], RadioButton
- RadioButton [WPF], styles and templates
- ControlTemplate [WPF], RadioButton
- states [WPF], RadioButton
- templates [WPF], RadioButton
- parts [WPF], RadioButton
ms.assetid: 9acf93f7-dd2f-4010-8ce0-1edd81c52ae2
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 384a587fe01fb69ff5d377f2aa34d03ff110880d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="radiobutton-styles-and-templates"></a><span data-ttu-id="c4880-102">RadioButton のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="c4880-102">RadioButton Styles and Templates</span></span>
<span data-ttu-id="c4880-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.RadioButton>コントロール。</span><span class="sxs-lookup"><span data-stu-id="c4880-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.RadioButton> control.</span></span> <span data-ttu-id="c4880-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="c4880-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="c4880-105">詳細については、「[Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4880-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="radiobutton-parts"></a><span data-ttu-id="c4880-106">RadioButton のパーツ</span><span class="sxs-lookup"><span data-stu-id="c4880-106">RadioButton Parts</span></span>  
 <span data-ttu-id="c4880-107"><xref:System.Windows.Controls.RadioButton>コントロールには、その名前付きの部分はありません。</span><span class="sxs-lookup"><span data-stu-id="c4880-107">The <xref:System.Windows.Controls.RadioButton> control does not have any named parts.</span></span>  
  
## <a name="radiobutton-states"></a><span data-ttu-id="c4880-108">状態の RadioButton</span><span class="sxs-lookup"><span data-stu-id="c4880-108">RadioButton States</span></span>  
 <span data-ttu-id="c4880-109">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.RadioButton>コントロール。</span><span class="sxs-lookup"><span data-stu-id="c4880-109">The following table lists the visual states for the <xref:System.Windows.Controls.RadioButton> control.</span></span>  
  
|<span data-ttu-id="c4880-110">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="c4880-110">VisualState Name</span></span>|<span data-ttu-id="c4880-111">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="c4880-111">VisualStateGroup Name</span></span>|<span data-ttu-id="c4880-112">説明</span><span class="sxs-lookup"><span data-stu-id="c4880-112">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="c4880-113">標準</span><span class="sxs-lookup"><span data-stu-id="c4880-113">Normal</span></span>|<span data-ttu-id="c4880-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c4880-114">CommonStates</span></span>|<span data-ttu-id="c4880-115">既定の状態です。</span><span class="sxs-lookup"><span data-stu-id="c4880-115">The default state.</span></span>|  
|<span data-ttu-id="c4880-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="c4880-116">MouseOver</span></span>|<span data-ttu-id="c4880-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c4880-117">CommonStates</span></span>|<span data-ttu-id="c4880-118">マウス ポインターがコントロール上に配置されています。</span><span class="sxs-lookup"><span data-stu-id="c4880-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="c4880-119">押されている</span><span class="sxs-lookup"><span data-stu-id="c4880-119">Pressed</span></span>|<span data-ttu-id="c4880-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c4880-120">CommonStates</span></span>|<span data-ttu-id="c4880-121">コントロールが押されています。</span><span class="sxs-lookup"><span data-stu-id="c4880-121">The control is pressed.</span></span>|  
|<span data-ttu-id="c4880-122">無効</span><span class="sxs-lookup"><span data-stu-id="c4880-122">Disabled</span></span>|<span data-ttu-id="c4880-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c4880-123">CommonStates</span></span>|<span data-ttu-id="c4880-124">コントロールが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="c4880-124">The control is disabled.</span></span>|  
|<span data-ttu-id="c4880-125">フォーカスされている</span><span class="sxs-lookup"><span data-stu-id="c4880-125">Focused</span></span>|<span data-ttu-id="c4880-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="c4880-126">FocusStates</span></span>|<span data-ttu-id="c4880-127">コントロールにフォーカスがあります。</span><span class="sxs-lookup"><span data-stu-id="c4880-127">The control has focus.</span></span>|  
|<span data-ttu-id="c4880-128">フォーカスされていない</span><span class="sxs-lookup"><span data-stu-id="c4880-128">Unfocused</span></span>|<span data-ttu-id="c4880-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="c4880-129">FocusStates</span></span>|<span data-ttu-id="c4880-130">コントロールにフォーカスがありません。</span><span class="sxs-lookup"><span data-stu-id="c4880-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="c4880-131">チェック済み</span><span class="sxs-lookup"><span data-stu-id="c4880-131">Checked</span></span>|<span data-ttu-id="c4880-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="c4880-132">CheckStates</span></span>|<span data-ttu-id="c4880-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> は `true` です。</span><span class="sxs-lookup"><span data-stu-id="c4880-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|  
|<span data-ttu-id="c4880-134">オンになっていません。</span><span class="sxs-lookup"><span data-stu-id="c4880-134">Unchecked</span></span>|<span data-ttu-id="c4880-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="c4880-135">CheckStates</span></span>|<span data-ttu-id="c4880-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> は `false` です。</span><span class="sxs-lookup"><span data-stu-id="c4880-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|  
|<span data-ttu-id="c4880-137">不確定です</span><span class="sxs-lookup"><span data-stu-id="c4880-137">Indeterminate</span></span>|<span data-ttu-id="c4880-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="c4880-138">CheckStates</span></span>|<span data-ttu-id="c4880-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A>is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span><span class="sxs-lookup"><span data-stu-id="c4880-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|  
|<span data-ttu-id="c4880-140">有効</span><span class="sxs-lookup"><span data-stu-id="c4880-140">Valid</span></span>|<span data-ttu-id="c4880-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c4880-141">ValidationStates</span></span>|<span data-ttu-id="c4880-142">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="c4880-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="c4880-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="c4880-143">InvalidFocused</span></span>|<span data-ttu-id="c4880-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c4880-144">ValidationStates</span></span>|<span data-ttu-id="c4880-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="c4880-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="c4880-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="c4880-146">InvalidUnfocused</span></span>|<span data-ttu-id="c4880-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c4880-147">ValidationStates</span></span>|<span data-ttu-id="c4880-148"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="c4880-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="radiobutton-controltemplate-example"></a><span data-ttu-id="c4880-149">オプション ボタン ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="c4880-149">RadioButton ControlTemplate Example</span></span>  
 <span data-ttu-id="c4880-150">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.RadioButton>コントロール。</span><span class="sxs-lookup"><span data-stu-id="c4880-150">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.RadioButton> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#RadioButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/radiobutton.xaml#radiobutton)]  
  
 <span data-ttu-id="c4880-151">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="c4880-151">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="c4880-152">完全なサンプルについては、[Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4880-152">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4880-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4880-153">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="c4880-154">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="c4880-154">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="c4880-155">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="c4880-155">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="c4880-156">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="c4880-156">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="c4880-157">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="c4880-157">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
