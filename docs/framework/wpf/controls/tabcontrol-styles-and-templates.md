---
title: "TabControl のスタイルとテンプレート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], TabControl
- TabControl [WPF], styles and templates [WPF]
- parts [WPF], TabControl
- styles [WPF], TabControl
- states [WPF], TabControl
- templates [WPF], TabControl
ms.assetid: f6b19a30-f10e-4fa1-96ce-f17a54092ab6
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 22d1e4dbd8e7a3ca6ec9f0c91e5e59be2f683455
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="tabcontrol-styles-and-templates"></a><span data-ttu-id="e4b74-102">TabControl のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="e4b74-102">TabControl Styles and Templates</span></span>
<span data-ttu-id="e4b74-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.TabControl>コントロール。</span><span class="sxs-lookup"><span data-stu-id="e4b74-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.TabControl> control.</span></span> <span data-ttu-id="e4b74-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="e4b74-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="e4b74-105">詳細については、「[Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4b74-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="tabcontrol-parts"></a><span data-ttu-id="e4b74-106">TabControl 部分</span><span class="sxs-lookup"><span data-stu-id="e4b74-106">TabControl Parts</span></span>  
 <span data-ttu-id="e4b74-107">次の表に、名前付きのパーツの<xref:System.Windows.Controls.TabControl>コントロール。</span><span class="sxs-lookup"><span data-stu-id="e4b74-107">The following table lists the named parts for the <xref:System.Windows.Controls.TabControl> control.</span></span>  
  
|<span data-ttu-id="e4b74-108">パーツ</span><span class="sxs-lookup"><span data-stu-id="e4b74-108">Part</span></span>|<span data-ttu-id="e4b74-109">型</span><span class="sxs-lookup"><span data-stu-id="e4b74-109">Type</span></span>|<span data-ttu-id="e4b74-110">説明</span><span class="sxs-lookup"><span data-stu-id="e4b74-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="e4b74-111">PART_SelectedContentHost</span><span class="sxs-lookup"><span data-stu-id="e4b74-111">PART_SelectedContentHost</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="e4b74-112">現在選択されているの内容を表示するオブジェクト<xref:System.Windows.Controls.TabItem>です。</span><span class="sxs-lookup"><span data-stu-id="e4b74-112">The object that shows the content of the currently selected <xref:System.Windows.Controls.TabItem>.</span></span>|  
  
 <span data-ttu-id="e4b74-113">作成するときに、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.TabControl>、テンプレートを含めることがあります、<xref:System.Windows.Controls.ItemsPresenter>内で、<xref:System.Windows.Controls.ScrollViewer>です。</span><span class="sxs-lookup"><span data-stu-id="e4b74-113">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.TabControl>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="e4b74-114">(、<xref:System.Windows.Controls.ItemsPresenter>内の各項目を表示、 <xref:System.Windows.Controls.TabControl>;<xref:System.Windows.Controls.ScrollViewer>コントロール内でスクロールできるように) します。</span><span class="sxs-lookup"><span data-stu-id="e4b74-114">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.TabControl>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="e4b74-115">場合、<xref:System.Windows.Controls.ItemsPresenter>の直接の子ではない、<xref:System.Windows.Controls.ScrollViewer>を付ける必要があります、<xref:System.Windows.Controls.ItemsPresenter>名、`ItemsPresenter`です。</span><span class="sxs-lookup"><span data-stu-id="e4b74-115">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="tabcontrol-states"></a><span data-ttu-id="e4b74-116">TabControl の状態</span><span class="sxs-lookup"><span data-stu-id="e4b74-116">TabControl States</span></span>  
 <span data-ttu-id="e4b74-117">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.TabControl>コントロール。</span><span class="sxs-lookup"><span data-stu-id="e4b74-117">The following table lists the visual states for the <xref:System.Windows.Controls.TabControl> control.</span></span>  
  
|<span data-ttu-id="e4b74-118">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="e4b74-118">VisualState Name</span></span>|<span data-ttu-id="e4b74-119">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="e4b74-119">VisualStateGroup Name</span></span>|<span data-ttu-id="e4b74-120">説明</span><span class="sxs-lookup"><span data-stu-id="e4b74-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="e4b74-121">標準</span><span class="sxs-lookup"><span data-stu-id="e4b74-121">Normal</span></span>|<span data-ttu-id="e4b74-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e4b74-122">CommonStates</span></span>|<span data-ttu-id="e4b74-123">既定の状態です。</span><span class="sxs-lookup"><span data-stu-id="e4b74-123">The default state.</span></span>|  
|<span data-ttu-id="e4b74-124">無効</span><span class="sxs-lookup"><span data-stu-id="e4b74-124">Disabled</span></span>|<span data-ttu-id="e4b74-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e4b74-125">CommonStates</span></span>|<span data-ttu-id="e4b74-126">コントロールが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="e4b74-126">The control is disabled.</span></span>|  
|<span data-ttu-id="e4b74-127">有効</span><span class="sxs-lookup"><span data-stu-id="e4b74-127">Valid</span></span>|<span data-ttu-id="e4b74-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e4b74-128">ValidationStates</span></span>|<span data-ttu-id="e4b74-129">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="e4b74-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="e4b74-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="e4b74-130">InvalidFocused</span></span>|<span data-ttu-id="e4b74-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e4b74-131">ValidationStates</span></span>|<span data-ttu-id="e4b74-132"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="e4b74-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="e4b74-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="e4b74-133">InvalidUnfocused</span></span>|<span data-ttu-id="e4b74-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e4b74-134">ValidationStates</span></span>|<span data-ttu-id="e4b74-135"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="e4b74-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tabitem-parts"></a><span data-ttu-id="e4b74-136">TabItem 部分</span><span class="sxs-lookup"><span data-stu-id="e4b74-136">TabItem Parts</span></span>  
 <span data-ttu-id="e4b74-137"><xref:System.Windows.Controls.TabItem>コントロールには、その名前付きの部分はありません。</span><span class="sxs-lookup"><span data-stu-id="e4b74-137">The <xref:System.Windows.Controls.TabItem> control does not have any named parts.</span></span>  
  
## <a name="tabitem-states"></a><span data-ttu-id="e4b74-138">TabItem 状態</span><span class="sxs-lookup"><span data-stu-id="e4b74-138">TabItem States</span></span>  
 <span data-ttu-id="e4b74-139">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.TabItem>コントロール。</span><span class="sxs-lookup"><span data-stu-id="e4b74-139">The following table lists the visual states for the <xref:System.Windows.Controls.TabItem> control.</span></span>  
  
|<span data-ttu-id="e4b74-140">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="e4b74-140">VisualState Name</span></span>|<span data-ttu-id="e4b74-141">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="e4b74-141">VisualStateGroup Name</span></span>|<span data-ttu-id="e4b74-142">説明</span><span class="sxs-lookup"><span data-stu-id="e4b74-142">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="e4b74-143">標準</span><span class="sxs-lookup"><span data-stu-id="e4b74-143">Normal</span></span>|<span data-ttu-id="e4b74-144">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e4b74-144">CommonStates</span></span>|<span data-ttu-id="e4b74-145">既定の状態です。</span><span class="sxs-lookup"><span data-stu-id="e4b74-145">The default state.</span></span>|  
|<span data-ttu-id="e4b74-146">MouseOver</span><span class="sxs-lookup"><span data-stu-id="e4b74-146">MouseOver</span></span>|<span data-ttu-id="e4b74-147">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e4b74-147">CommonStates</span></span>|<span data-ttu-id="e4b74-148">マウス ポインターがコントロール上に配置されます。</span><span class="sxs-lookup"><span data-stu-id="e4b74-148">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="e4b74-149">無効</span><span class="sxs-lookup"><span data-stu-id="e4b74-149">Disabled</span></span>|<span data-ttu-id="e4b74-150">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e4b74-150">CommonStates</span></span>|<span data-ttu-id="e4b74-151">コントロールが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="e4b74-151">The control is disabled.</span></span>|  
|<span data-ttu-id="e4b74-152">フォーカスされている</span><span class="sxs-lookup"><span data-stu-id="e4b74-152">Focused</span></span>|<span data-ttu-id="e4b74-153">FocusStates</span><span class="sxs-lookup"><span data-stu-id="e4b74-153">FocusStates</span></span>|<span data-ttu-id="e4b74-154">コントロールにフォーカスがあります。</span><span class="sxs-lookup"><span data-stu-id="e4b74-154">The control has focus.</span></span>|  
|<span data-ttu-id="e4b74-155">フォーカスされていない</span><span class="sxs-lookup"><span data-stu-id="e4b74-155">Unfocused</span></span>|<span data-ttu-id="e4b74-156">FocusStates</span><span class="sxs-lookup"><span data-stu-id="e4b74-156">FocusStates</span></span>|<span data-ttu-id="e4b74-157">コントロールにフォーカスがありません。</span><span class="sxs-lookup"><span data-stu-id="e4b74-157">The control does not have focus.</span></span>|  
|<span data-ttu-id="e4b74-158">選択済み</span><span class="sxs-lookup"><span data-stu-id="e4b74-158">Selected</span></span>|<span data-ttu-id="e4b74-159">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="e4b74-159">SelectionStates</span></span>|<span data-ttu-id="e4b74-160">コントロールが選択されます。</span><span class="sxs-lookup"><span data-stu-id="e4b74-160">The control is selected.</span></span>|  
|<span data-ttu-id="e4b74-161">未選択</span><span class="sxs-lookup"><span data-stu-id="e4b74-161">Unselected</span></span>|<span data-ttu-id="e4b74-162">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="e4b74-162">SelectionStates</span></span>|<span data-ttu-id="e4b74-163">コントロールが選択されていません。</span><span class="sxs-lookup"><span data-stu-id="e4b74-163">The control is not selected.</span></span>|  
|<span data-ttu-id="e4b74-164">有効</span><span class="sxs-lookup"><span data-stu-id="e4b74-164">Valid</span></span>|<span data-ttu-id="e4b74-165">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e4b74-165">ValidationStates</span></span>|<span data-ttu-id="e4b74-166">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="e4b74-166">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="e4b74-167">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="e4b74-167">InvalidFocused</span></span>|<span data-ttu-id="e4b74-168">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e4b74-168">ValidationStates</span></span>|<span data-ttu-id="e4b74-169"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="e4b74-169">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="e4b74-170">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="e4b74-170">InvalidUnfocused</span></span>|<span data-ttu-id="e4b74-171">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e4b74-171">ValidationStates</span></span>|<span data-ttu-id="e4b74-172"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="e4b74-172">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tabcontrol-controltemplate-example"></a><span data-ttu-id="e4b74-173">TabControl ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="e4b74-173">TabControl ControlTemplate Example</span></span>  
 <span data-ttu-id="e4b74-174">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.TabControl>と<xref:System.Windows.Controls.TabItem>コントロール。</span><span class="sxs-lookup"><span data-stu-id="e4b74-174">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TabControl> and <xref:System.Windows.Controls.TabItem> controls.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TabControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tabcontrol.xaml#tabcontrol)]  
  
 <span data-ttu-id="e4b74-175">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="e4b74-175">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="e4b74-176">完全なサンプルについては、[Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4b74-176">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4b74-177">参照</span><span class="sxs-lookup"><span data-stu-id="e4b74-177">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="e4b74-178">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="e4b74-178">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="e4b74-179">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="e4b74-179">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="e4b74-180">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="e4b74-180">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="e4b74-181">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="e4b74-181">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
