---
title: "メニューのスタイルとテンプレート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], Menu
- ControlTemplate [WPF], Menu
- Menu [WPF], styles and templates
- states [WPF], Menu
- templates [WPF], Menu
- parts [WPF], Menu
ms.assetid: b89da183-9b87-42c6-ac53-731a42c7b09e
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1e007ae09e57353446feb13b3693e62c985f522d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="menu-styles-and-templates"></a><span data-ttu-id="d9a0b-102">メニューのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="d9a0b-102">Menu Styles and Templates</span></span>
<span data-ttu-id="d9a0b-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.Menu>コントロール。</span><span class="sxs-lookup"><span data-stu-id="d9a0b-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Menu> control.</span></span> <span data-ttu-id="d9a0b-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="d9a0b-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d9a0b-105">詳細については、「[Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9a0b-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="menu-parts"></a><span data-ttu-id="d9a0b-106">メニューのパーツ</span><span class="sxs-lookup"><span data-stu-id="d9a0b-106">Menu Parts</span></span>  
 <span data-ttu-id="d9a0b-107"><xref:System.Windows.Controls.Menu>コントロールには、その名前付きの部分はありません。</span><span class="sxs-lookup"><span data-stu-id="d9a0b-107">The <xref:System.Windows.Controls.Menu> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="d9a0b-108">作成するときに、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Menu>、テンプレートを含めることがあります、<xref:System.Windows.Controls.ItemsPresenter>内で、<xref:System.Windows.Controls.ScrollViewer>です。</span><span class="sxs-lookup"><span data-stu-id="d9a0b-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.Menu>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="d9a0b-109">(、<xref:System.Windows.Controls.ItemsPresenter>内の各項目を表示、 <xref:System.Windows.Controls.Menu>;<xref:System.Windows.Controls.ScrollViewer>コントロール内でスクロールできるように) します。</span><span class="sxs-lookup"><span data-stu-id="d9a0b-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.Menu>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="d9a0b-110">場合、<xref:System.Windows.Controls.ItemsPresenter>の直接の子ではない、<xref:System.Windows.Controls.ScrollViewer>を付ける必要があります、<xref:System.Windows.Controls.ItemsPresenter>名、`ItemsPresenter`です。</span><span class="sxs-lookup"><span data-stu-id="d9a0b-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="menu-states"></a><span data-ttu-id="d9a0b-111">メニューの状態</span><span class="sxs-lookup"><span data-stu-id="d9a0b-111">Menu States</span></span>  
 <span data-ttu-id="d9a0b-112">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.Menu>コントロール。</span><span class="sxs-lookup"><span data-stu-id="d9a0b-112">The following table lists the visual states for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
|<span data-ttu-id="d9a0b-113">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="d9a0b-113">VisualState Name</span></span>|<span data-ttu-id="d9a0b-114">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="d9a0b-114">VisualStateGroup Name</span></span>|<span data-ttu-id="d9a0b-115">説明</span><span class="sxs-lookup"><span data-stu-id="d9a0b-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d9a0b-116">有効</span><span class="sxs-lookup"><span data-stu-id="d9a0b-116">Valid</span></span>|<span data-ttu-id="d9a0b-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d9a0b-117">ValidationStates</span></span>|<span data-ttu-id="d9a0b-118">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="d9a0b-118">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d9a0b-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d9a0b-119">InvalidFocused</span></span>|<span data-ttu-id="d9a0b-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d9a0b-120">ValidationStates</span></span>|<span data-ttu-id="d9a0b-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="d9a0b-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d9a0b-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d9a0b-122">InvalidUnfocused</span></span>|<span data-ttu-id="d9a0b-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d9a0b-123">ValidationStates</span></span>|<span data-ttu-id="d9a0b-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="d9a0b-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="menuitem-parts"></a><span data-ttu-id="d9a0b-125">MenuItem のパーツ</span><span class="sxs-lookup"><span data-stu-id="d9a0b-125">MenuItem Parts</span></span>  
 <span data-ttu-id="d9a0b-126">次の表に、名前付きのパーツの<xref:System.Windows.Controls.Menu>コントロール。</span><span class="sxs-lookup"><span data-stu-id="d9a0b-126">The following table lists the named parts for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
|<span data-ttu-id="d9a0b-127">パーツ</span><span class="sxs-lookup"><span data-stu-id="d9a0b-127">Part</span></span>|<span data-ttu-id="d9a0b-128">型</span><span class="sxs-lookup"><span data-stu-id="d9a0b-128">Type</span></span>|<span data-ttu-id="d9a0b-129">説明</span><span class="sxs-lookup"><span data-stu-id="d9a0b-129">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d9a0b-130">PART_Popup</span><span class="sxs-lookup"><span data-stu-id="d9a0b-130">PART_Popup</span></span>|<xref:System.Windows.Controls.Primitives.Popup>|<span data-ttu-id="d9a0b-131">サブメニューの領域です。</span><span class="sxs-lookup"><span data-stu-id="d9a0b-131">The area for the submenu.</span></span>|  
  
 <span data-ttu-id="d9a0b-132">作成するときに、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.MenuItem>、テンプレートを含めることがあります、<xref:System.Windows.Controls.ItemsPresenter>内で、<xref:System.Windows.Controls.ScrollViewer>です。</span><span class="sxs-lookup"><span data-stu-id="d9a0b-132">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.MenuItem>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="d9a0b-133">(、<xref:System.Windows.Controls.ItemsPresenter>内の各項目を表示、 <xref:System.Windows.Controls.MenuItem>;<xref:System.Windows.Controls.ScrollViewer>コントロール内でスクロールできるように) します。</span><span class="sxs-lookup"><span data-stu-id="d9a0b-133">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.MenuItem>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="d9a0b-134">場合、<xref:System.Windows.Controls.ItemsPresenter>の直接の子ではない、<xref:System.Windows.Controls.ScrollViewer>を付ける必要があります、<xref:System.Windows.Controls.ItemsPresenter>名、`ItemsPresenter`です。</span><span class="sxs-lookup"><span data-stu-id="d9a0b-134">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="menuitem-states"></a><span data-ttu-id="d9a0b-135">MenuItem の状態</span><span class="sxs-lookup"><span data-stu-id="d9a0b-135">MenuItem States</span></span>  
 <span data-ttu-id="d9a0b-136">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.MenuItem>コントロール。</span><span class="sxs-lookup"><span data-stu-id="d9a0b-136">The following table lists the visual states for the <xref:System.Windows.Controls.MenuItem> control.</span></span>  
  
|<span data-ttu-id="d9a0b-137">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="d9a0b-137">VisualState Name</span></span>|<span data-ttu-id="d9a0b-138">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="d9a0b-138">VisualStateGroup Name</span></span>|<span data-ttu-id="d9a0b-139">説明</span><span class="sxs-lookup"><span data-stu-id="d9a0b-139">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d9a0b-140">有効</span><span class="sxs-lookup"><span data-stu-id="d9a0b-140">Valid</span></span>|<span data-ttu-id="d9a0b-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d9a0b-141">ValidationStates</span></span>|<span data-ttu-id="d9a0b-142">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="d9a0b-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d9a0b-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d9a0b-143">InvalidFocused</span></span>|<span data-ttu-id="d9a0b-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d9a0b-144">ValidationStates</span></span>|<span data-ttu-id="d9a0b-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="d9a0b-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d9a0b-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d9a0b-146">InvalidUnfocused</span></span>|<span data-ttu-id="d9a0b-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d9a0b-147">ValidationStates</span></span>|<span data-ttu-id="d9a0b-148"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="d9a0b-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="menu-and-menuitem-controltemplate-example"></a><span data-ttu-id="d9a0b-149">メニューと MenuItem ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="d9a0b-149">Menu and MenuItem ControlTemplate Example</span></span>  
 <span data-ttu-id="d9a0b-150">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Menu>コントロール。</span><span class="sxs-lookup"><span data-stu-id="d9a0b-150">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Menu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menu)]  
  
 <span data-ttu-id="d9a0b-151">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.MenuItem>コントロール。</span><span class="sxs-lookup"><span data-stu-id="d9a0b-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.MenuItem> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#MenuItem](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuitem)]  
  
 <span data-ttu-id="d9a0b-152">次の例では定義、 `MenuScrollViewer`、前の例で使用されます。</span><span class="sxs-lookup"><span data-stu-id="d9a0b-152">The following example defines the `MenuScrollViewer`, which is used in the previous example.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#MenuScrollViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuscrollviewer)]  
  
 <span data-ttu-id="d9a0b-153"><xref:System.Windows.Controls.ControlTemplate>の例は、1 つ以上の次のリソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="d9a0b-153">The <xref:System.Windows.Controls.ControlTemplate> examples use one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="d9a0b-154">完全なサンプルについては、[Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9a0b-154">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9a0b-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9a0b-155">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="d9a0b-156">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="d9a0b-156">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="d9a0b-157">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="d9a0b-157">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="d9a0b-158">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="d9a0b-158">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="d9a0b-159">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="d9a0b-159">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
