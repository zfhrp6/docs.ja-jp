---
title: "ProgressBar のスタイルとテンプレート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], ProgressBar
- ProgressBar [WPF], styles and templates
- styles [WPF], ProgressBar
- ControlTemplate [WPF], ProgressBar
- templates [WPF], ProgressBar
- states [WPF], ProgressBar
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 475607381f16d7b42f26f12809a11d5eaf4e74bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="14da5-102">ProgressBar のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="14da5-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="14da5-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.ProgressBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="14da5-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="14da5-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="14da5-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="14da5-105">詳細については、「[Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14da5-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="14da5-106">ProgressBar のパーツ</span><span class="sxs-lookup"><span data-stu-id="14da5-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="14da5-107">次の表に、名前付きのパーツの<xref:System.Windows.Controls.ProgressBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="14da5-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="14da5-108">パーツ</span><span class="sxs-lookup"><span data-stu-id="14da5-108">Part</span></span>|<span data-ttu-id="14da5-109">型</span><span class="sxs-lookup"><span data-stu-id="14da5-109">Type</span></span>|<span data-ttu-id="14da5-110">説明</span><span class="sxs-lookup"><span data-stu-id="14da5-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="14da5-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="14da5-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="14da5-112">進行状況を示すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="14da5-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="14da5-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="14da5-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="14da5-114">進行状況インジケーターのパスを定義するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="14da5-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="14da5-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="14da5-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="14da5-116">進行状況バーを embellishes オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="14da5-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="14da5-117">ProgressBar の状態</span><span class="sxs-lookup"><span data-stu-id="14da5-117">ProgressBar States</span></span>  
 <span data-ttu-id="14da5-118">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.ProgressBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="14da5-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="14da5-119">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="14da5-119">VisualState Name</span></span>|<span data-ttu-id="14da5-120">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="14da5-120">VisualStateGroup Name</span></span>|<span data-ttu-id="14da5-121">説明</span><span class="sxs-lookup"><span data-stu-id="14da5-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="14da5-122">不定になります</span><span class="sxs-lookup"><span data-stu-id="14da5-122">Determinate</span></span>|<span data-ttu-id="14da5-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="14da5-123">CommonStates</span></span>|<span data-ttu-id="14da5-124"><xref:System.Windows.Controls.ProgressBar>に基づいて進行状況をレポート、<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="14da5-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="14da5-125">不確定です</span><span class="sxs-lookup"><span data-stu-id="14da5-125">Indeterminate</span></span>|<span data-ttu-id="14da5-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="14da5-126">CommonStates</span></span>|<span data-ttu-id="14da5-127"><xref:System.Windows.Controls.ProgressBar>繰り返しのパターンを持つジェネリックの進行状況を報告します。</span><span class="sxs-lookup"><span data-stu-id="14da5-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="14da5-128">有効</span><span class="sxs-lookup"><span data-stu-id="14da5-128">Valid</span></span>|<span data-ttu-id="14da5-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="14da5-129">ValidationStates</span></span>|<span data-ttu-id="14da5-130">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="14da5-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="14da5-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="14da5-131">InvalidFocused</span></span>|<span data-ttu-id="14da5-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="14da5-132">ValidationStates</span></span>|<span data-ttu-id="14da5-133"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="14da5-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="14da5-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="14da5-134">InvalidUnfocused</span></span>|<span data-ttu-id="14da5-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="14da5-135">ValidationStates</span></span>|<span data-ttu-id="14da5-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="14da5-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="14da5-137">ProgressBar ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="14da5-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="14da5-138">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.ProgressBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="14da5-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="14da5-139">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="14da5-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="14da5-140">完全なサンプルについては、[Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14da5-140">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14da5-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="14da5-141">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="14da5-142">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="14da5-142">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="14da5-143">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="14da5-143">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="14da5-144">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="14da5-144">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="14da5-145">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="14da5-145">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
