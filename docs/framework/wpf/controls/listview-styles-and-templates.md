---
title: "ListView のスタイルとテンプレート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], ListView
- states [WPF], ListView
- ControlTemplate [WPF], ListView
- styles [WPF], ListView
- ListView [WPF], styles and templates
- templates [WPF], ListView
ms.assetid: d2387356-2171-4785-822a-7247e024b4ee
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ccd597aa6d517bb3a7dda347c26c0eaf731a278f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="listview-styles-and-templates"></a><span data-ttu-id="5acca-102">ListView のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="5acca-102">ListView Styles and Templates</span></span>
<span data-ttu-id="5acca-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.ListView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="5acca-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="5acca-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="5acca-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="5acca-105">詳細については、「[Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5acca-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="listview-parts"></a><span data-ttu-id="5acca-106">ListView のパーツ</span><span class="sxs-lookup"><span data-stu-id="5acca-106">ListView Parts</span></span>  
 <span data-ttu-id="5acca-107"><xref:System.Windows.Controls.ListView>コントロールには、その名前付きの部分はありません。</span><span class="sxs-lookup"><span data-stu-id="5acca-107">The <xref:System.Windows.Controls.ListView> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="5acca-108">作成するときに、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.ListView>、テンプレートを含めることがあります、<xref:System.Windows.Controls.ItemsPresenter>内で、<xref:System.Windows.Controls.ScrollViewer>です。</span><span class="sxs-lookup"><span data-stu-id="5acca-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ListView>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="5acca-109">(、<xref:System.Windows.Controls.ItemsPresenter>内の各項目を表示、 <xref:System.Windows.Controls.ListView>;<xref:System.Windows.Controls.ScrollViewer>コントロール内でスクロールできるように) します。</span><span class="sxs-lookup"><span data-stu-id="5acca-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ListView>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="5acca-110">場合、<xref:System.Windows.Controls.ItemsPresenter>の直接の子ではない、<xref:System.Windows.Controls.ScrollViewer>を付ける必要があります、<xref:System.Windows.Controls.ItemsPresenter>名、`ItemsPresenter`です。</span><span class="sxs-lookup"><span data-stu-id="5acca-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="listview-states"></a><span data-ttu-id="5acca-111">ListView の状態</span><span class="sxs-lookup"><span data-stu-id="5acca-111">ListView States</span></span>  
 <span data-ttu-id="5acca-112">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.ListView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="5acca-112">The following table lists the visual states for the <xref:System.Windows.Controls.ListView> control.</span></span>  
  
|<span data-ttu-id="5acca-113">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="5acca-113">VisualState Name</span></span>|<span data-ttu-id="5acca-114">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="5acca-114">VisualStateGroup Name</span></span>|<span data-ttu-id="5acca-115">説明</span><span class="sxs-lookup"><span data-stu-id="5acca-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="5acca-116">有効</span><span class="sxs-lookup"><span data-stu-id="5acca-116">Valid</span></span>|<span data-ttu-id="5acca-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5acca-117">ValidationStates</span></span>|<span data-ttu-id="5acca-118">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="5acca-118">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="5acca-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="5acca-119">InvalidFocused</span></span>|<span data-ttu-id="5acca-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5acca-120">ValidationStates</span></span>|<span data-ttu-id="5acca-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="5acca-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="5acca-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="5acca-122">InvalidUnfocused</span></span>|<span data-ttu-id="5acca-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5acca-123">ValidationStates</span></span>|<span data-ttu-id="5acca-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="5acca-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="listviewitem-parts"></a><span data-ttu-id="5acca-125">ListViewItem のパーツ</span><span class="sxs-lookup"><span data-stu-id="5acca-125">ListViewItem Parts</span></span>  
 <span data-ttu-id="5acca-126"><xref:System.Windows.Controls.ListViewItem>コントロールには、その名前付きの部分はありません。</span><span class="sxs-lookup"><span data-stu-id="5acca-126">The <xref:System.Windows.Controls.ListViewItem> control does not have any named parts.</span></span>  
  
## <a name="listviewitem-states"></a><span data-ttu-id="5acca-127">ListViewItem の状態</span><span class="sxs-lookup"><span data-stu-id="5acca-127">ListViewItem States</span></span>  
 <span data-ttu-id="5acca-128">次の表に、状態、<xref:System.Windows.Controls.ListViewItem>コントロール。</span><span class="sxs-lookup"><span data-stu-id="5acca-128">The following table lists the states for the <xref:System.Windows.Controls.ListViewItem> control.</span></span>  
  
|<span data-ttu-id="5acca-129">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="5acca-129">VisualState Name</span></span>|<span data-ttu-id="5acca-130">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="5acca-130">VisualStateGroup Name</span></span>|<span data-ttu-id="5acca-131">説明</span><span class="sxs-lookup"><span data-stu-id="5acca-131">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="5acca-132">標準</span><span class="sxs-lookup"><span data-stu-id="5acca-132">Normal</span></span>|<span data-ttu-id="5acca-133">CommonStates</span><span class="sxs-lookup"><span data-stu-id="5acca-133">CommonStates</span></span>|<span data-ttu-id="5acca-134">既定の状態です。</span><span class="sxs-lookup"><span data-stu-id="5acca-134">The default state.</span></span>|  
|<span data-ttu-id="5acca-135">無効</span><span class="sxs-lookup"><span data-stu-id="5acca-135">Disabled</span></span>|<span data-ttu-id="5acca-136">CommonStates</span><span class="sxs-lookup"><span data-stu-id="5acca-136">CommonStates</span></span>|<span data-ttu-id="5acca-137">コントロールが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="5acca-137">The control is disabled.</span></span>|  
|<span data-ttu-id="5acca-138">MouseOver</span><span class="sxs-lookup"><span data-stu-id="5acca-138">MouseOver</span></span>|<span data-ttu-id="5acca-139">CommonStates</span><span class="sxs-lookup"><span data-stu-id="5acca-139">CommonStates</span></span>|<span data-ttu-id="5acca-140">上にマウス ポインターが、<xref:System.Windows.Controls.ComboBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="5acca-140">The mouse pointer is over the <xref:System.Windows.Controls.ComboBox> control.</span></span>|  
|<span data-ttu-id="5acca-141">フォーカスされている</span><span class="sxs-lookup"><span data-stu-id="5acca-141">Focused</span></span>|<span data-ttu-id="5acca-142">FocusStates</span><span class="sxs-lookup"><span data-stu-id="5acca-142">FocusStates</span></span>|<span data-ttu-id="5acca-143">コントロールにフォーカスがあります。</span><span class="sxs-lookup"><span data-stu-id="5acca-143">The control has focus.</span></span>|  
|<span data-ttu-id="5acca-144">フォーカスされていない</span><span class="sxs-lookup"><span data-stu-id="5acca-144">Unfocused</span></span>|<span data-ttu-id="5acca-145">FocusStates</span><span class="sxs-lookup"><span data-stu-id="5acca-145">FocusStates</span></span>|<span data-ttu-id="5acca-146">コントロールにフォーカスがありません。</span><span class="sxs-lookup"><span data-stu-id="5acca-146">The control does not have focus.</span></span>|  
|<span data-ttu-id="5acca-147">選択済み</span><span class="sxs-lookup"><span data-stu-id="5acca-147">Selected</span></span>|<span data-ttu-id="5acca-148">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="5acca-148">SelectionStates</span></span>|<span data-ttu-id="5acca-149">項目が現在選択されています。</span><span class="sxs-lookup"><span data-stu-id="5acca-149">The item is currently selected.</span></span>|  
|<span data-ttu-id="5acca-150">未選択</span><span class="sxs-lookup"><span data-stu-id="5acca-150">Unselected</span></span>|<span data-ttu-id="5acca-151">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="5acca-151">SelectionStates</span></span>|<span data-ttu-id="5acca-152">この項目は選択されていません。</span><span class="sxs-lookup"><span data-stu-id="5acca-152">The item is not selected.</span></span>|  
|<span data-ttu-id="5acca-153">SelectedUnfocused</span><span class="sxs-lookup"><span data-stu-id="5acca-153">SelectedUnfocused</span></span>|<span data-ttu-id="5acca-154">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="5acca-154">SelectionStates</span></span>|<span data-ttu-id="5acca-155">この項目は選択されていますが、フォーカスがありません。</span><span class="sxs-lookup"><span data-stu-id="5acca-155">The item is selected, but does not have focus.</span></span>|  
|<span data-ttu-id="5acca-156">有効</span><span class="sxs-lookup"><span data-stu-id="5acca-156">Valid</span></span>|<span data-ttu-id="5acca-157">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5acca-157">ValidationStates</span></span>|<span data-ttu-id="5acca-158">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="5acca-158">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="5acca-159">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="5acca-159">InvalidFocused</span></span>|<span data-ttu-id="5acca-160">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5acca-160">ValidationStates</span></span>|<span data-ttu-id="5acca-161"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="5acca-161">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="5acca-162">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="5acca-162">InvalidUnfocused</span></span>|<span data-ttu-id="5acca-163">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5acca-163">ValidationStates</span></span>|<span data-ttu-id="5acca-164"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="5acca-164">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="listview-controltemplate-examples"></a><span data-ttu-id="5acca-165">ListView ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="5acca-165">ListView ControlTemplate Examples</span></span>  
 <span data-ttu-id="5acca-166">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.ListView>コントロールとその関連する型。</span><span class="sxs-lookup"><span data-stu-id="5acca-166">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ListView> control and its associated types.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ListView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listview.xaml#listview)]  
  
 <span data-ttu-id="5acca-167"><xref:System.Windows.Controls.ControlTemplate>の例は、1 つ以上の次のリソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="5acca-167">The <xref:System.Windows.Controls.ControlTemplate> examples use one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="5acca-168">完全なサンプルについては、[Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5acca-168">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5acca-169">関連項目</span><span class="sxs-lookup"><span data-stu-id="5acca-169">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="5acca-170">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="5acca-170">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="5acca-171">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="5acca-171">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="5acca-172">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="5acca-172">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="5acca-173">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="5acca-173">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
