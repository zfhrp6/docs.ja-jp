---
title: "ListBox のスタイルとテンプレート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], ListBox
- templates [WPF], ListBox
- states [WPF], ListBox
- ControlTemplate [WPF], ListBox
- parts [WPF], ListBox
- ListBox [WPF], styles and templates
ms.assetid: fc5764cb-c27b-495b-88d4-d969a8213ccb
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: df974b2f6f89c3b62c5039be9cde144d9ef62d14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="listbox-styles-and-templates"></a><span data-ttu-id="5beba-102">ListBox のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="5beba-102">ListBox Styles and Templates</span></span>
<span data-ttu-id="5beba-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.ListBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="5beba-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="5beba-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="5beba-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="5beba-105">詳細については、「[Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5beba-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="listbox-parts"></a><span data-ttu-id="5beba-106">ListBox パーツ</span><span class="sxs-lookup"><span data-stu-id="5beba-106">ListBox Parts</span></span>  
 <span data-ttu-id="5beba-107"><xref:System.Windows.Controls.ListBox>コントロールには、その名前付きの部分はありません。</span><span class="sxs-lookup"><span data-stu-id="5beba-107">The <xref:System.Windows.Controls.ListBox> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="5beba-108">作成するときに、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.ListBox>、テンプレートを含めることがあります、<xref:System.Windows.Controls.ItemsPresenter>内で、<xref:System.Windows.Controls.ScrollViewer>です。</span><span class="sxs-lookup"><span data-stu-id="5beba-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ListBox>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="5beba-109">(、<xref:System.Windows.Controls.ItemsPresenter>内の各項目を表示、 <xref:System.Windows.Controls.ListBox>;<xref:System.Windows.Controls.ScrollViewer>コントロール内でスクロールできるように) します。</span><span class="sxs-lookup"><span data-stu-id="5beba-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ListBox>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="5beba-110">場合、<xref:System.Windows.Controls.ItemsPresenter>の直接の子ではない、<xref:System.Windows.Controls.ScrollViewer>を付ける必要があります、<xref:System.Windows.Controls.ItemsPresenter>名、`ItemsPresenter`です。</span><span class="sxs-lookup"><span data-stu-id="5beba-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="listbox-states"></a><span data-ttu-id="5beba-111">リスト ボックスの状態</span><span class="sxs-lookup"><span data-stu-id="5beba-111">ListBox States</span></span>  
 <span data-ttu-id="5beba-112">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.ListBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="5beba-112">The following table lists the visual states for the <xref:System.Windows.Controls.ListBox> control.</span></span>  
  
|<span data-ttu-id="5beba-113">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="5beba-113">VisualState Name</span></span>|<span data-ttu-id="5beba-114">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="5beba-114">VisualStateGroup Name</span></span>|<span data-ttu-id="5beba-115">説明</span><span class="sxs-lookup"><span data-stu-id="5beba-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="5beba-116">有効</span><span class="sxs-lookup"><span data-stu-id="5beba-116">Valid</span></span>|<span data-ttu-id="5beba-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5beba-117">ValidationStates</span></span>|<span data-ttu-id="5beba-118">コントロールは有効です。</span><span class="sxs-lookup"><span data-stu-id="5beba-118">The control is valid.</span></span>|  
|<span data-ttu-id="5beba-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="5beba-119">InvalidFocused</span></span>|<span data-ttu-id="5beba-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5beba-120">ValidationStates</span></span>|<span data-ttu-id="5beba-121">コントロールが無効で、フォーカスがあります。</span><span class="sxs-lookup"><span data-stu-id="5beba-121">The control is not valid and has focus.</span></span>|  
|<span data-ttu-id="5beba-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="5beba-122">InvalidUnfocused</span></span>|<span data-ttu-id="5beba-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5beba-123">ValidationStates</span></span>|<span data-ttu-id="5beba-124">コントロールが無効で、フォーカスがありません。</span><span class="sxs-lookup"><span data-stu-id="5beba-124">The control is not valid and does not have focus.</span></span>|  
  
## <a name="listboxitem-parts"></a><span data-ttu-id="5beba-125">ListBoxItem のパーツ</span><span class="sxs-lookup"><span data-stu-id="5beba-125">ListBoxItem Parts</span></span>  
 <span data-ttu-id="5beba-126"><xref:System.Windows.Controls.ListBoxItem>コントロールには、その名前付きの部分はありません。</span><span class="sxs-lookup"><span data-stu-id="5beba-126">The <xref:System.Windows.Controls.ListBoxItem> control does not have any named parts.</span></span>  
  
## <a name="listboxitem-states"></a><span data-ttu-id="5beba-127">ListBoxItem の状態</span><span class="sxs-lookup"><span data-stu-id="5beba-127">ListBoxItem States</span></span>  
 <span data-ttu-id="5beba-128">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.ListBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="5beba-128">The following table lists the visual states for the <xref:System.Windows.Controls.ListBox> control.</span></span>  
  
|<span data-ttu-id="5beba-129">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="5beba-129">VisualState Name</span></span>|<span data-ttu-id="5beba-130">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="5beba-130">VisualStateGroup Name</span></span>|<span data-ttu-id="5beba-131">説明</span><span class="sxs-lookup"><span data-stu-id="5beba-131">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="5beba-132">標準</span><span class="sxs-lookup"><span data-stu-id="5beba-132">Normal</span></span>|<span data-ttu-id="5beba-133">CommonStates</span><span class="sxs-lookup"><span data-stu-id="5beba-133">CommonStates</span></span>|<span data-ttu-id="5beba-134">既定の状態です。</span><span class="sxs-lookup"><span data-stu-id="5beba-134">The default state.</span></span>|  
|<span data-ttu-id="5beba-135">MouseOver</span><span class="sxs-lookup"><span data-stu-id="5beba-135">MouseOver</span></span>|<span data-ttu-id="5beba-136">CommonStates</span><span class="sxs-lookup"><span data-stu-id="5beba-136">CommonStates</span></span>|<span data-ttu-id="5beba-137">マウス ポインターがコントロール上に配置されます。</span><span class="sxs-lookup"><span data-stu-id="5beba-137">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="5beba-138">無効</span><span class="sxs-lookup"><span data-stu-id="5beba-138">Disabled</span></span>|<span data-ttu-id="5beba-139">CommonStates</span><span class="sxs-lookup"><span data-stu-id="5beba-139">CommonStates</span></span>|<span data-ttu-id="5beba-140">この項目は無効です。</span><span class="sxs-lookup"><span data-stu-id="5beba-140">The item is disabled.</span></span>|  
|<span data-ttu-id="5beba-141">フォーカスされている</span><span class="sxs-lookup"><span data-stu-id="5beba-141">Focused</span></span>|<span data-ttu-id="5beba-142">FocusStates</span><span class="sxs-lookup"><span data-stu-id="5beba-142">FocusStates</span></span>|<span data-ttu-id="5beba-143">この項目にフォーカスがあります。</span><span class="sxs-lookup"><span data-stu-id="5beba-143">The item has focus.</span></span>|  
|<span data-ttu-id="5beba-144">フォーカスされていない</span><span class="sxs-lookup"><span data-stu-id="5beba-144">Unfocused</span></span>|<span data-ttu-id="5beba-145">FocusStates</span><span class="sxs-lookup"><span data-stu-id="5beba-145">FocusStates</span></span>|<span data-ttu-id="5beba-146">この項目にフォーカスがありません。</span><span class="sxs-lookup"><span data-stu-id="5beba-146">The item does not have focus.</span></span>|  
|<span data-ttu-id="5beba-147">未選択</span><span class="sxs-lookup"><span data-stu-id="5beba-147">Unselected</span></span>|<span data-ttu-id="5beba-148">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="5beba-148">SelectionStates</span></span>|<span data-ttu-id="5beba-149">この項目は選択されていません。</span><span class="sxs-lookup"><span data-stu-id="5beba-149">The item is not selected.</span></span>|  
|<span data-ttu-id="5beba-150">選択済み</span><span class="sxs-lookup"><span data-stu-id="5beba-150">Selected</span></span>|<span data-ttu-id="5beba-151">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="5beba-151">SelectionStates</span></span>|<span data-ttu-id="5beba-152">この項目は、選択した currentlyplate です。</span><span class="sxs-lookup"><span data-stu-id="5beba-152">The item is currentlyplate selected.</span></span>|  
|<span data-ttu-id="5beba-153">SelectedUnfocused</span><span class="sxs-lookup"><span data-stu-id="5beba-153">SelectedUnfocused</span></span>|<span data-ttu-id="5beba-154">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="5beba-154">SelectionStates</span></span>|<span data-ttu-id="5beba-155">この項目は選択されていますが、フォーカスがありません。</span><span class="sxs-lookup"><span data-stu-id="5beba-155">The item is selected, but does not have focus.</span></span>|  
|<span data-ttu-id="5beba-156">有効</span><span class="sxs-lookup"><span data-stu-id="5beba-156">Valid</span></span>|<span data-ttu-id="5beba-157">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5beba-157">ValidationStates</span></span>|<span data-ttu-id="5beba-158">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="5beba-158">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="5beba-159">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="5beba-159">InvalidFocused</span></span>|<span data-ttu-id="5beba-160">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5beba-160">ValidationStates</span></span>|<span data-ttu-id="5beba-161"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="5beba-161">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="5beba-162">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="5beba-162">InvalidUnfocused</span></span>|<span data-ttu-id="5beba-163">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5beba-163">ValidationStates</span></span>|<span data-ttu-id="5beba-164"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="5beba-164">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="listbox-controltemplate-example"></a><span data-ttu-id="5beba-165">ListBox ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="5beba-165">ListBox ControlTemplate Example</span></span>  
 <span data-ttu-id="5beba-166">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.ListBox>と<xref:System.Windows.Controls.ListBoxItem>コントロール。</span><span class="sxs-lookup"><span data-stu-id="5beba-166">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ListBox> and <xref:System.Windows.Controls.ListBoxItem> controls.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listbox.xaml#listbox)]  
  
 <span data-ttu-id="5beba-167">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="5beba-167">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="5beba-168">完全なサンプルについては、[Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5beba-168">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5beba-169">関連項目</span><span class="sxs-lookup"><span data-stu-id="5beba-169">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="5beba-170">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="5beba-170">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="5beba-171">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="5beba-171">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="5beba-172">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="5beba-172">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="5beba-173">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="5beba-173">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
