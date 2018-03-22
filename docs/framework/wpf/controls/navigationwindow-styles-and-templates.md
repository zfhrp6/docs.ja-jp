---
title: NavigationWindow のスタイルとテンプレート
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- states [WPF], NavigationWindow
- NavigationWindow [WPF], styles and templates
- ControlTemplate [WPF], NavigationWindow
- parts [WPF], NavigationWindow
- styles [WPF], NavigationWindow
- templates [WPF], NavigationWindow
ms.assetid: 3656055e-3222-43c8-b868-fd0c90cc31a3
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b638d43fb59506572e2ccddd9da7188639bff279
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="navigationwindow-styles-and-templates"></a><span data-ttu-id="714e0-102">NavigationWindow のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="714e0-102">NavigationWindow Styles and Templates</span></span>
<span data-ttu-id="714e0-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Navigation.NavigationWindow>コントロール。</span><span class="sxs-lookup"><span data-stu-id="714e0-103">This topic describes the styles and templates for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span> <span data-ttu-id="714e0-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="714e0-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="714e0-105">詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="714e0-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="navigationwindow-parts"></a><span data-ttu-id="714e0-106">NavigationWindow 部分</span><span class="sxs-lookup"><span data-stu-id="714e0-106">NavigationWindow Parts</span></span>  
 <span data-ttu-id="714e0-107">次の表に、名前付きのパーツの<xref:System.Windows.Navigation.NavigationWindow>コントロール。</span><span class="sxs-lookup"><span data-stu-id="714e0-107">The following table lists the named parts for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="714e0-108">パーツ</span><span class="sxs-lookup"><span data-stu-id="714e0-108">Part</span></span>|<span data-ttu-id="714e0-109">型</span><span class="sxs-lookup"><span data-stu-id="714e0-109">Type</span></span>|<span data-ttu-id="714e0-110">説明</span><span class="sxs-lookup"><span data-stu-id="714e0-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="714e0-111">PART_NavWinCP</span><span class="sxs-lookup"><span data-stu-id="714e0-111">PART_NavWinCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="714e0-112">コンテンツの領域。</span><span class="sxs-lookup"><span data-stu-id="714e0-112">The area for the content.</span></span>|  
  
## <a name="navigationwindow-states"></a><span data-ttu-id="714e0-113">NavigationWindow 状態</span><span class="sxs-lookup"><span data-stu-id="714e0-113">NavigationWindow States</span></span>  
 <span data-ttu-id="714e0-114">次の表に、用ビジュアル状態、<xref:System.Windows.Navigation.NavigationWindow>コントロール。</span><span class="sxs-lookup"><span data-stu-id="714e0-114">The following table lists the visual states for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="714e0-115">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="714e0-115">VisualState Name</span></span>|<span data-ttu-id="714e0-116">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="714e0-116">VisualStateGroup Name</span></span>|<span data-ttu-id="714e0-117">説明</span><span class="sxs-lookup"><span data-stu-id="714e0-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="714e0-118">有効</span><span class="sxs-lookup"><span data-stu-id="714e0-118">Valid</span></span>|<span data-ttu-id="714e0-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="714e0-119">ValidationStates</span></span>|<span data-ttu-id="714e0-120">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="714e0-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="714e0-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="714e0-121">InvalidFocused</span></span>|<span data-ttu-id="714e0-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="714e0-122">ValidationStates</span></span>|<span data-ttu-id="714e0-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="714e0-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="714e0-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="714e0-124">InvalidUnfocused</span></span>|<span data-ttu-id="714e0-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="714e0-125">ValidationStates</span></span>|<span data-ttu-id="714e0-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="714e0-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="navigationwindow-controltemplate-example"></a><span data-ttu-id="714e0-127">NavigationWindow ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="714e0-127">NavigationWindow ControlTemplate Example</span></span>  
 <span data-ttu-id="714e0-128">この例には、すべての要素で定義されているが含まれますが、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Navigation.NavigationWindow>既定では、特定の値見なす必要がありますの例とします。</span><span class="sxs-lookup"><span data-stu-id="714e0-128">Although this example contains all of the elements that are defined in the <xref:System.Windows.Controls.ControlTemplate> of a <xref:System.Windows.Navigation.NavigationWindow> by default, the specific values should be thought of as examples.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#NavigationWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/navigationwindow.xaml#navigationwindow)]  
  
 <span data-ttu-id="714e0-129">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="714e0-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="714e0-130">完全なサンプルについては、[Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="714e0-130">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="714e0-131">参照</span><span class="sxs-lookup"><span data-stu-id="714e0-131">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="714e0-132">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="714e0-132">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="714e0-133">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="714e0-133">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="714e0-134">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="714e0-134">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="714e0-135">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="714e0-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
