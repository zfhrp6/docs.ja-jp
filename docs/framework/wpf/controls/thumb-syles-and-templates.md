---
title: "つまみのスタイルとテンプレート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], Thumb
- styles [WPF], Thumb
- templates [WPF], Thumb
- Thumb [WPF], styles and templates
- ControlTemplate [WPF], Thumb
- parts [WPF], Thumb
ms.assetid: 86a49235-62d9-414e-923e-53126e3f930a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 780ddc07c79aab111c17f9e7e551cfde85c68f3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="thumb-syles-and-templates"></a><span data-ttu-id="7c102-102">つまみのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="7c102-102">Thumb Syles and Templates</span></span>
<span data-ttu-id="7c102-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.Primitives.Thumb>コントロール。</span><span class="sxs-lookup"><span data-stu-id="7c102-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="7c102-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="7c102-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="7c102-105">詳細については、「[Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7c102-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="thumb-parts"></a><span data-ttu-id="7c102-106">つまみのパーツ</span><span class="sxs-lookup"><span data-stu-id="7c102-106">Thumb Parts</span></span>  
 <span data-ttu-id="7c102-107"><xref:System.Windows.Controls.Primitives.Thumb>コントロールには、その名前付きの部分はありません。</span><span class="sxs-lookup"><span data-stu-id="7c102-107">The <xref:System.Windows.Controls.Primitives.Thumb> control does not have any named parts.</span></span>  
  
## <a name="thumb-states"></a><span data-ttu-id="7c102-108">つまみの状態</span><span class="sxs-lookup"><span data-stu-id="7c102-108">Thumb States</span></span>  
 <span data-ttu-id="7c102-109">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.Primitives.Thumb>コントロール。</span><span class="sxs-lookup"><span data-stu-id="7c102-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
|<span data-ttu-id="7c102-110">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="7c102-110">VisualState Name</span></span>|<span data-ttu-id="7c102-111">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="7c102-111">VisualStateGroup Name</span></span>|<span data-ttu-id="7c102-112">説明</span><span class="sxs-lookup"><span data-stu-id="7c102-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="7c102-113">標準</span><span class="sxs-lookup"><span data-stu-id="7c102-113">Normal</span></span>|<span data-ttu-id="7c102-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7c102-114">CommonStates</span></span>|<span data-ttu-id="7c102-115">既定の状態です。</span><span class="sxs-lookup"><span data-stu-id="7c102-115">The default state.</span></span>|  
|<span data-ttu-id="7c102-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="7c102-116">MouseOver</span></span>|<span data-ttu-id="7c102-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7c102-117">CommonStates</span></span>|<span data-ttu-id="7c102-118">マウス ポインターがコントロール上に配置されています。</span><span class="sxs-lookup"><span data-stu-id="7c102-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="7c102-119">押されている</span><span class="sxs-lookup"><span data-stu-id="7c102-119">Pressed</span></span>|<span data-ttu-id="7c102-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7c102-120">CommonStates</span></span>|<span data-ttu-id="7c102-121">コントロールが押されています。</span><span class="sxs-lookup"><span data-stu-id="7c102-121">The control is pressed.</span></span>|  
|<span data-ttu-id="7c102-122">無効</span><span class="sxs-lookup"><span data-stu-id="7c102-122">Disabled</span></span>|<span data-ttu-id="7c102-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="7c102-123">CommonStates</span></span>|<span data-ttu-id="7c102-124">コントロールが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="7c102-124">The control is disabled.</span></span>|  
|<span data-ttu-id="7c102-125">フォーカスされている</span><span class="sxs-lookup"><span data-stu-id="7c102-125">Focused</span></span>|<span data-ttu-id="7c102-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="7c102-126">FocusStates</span></span>|<span data-ttu-id="7c102-127">コントロールにフォーカスがあります。</span><span class="sxs-lookup"><span data-stu-id="7c102-127">The control has focus.</span></span>|  
|<span data-ttu-id="7c102-128">フォーカスされていない</span><span class="sxs-lookup"><span data-stu-id="7c102-128">Unfocused</span></span>|<span data-ttu-id="7c102-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="7c102-129">FocusStates</span></span>|<span data-ttu-id="7c102-130">コントロールにフォーカスがありません。</span><span class="sxs-lookup"><span data-stu-id="7c102-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="7c102-131">有効</span><span class="sxs-lookup"><span data-stu-id="7c102-131">Valid</span></span>|<span data-ttu-id="7c102-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7c102-132">ValidationStates</span></span>|<span data-ttu-id="7c102-133">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="7c102-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="7c102-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="7c102-134">InvalidFocused</span></span>|<span data-ttu-id="7c102-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7c102-135">ValidationStates</span></span>|<span data-ttu-id="7c102-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="7c102-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="7c102-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="7c102-137">InvalidUnfocused</span></span>|<span data-ttu-id="7c102-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7c102-138">ValidationStates</span></span>|<span data-ttu-id="7c102-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="7c102-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="thumb-controltemplate-example"></a><span data-ttu-id="7c102-140">Thumb ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="7c102-140">Thumb ControlTemplate Example</span></span>  
 <span data-ttu-id="7c102-141">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Primitives.Thumb>コントロール。</span><span class="sxs-lookup"><span data-stu-id="7c102-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]  
  
 <span data-ttu-id="7c102-142">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="7c102-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="7c102-143">完全なサンプルについては、[Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7c102-143">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c102-144">参照</span><span class="sxs-lookup"><span data-stu-id="7c102-144">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="7c102-145">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="7c102-145">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="7c102-146">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="7c102-146">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="7c102-147">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="7c102-147">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="7c102-148">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="7c102-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
