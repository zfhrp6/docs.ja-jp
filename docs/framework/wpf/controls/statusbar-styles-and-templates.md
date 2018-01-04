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
ms.workload: dotnet
ms.openlocfilehash: 370f8f9bc61ffbdd3b98743d11f61613803e6d98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="3d9dd-102">StatusBar のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="3d9dd-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="3d9dd-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.Primitives.StatusBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="3d9dd-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="3d9dd-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="3d9dd-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="3d9dd-105">詳細については、「[Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d9dd-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="3d9dd-106">ステータス バーのパーツ</span><span class="sxs-lookup"><span data-stu-id="3d9dd-106">StatusBar Parts</span></span>  
 <span data-ttu-id="3d9dd-107"><xref:System.Windows.Controls.Primitives.StatusBar>コントロールには、その名前付きの部分はありません。</span><span class="sxs-lookup"><span data-stu-id="3d9dd-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="3d9dd-108">ステータス バーの状態</span><span class="sxs-lookup"><span data-stu-id="3d9dd-108">StatusBar States</span></span>  
 <span data-ttu-id="3d9dd-109">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.Primitives.StatusBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="3d9dd-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="3d9dd-110">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="3d9dd-110">VisualState Name</span></span>|<span data-ttu-id="3d9dd-111">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="3d9dd-111">VisualStateGroup Name</span></span>|<span data-ttu-id="3d9dd-112">説明</span><span class="sxs-lookup"><span data-stu-id="3d9dd-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="3d9dd-113">有効</span><span class="sxs-lookup"><span data-stu-id="3d9dd-113">Valid</span></span>|<span data-ttu-id="3d9dd-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3d9dd-114">ValidationStates</span></span>|<span data-ttu-id="3d9dd-115">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="3d9dd-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="3d9dd-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="3d9dd-116">InvalidFocused</span></span>|<span data-ttu-id="3d9dd-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3d9dd-117">ValidationStates</span></span>|<span data-ttu-id="3d9dd-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="3d9dd-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="3d9dd-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="3d9dd-119">InvalidUnfocused</span></span>|<span data-ttu-id="3d9dd-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3d9dd-120">ValidationStates</span></span>|<span data-ttu-id="3d9dd-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="3d9dd-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="3d9dd-122">StatusBarItem 部分</span><span class="sxs-lookup"><span data-stu-id="3d9dd-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="3d9dd-123"><xref:System.Windows.Controls.Primitives.StatusBarItem>コントロールには、その名前付きの部分はありません。</span><span class="sxs-lookup"><span data-stu-id="3d9dd-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="3d9dd-124">ステータス バーの状態</span><span class="sxs-lookup"><span data-stu-id="3d9dd-124">StatusBar States</span></span>  
 <span data-ttu-id="3d9dd-125">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.Primitives.StatusBarItem>コントロール。</span><span class="sxs-lookup"><span data-stu-id="3d9dd-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="3d9dd-126">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="3d9dd-126">VisualState Name</span></span>|<span data-ttu-id="3d9dd-127">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="3d9dd-127">VisualStateGroup Name</span></span>|<span data-ttu-id="3d9dd-128">説明</span><span class="sxs-lookup"><span data-stu-id="3d9dd-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="3d9dd-129">有効</span><span class="sxs-lookup"><span data-stu-id="3d9dd-129">Valid</span></span>|<span data-ttu-id="3d9dd-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3d9dd-130">ValidationStates</span></span>|<span data-ttu-id="3d9dd-131">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="3d9dd-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="3d9dd-132">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="3d9dd-132">InvalidFocused</span></span>|<span data-ttu-id="3d9dd-133">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3d9dd-133">ValidationStates</span></span>|<span data-ttu-id="3d9dd-134"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="3d9dd-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="3d9dd-135">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="3d9dd-135">InvalidUnfocused</span></span>|<span data-ttu-id="3d9dd-136">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3d9dd-136">ValidationStates</span></span>|<span data-ttu-id="3d9dd-137"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="3d9dd-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="3d9dd-138">StatusBar ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="3d9dd-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="3d9dd-139">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Primitives.StatusBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="3d9dd-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="3d9dd-140"><xref:System.Windows.Controls.ControlTemplate>次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="3d9dd-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="3d9dd-141">完全なサンプルについては、[Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d9dd-141">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d9dd-142">参照</span><span class="sxs-lookup"><span data-stu-id="3d9dd-142">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="3d9dd-143">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="3d9dd-143">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="3d9dd-144">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="3d9dd-144">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="3d9dd-145">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="3d9dd-145">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="3d9dd-146">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="3d9dd-146">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
