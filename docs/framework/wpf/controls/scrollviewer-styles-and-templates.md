---
title: "ScrollViewer のスタイルとテンプレート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], ScrollViewer
- states [WPF], ScrollViewer
- styles [WPF], ScrollViewer
- templates [WPF], ScrollViewer
- ControlTemplate [WPF], ScrollViewer
- ScrollViewer [WPF], styles and templates
ms.assetid: dffdd822-ae69-4946-abaf-710860cd65b2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ac02896708744bc9b1c2d017da4e6f56ac32b53a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="scrollviewer-styles-and-templates"></a><span data-ttu-id="8e3b6-102">ScrollViewer のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="8e3b6-102">ScrollViewer Styles and Templates</span></span>
<span data-ttu-id="8e3b6-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.ScrollViewer>コントロール。</span><span class="sxs-lookup"><span data-stu-id="8e3b6-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span> <span data-ttu-id="8e3b6-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="8e3b6-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="8e3b6-105">詳細については、「[Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e3b6-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollviewer-parts"></a><span data-ttu-id="8e3b6-106">ScrollViewer 部分</span><span class="sxs-lookup"><span data-stu-id="8e3b6-106">ScrollViewer Parts</span></span>  
 <span data-ttu-id="8e3b6-107">次の表に、名前付きのパーツの<xref:System.Windows.Controls.ScrollViewer>コントロール。</span><span class="sxs-lookup"><span data-stu-id="8e3b6-107">The following table lists the named parts for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="8e3b6-108">パーツ</span><span class="sxs-lookup"><span data-stu-id="8e3b6-108">Part</span></span>|<span data-ttu-id="8e3b6-109">型</span><span class="sxs-lookup"><span data-stu-id="8e3b6-109">Type</span></span>|<span data-ttu-id="8e3b6-110">説明</span><span class="sxs-lookup"><span data-stu-id="8e3b6-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="8e3b6-111">PART_ScrollContentPresenter</span><span class="sxs-lookup"><span data-stu-id="8e3b6-111">PART_ScrollContentPresenter</span></span>|<xref:System.Windows.Controls.ScrollContentPresenter>|<span data-ttu-id="8e3b6-112">内のコンテンツのプレース ホルダー、<xref:System.Windows.Controls.ScrollViewer>です。</span><span class="sxs-lookup"><span data-stu-id="8e3b6-112">The placeholder for content in the <xref:System.Windows.Controls.ScrollViewer>.</span></span>|  
|<span data-ttu-id="8e3b6-113">PART_HorizontalScrollBar</span><span class="sxs-lookup"><span data-stu-id="8e3b6-113">PART_HorizontalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="8e3b6-114"><xref:System.Windows.Controls.Primitives.ScrollBar>コンテンツを水平方向にスクロールするために使用します。</span><span class="sxs-lookup"><span data-stu-id="8e3b6-114">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content horizontally.</span></span>|  
|<span data-ttu-id="8e3b6-115">PART_VerticalScrollBar</span><span class="sxs-lookup"><span data-stu-id="8e3b6-115">PART_VerticalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="8e3b6-116"><xref:System.Windows.Controls.Primitives.ScrollBar>コンテンツを垂直方向にスクロールするために使用します。</span><span class="sxs-lookup"><span data-stu-id="8e3b6-116">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content vertically.</span></span>|  
  
## <a name="scrollviewer-states"></a><span data-ttu-id="8e3b6-117">ScrollViewer 状態</span><span class="sxs-lookup"><span data-stu-id="8e3b6-117">ScrollViewer States</span></span>  
 <span data-ttu-id="8e3b6-118">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.ScrollViewer>コントロール。</span><span class="sxs-lookup"><span data-stu-id="8e3b6-118">The following table lists the visual states for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="8e3b6-119">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="8e3b6-119">VisualState Name</span></span>|<span data-ttu-id="8e3b6-120">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="8e3b6-120">VisualStateGroup Name</span></span>|<span data-ttu-id="8e3b6-121">説明</span><span class="sxs-lookup"><span data-stu-id="8e3b6-121">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="8e3b6-122">有効</span><span class="sxs-lookup"><span data-stu-id="8e3b6-122">Valid</span></span>|<span data-ttu-id="8e3b6-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8e3b6-123">ValidationStates</span></span>|<span data-ttu-id="8e3b6-124">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="8e3b6-124">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="8e3b6-125">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="8e3b6-125">InvalidFocused</span></span>|<span data-ttu-id="8e3b6-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8e3b6-126">ValidationStates</span></span>|<span data-ttu-id="8e3b6-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="8e3b6-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="8e3b6-128">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="8e3b6-128">InvalidUnfocused</span></span>|<span data-ttu-id="8e3b6-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8e3b6-129">ValidationStates</span></span>|<span data-ttu-id="8e3b6-130"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="8e3b6-130">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollviewer-controltemplate-example"></a><span data-ttu-id="8e3b6-131">ScrollViewer ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="8e3b6-131">ScrollViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="8e3b6-132">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.ScrollViewer>コントロール。</span><span class="sxs-lookup"><span data-stu-id="8e3b6-132">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollviewer.xaml#scrollviewer)]  
  
 <span data-ttu-id="8e3b6-133">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="8e3b6-133">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="8e3b6-134">完全なサンプルについては、[Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e3b6-134">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e3b6-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="8e3b6-135">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="8e3b6-136">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="8e3b6-136">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="8e3b6-137">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="8e3b6-137">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="8e3b6-138">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="8e3b6-138">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="8e3b6-139">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="8e3b6-139">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
