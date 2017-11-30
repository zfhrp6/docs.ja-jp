---
title: "ToolTip のスタイルとテンプレート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], ToolTip
- styles [WPF], ToolTip
- states [WPF], ToolTip
- ToolTip [WPF], styles and templates
- ControlTemplate [WPF], ToolTip
- templates [WPF], ToolTip
ms.assetid: 405fe385-4de9-49ee-a448-d8f4d1f740dd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec946e7982983519a317ee1936e8584eef63479c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="tooltip-styles-and-templates"></a><span data-ttu-id="76457-102">ToolTip のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="76457-102">ToolTip Styles and Templates</span></span>
<span data-ttu-id="76457-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.ToolTip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="76457-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolTip> control.</span></span> <span data-ttu-id="76457-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="76457-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="76457-105">詳細については、「[Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76457-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="tooltip-parts"></a><span data-ttu-id="76457-106">ツールヒントのパーツ</span><span class="sxs-lookup"><span data-stu-id="76457-106">ToolTip Parts</span></span>  
 <span data-ttu-id="76457-107"><xref:System.Windows.Controls.ToolTip>コントロールには、その名前付きの部分はありません。</span><span class="sxs-lookup"><span data-stu-id="76457-107">The <xref:System.Windows.Controls.ToolTip> control does not have any named parts.</span></span>  
  
## <a name="tooltip-states"></a><span data-ttu-id="76457-108">ツール ヒントの状態</span><span class="sxs-lookup"><span data-stu-id="76457-108">ToolTip States</span></span>  
 <span data-ttu-id="76457-109">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.ToolTip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="76457-109">The following table lists the visual states for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
|<span data-ttu-id="76457-110">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="76457-110">VisualState Name</span></span>|<span data-ttu-id="76457-111">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="76457-111">VisualStateGroup Name</span></span>|<span data-ttu-id="76457-112">説明</span><span class="sxs-lookup"><span data-stu-id="76457-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="76457-113">Closed</span><span class="sxs-lookup"><span data-stu-id="76457-113">Closed</span></span>|<span data-ttu-id="76457-114">OpenStates</span><span class="sxs-lookup"><span data-stu-id="76457-114">OpenStates</span></span>|<span data-ttu-id="76457-115">既定の状態です。</span><span class="sxs-lookup"><span data-stu-id="76457-115">The default state.</span></span>|  
|<span data-ttu-id="76457-116">開く</span><span class="sxs-lookup"><span data-stu-id="76457-116">Open</span></span>|<span data-ttu-id="76457-117">OpenStates</span><span class="sxs-lookup"><span data-stu-id="76457-117">OpenStates</span></span>|<span data-ttu-id="76457-118"><xref:System.Windows.Controls.ToolTip>が表示されます。</span><span class="sxs-lookup"><span data-stu-id="76457-118">The <xref:System.Windows.Controls.ToolTip> is visible.</span></span>|  
|<span data-ttu-id="76457-119">有効</span><span class="sxs-lookup"><span data-stu-id="76457-119">Valid</span></span>|<span data-ttu-id="76457-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="76457-120">ValidationStates</span></span>|<span data-ttu-id="76457-121">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="76457-121">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="76457-122">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="76457-122">InvalidFocused</span></span>|<span data-ttu-id="76457-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="76457-123">ValidationStates</span></span>|<span data-ttu-id="76457-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="76457-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="76457-125">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="76457-125">InvalidUnfocused</span></span>|<span data-ttu-id="76457-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="76457-126">ValidationStates</span></span>|<span data-ttu-id="76457-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="76457-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tooltip-controltemplate-example"></a><span data-ttu-id="76457-128">ツールヒント ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="76457-128">ToolTip ControlTemplate Example</span></span>  
 <span data-ttu-id="76457-129">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.ToolTip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="76457-129">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tooltip.xaml#tooltip)]  
  
 <span data-ttu-id="76457-130">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="76457-130">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="76457-131">完全なサンプルについては、[Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76457-131">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76457-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="76457-132">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="76457-133">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="76457-133">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="76457-134">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="76457-134">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="76457-135">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="76457-135">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="76457-136">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="76457-136">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
