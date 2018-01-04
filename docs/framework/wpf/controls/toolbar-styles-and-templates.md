---
title: "ToolBar のスタイルとテンプレート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], ToolBar
- styles [WPF], ToolBar
- ControlTemplate [WPF], ToolBar
- parts [WPF], ToolBar
- ToolBar [WPF], styles and templates
- templates [WPF], ToolBar
ms.assetid: bd875f46-4690-46f5-81e0-f11a9822484f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d56858f3785a4d4d49a0781fbf4c19397a3bb375
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="toolbar-styles-and-templates"></a><span data-ttu-id="42833-102">ToolBar のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="42833-102">ToolBar Styles and Templates</span></span>
<span data-ttu-id="42833-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.ToolBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="42833-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolBar> control.</span></span> <span data-ttu-id="42833-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="42833-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="42833-105">詳細については、「[Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42833-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="toolbar-parts"></a><span data-ttu-id="42833-106">ツールバーのパーツ</span><span class="sxs-lookup"><span data-stu-id="42833-106">ToolBar Parts</span></span>  
 <span data-ttu-id="42833-107">次の表に、名前付きのパーツの<xref:System.Windows.Controls.ToolBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="42833-107">The following table lists the named parts for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="42833-108">パーツ</span><span class="sxs-lookup"><span data-stu-id="42833-108">Part</span></span>|<span data-ttu-id="42833-109">型</span><span class="sxs-lookup"><span data-stu-id="42833-109">Type</span></span>|<span data-ttu-id="42833-110">説明</span><span class="sxs-lookup"><span data-stu-id="42833-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="42833-111">PART_ToolBarPanel</span><span class="sxs-lookup"><span data-stu-id="42833-111">PART_ToolBarPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarPanel>|<span data-ttu-id="42833-112">上のコントロールを格納しているオブジェクト、<xref:System.Windows.Controls.ToolBar>です。</span><span class="sxs-lookup"><span data-stu-id="42833-112">The object that contains the controls on the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
|<span data-ttu-id="42833-113">PART_ToolBarOverflowPanel</span><span class="sxs-lookup"><span data-stu-id="42833-113">PART_ToolBarOverflowPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|<span data-ttu-id="42833-114">オーバーフロー領域内にあるコントロールを格納しているオブジェクト、<xref:System.Windows.Controls.ToolBar>です。</span><span class="sxs-lookup"><span data-stu-id="42833-114">The object that contains the controls that are in the overflow area of the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
  
 <span data-ttu-id="42833-115">作成するときに、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.ToolBar>、テンプレートを含めることがあります、<xref:System.Windows.Controls.ItemsPresenter>内で、<xref:System.Windows.Controls.ScrollViewer>です。</span><span class="sxs-lookup"><span data-stu-id="42833-115">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ToolBar>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="42833-116">(、<xref:System.Windows.Controls.ItemsPresenter>内の各項目を表示、 <xref:System.Windows.Controls.ToolBar>;<xref:System.Windows.Controls.ScrollViewer>コントロール内でスクロールできるように) します。</span><span class="sxs-lookup"><span data-stu-id="42833-116">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ToolBar>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="42833-117">場合、<xref:System.Windows.Controls.ItemsPresenter>の直接の子ではない、<xref:System.Windows.Controls.ScrollViewer>を付ける必要があります、<xref:System.Windows.Controls.ItemsPresenter>名、`ItemsPresenter`です。</span><span class="sxs-lookup"><span data-stu-id="42833-117">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="toolbar-states"></a><span data-ttu-id="42833-118">ツールバーの状態</span><span class="sxs-lookup"><span data-stu-id="42833-118">ToolBar States</span></span>  
 <span data-ttu-id="42833-119">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.ToolBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="42833-119">The following table lists the visual states for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="42833-120">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="42833-120">VisualState Name</span></span>|<span data-ttu-id="42833-121">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="42833-121">VisualStateGroup Name</span></span>|<span data-ttu-id="42833-122">説明</span><span class="sxs-lookup"><span data-stu-id="42833-122">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="42833-123">有効</span><span class="sxs-lookup"><span data-stu-id="42833-123">Valid</span></span>|<span data-ttu-id="42833-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="42833-124">ValidationStates</span></span>|<span data-ttu-id="42833-125">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="42833-125">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="42833-126">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="42833-126">InvalidFocused</span></span>|<span data-ttu-id="42833-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="42833-127">ValidationStates</span></span>|<span data-ttu-id="42833-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="42833-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="42833-129">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="42833-129">InvalidUnfocused</span></span>|<span data-ttu-id="42833-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="42833-130">ValidationStates</span></span>|<span data-ttu-id="42833-131"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="42833-131">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="toolbar-controltemplate-example"></a><span data-ttu-id="42833-132">ツールバー ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="42833-132">ToolBar ControlTemplate Example</span></span>  
 <span data-ttu-id="42833-133">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.ToolBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="42833-133">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/toolbar.xaml#toolbar)]  
  
 <span data-ttu-id="42833-134">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="42833-134">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="42833-135">完全なサンプルについては、[Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42833-135">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42833-136">参照</span><span class="sxs-lookup"><span data-stu-id="42833-136">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="42833-137">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="42833-137">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="42833-138">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="42833-138">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="42833-139">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="42833-139">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="42833-140">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="42833-140">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
