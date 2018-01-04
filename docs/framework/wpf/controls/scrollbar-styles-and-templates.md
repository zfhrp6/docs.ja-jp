---
title: "ScrollBar のスタイルとテンプレート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], ScrollBar
- ControlTemplate [WPF], ScrollBar
- states [WPF], ScrollBar
- ScrollBar [WPF], styles and templates
- templates [WPF], ScrollBar
- parts [WPF], ScrollBar
ms.assetid: 066ea45a-e27d-43b0-adfe-cce6934c22f5
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 14b40a458b271a4f8b88c167367771235f25c7a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="61de6-102">ScrollBar のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="61de6-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="61de6-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.Primitives.ScrollBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="61de6-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="61de6-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="61de6-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="61de6-105">詳細については、「[Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61de6-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="61de6-106">スクロール バーのパーツ</span><span class="sxs-lookup"><span data-stu-id="61de6-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="61de6-107">次の表に、名前付きのパーツの<xref:System.Windows.Controls.Primitives.ScrollBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="61de6-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="61de6-108">パーツ</span><span class="sxs-lookup"><span data-stu-id="61de6-108">Part</span></span>|<span data-ttu-id="61de6-109">型</span><span class="sxs-lookup"><span data-stu-id="61de6-109">Type</span></span>|<span data-ttu-id="61de6-110">説明</span><span class="sxs-lookup"><span data-stu-id="61de6-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="61de6-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="61de6-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="61de6-112">要素の位置を示すためのコンテナー、<xref:System.Windows.Controls.Primitives.ScrollBar>です。</span><span class="sxs-lookup"><span data-stu-id="61de6-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="61de6-113">スクロール バーの状態</span><span class="sxs-lookup"><span data-stu-id="61de6-113">ScrollBar States</span></span>  
 <span data-ttu-id="61de6-114">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.Primitives.ScrollBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="61de6-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="61de6-115">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="61de6-115">VisualState Name</span></span>|<span data-ttu-id="61de6-116">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="61de6-116">VisualStateGroup Name</span></span>|<span data-ttu-id="61de6-117">説明</span><span class="sxs-lookup"><span data-stu-id="61de6-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="61de6-118">標準</span><span class="sxs-lookup"><span data-stu-id="61de6-118">Normal</span></span>|<span data-ttu-id="61de6-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="61de6-119">CommonStates</span></span>|<span data-ttu-id="61de6-120">既定の状態です。</span><span class="sxs-lookup"><span data-stu-id="61de6-120">The default state.</span></span>|  
|<span data-ttu-id="61de6-121">MouseOver</span><span class="sxs-lookup"><span data-stu-id="61de6-121">MouseOver</span></span>|<span data-ttu-id="61de6-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="61de6-122">CommonStates</span></span>|<span data-ttu-id="61de6-123">マウス ポインターがコントロール上に配置されます。</span><span class="sxs-lookup"><span data-stu-id="61de6-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="61de6-124">無効</span><span class="sxs-lookup"><span data-stu-id="61de6-124">Disabled</span></span>|<span data-ttu-id="61de6-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="61de6-125">CommonStates</span></span>|<span data-ttu-id="61de6-126">コントロールが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="61de6-126">The control is disabled.</span></span>|  
|<span data-ttu-id="61de6-127">有効</span><span class="sxs-lookup"><span data-stu-id="61de6-127">Valid</span></span>|<span data-ttu-id="61de6-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="61de6-128">ValidationStates</span></span>|<span data-ttu-id="61de6-129">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="61de6-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="61de6-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="61de6-130">InvalidFocused</span></span>|<span data-ttu-id="61de6-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="61de6-131">ValidationStates</span></span>|<span data-ttu-id="61de6-132"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="61de6-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="61de6-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="61de6-133">InvalidUnfocused</span></span>|<span data-ttu-id="61de6-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="61de6-134">ValidationStates</span></span>|<span data-ttu-id="61de6-135"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="61de6-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="61de6-136">スクロール バー ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="61de6-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="61de6-137">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Primitives.ScrollBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="61de6-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="61de6-138">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="61de6-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="61de6-139">完全なサンプルについては、[Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61de6-139">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61de6-140">参照</span><span class="sxs-lookup"><span data-stu-id="61de6-140">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="61de6-141">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="61de6-141">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="61de6-142">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="61de6-142">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="61de6-143">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="61de6-143">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="61de6-144">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="61de6-144">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
