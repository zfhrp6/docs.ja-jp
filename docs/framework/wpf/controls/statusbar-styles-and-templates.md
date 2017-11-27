---
title: "StatusBar のスタイルとテンプレート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], StatusBar
- styles [WPF], StatusBar
- templates [WPF], StatusBar
- states [WPF], StatusBar
- parts [WPF], StatusBar
- StatusBar [WPF], styles and templates
ms.assetid: 9f5e1c25-81eb-4756-a0ac-d9e1fbe33ee2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 570edc023467fb6e95cdcba23b75ac53397797c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="622ee-102">StatusBar のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="622ee-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="622ee-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.Primitives.StatusBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="622ee-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="622ee-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="622ee-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="622ee-105">詳細については、「[Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="622ee-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="622ee-106">ステータス バーのパーツ</span><span class="sxs-lookup"><span data-stu-id="622ee-106">StatusBar Parts</span></span>  
 <span data-ttu-id="622ee-107"><xref:System.Windows.Controls.Primitives.StatusBar>コントロールには、その名前付きの部分はありません。</span><span class="sxs-lookup"><span data-stu-id="622ee-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="622ee-108">ステータス バーの状態</span><span class="sxs-lookup"><span data-stu-id="622ee-108">StatusBar States</span></span>  
 <span data-ttu-id="622ee-109">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.Primitives.StatusBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="622ee-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="622ee-110">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="622ee-110">VisualState Name</span></span>|<span data-ttu-id="622ee-111">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="622ee-111">VisualStateGroup Name</span></span>|<span data-ttu-id="622ee-112">説明</span><span class="sxs-lookup"><span data-stu-id="622ee-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="622ee-113">有効</span><span class="sxs-lookup"><span data-stu-id="622ee-113">Valid</span></span>|<span data-ttu-id="622ee-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="622ee-114">ValidationStates</span></span>|<span data-ttu-id="622ee-115">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="622ee-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="622ee-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="622ee-116">InvalidFocused</span></span>|<span data-ttu-id="622ee-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="622ee-117">ValidationStates</span></span>|<span data-ttu-id="622ee-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="622ee-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="622ee-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="622ee-119">InvalidUnfocused</span></span>|<span data-ttu-id="622ee-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="622ee-120">ValidationStates</span></span>|<span data-ttu-id="622ee-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="622ee-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="622ee-122">StatusBarItem 部分</span><span class="sxs-lookup"><span data-stu-id="622ee-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="622ee-123"><xref:System.Windows.Controls.Primitives.StatusBarItem>コントロールには、その名前付きの部分はありません。</span><span class="sxs-lookup"><span data-stu-id="622ee-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="622ee-124">ステータス バーの状態</span><span class="sxs-lookup"><span data-stu-id="622ee-124">StatusBar States</span></span>  
 <span data-ttu-id="622ee-125">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.Primitives.StatusBarItem>コントロール。</span><span class="sxs-lookup"><span data-stu-id="622ee-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="622ee-126">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="622ee-126">VisualState Name</span></span>|<span data-ttu-id="622ee-127">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="622ee-127">VisualStateGroup Name</span></span>|<span data-ttu-id="622ee-128">説明</span><span class="sxs-lookup"><span data-stu-id="622ee-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="622ee-129">有効</span><span class="sxs-lookup"><span data-stu-id="622ee-129">Valid</span></span>|<span data-ttu-id="622ee-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="622ee-130">ValidationStates</span></span>|<span data-ttu-id="622ee-131">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="622ee-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="622ee-132">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="622ee-132">InvalidFocused</span></span>|<span data-ttu-id="622ee-133">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="622ee-133">ValidationStates</span></span>|<span data-ttu-id="622ee-134"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="622ee-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="622ee-135">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="622ee-135">InvalidUnfocused</span></span>|<span data-ttu-id="622ee-136">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="622ee-136">ValidationStates</span></span>|<span data-ttu-id="622ee-137"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="622ee-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="622ee-138">StatusBar ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="622ee-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="622ee-139">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Primitives.StatusBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="622ee-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="622ee-140"><xref:System.Windows.Controls.ControlTemplate>次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="622ee-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="622ee-141">完全なサンプルについては、[Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="622ee-141">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="622ee-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="622ee-142">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="622ee-143">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="622ee-143">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="622ee-144">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="622ee-144">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="622ee-145">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="622ee-145">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="622ee-146">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="622ee-146">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
