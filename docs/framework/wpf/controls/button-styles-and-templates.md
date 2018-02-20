---
title: "ボタンのスタイルとテンプレート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], Button
- parts [WPF], Button
- styles [WPF], Button
- Button [WPF], styles and templates
- templates [WPF], Button
- ControlTemplate [WPF], Button
ms.assetid: e223c759-f8c4-4717-acfb-b1e40bdf5f3b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d783b3141463ca2c74ddd649848ea49e154415b6
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2018
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="6b8c4-102">ボタンのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="6b8c4-102">Button Styles and Templates</span></span>
<span data-ttu-id="6b8c4-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.Button>コントロール。</span><span class="sxs-lookup"><span data-stu-id="6b8c4-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="6b8c4-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="6b8c4-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="6b8c4-105">詳細については、「[Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b8c4-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="6b8c4-106">ボタンのパーツ</span><span class="sxs-lookup"><span data-stu-id="6b8c4-106">Button Parts</span></span>  
 <span data-ttu-id="6b8c4-107"><xref:System.Windows.Controls.Button>コントロールには、その名前付きの部分はありません。</span><span class="sxs-lookup"><span data-stu-id="6b8c4-107">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="6b8c4-108">ボタンの状態</span><span class="sxs-lookup"><span data-stu-id="6b8c4-108">Button States</span></span>  
 <span data-ttu-id="6b8c4-109">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.Button>コントロール。</span><span class="sxs-lookup"><span data-stu-id="6b8c4-109">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="6b8c4-110">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="6b8c4-110">VisualState Name</span></span>|<span data-ttu-id="6b8c4-111">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="6b8c4-111">VisualStateGroup Name</span></span>|<span data-ttu-id="6b8c4-112">説明</span><span class="sxs-lookup"><span data-stu-id="6b8c4-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6b8c4-113">標準</span><span class="sxs-lookup"><span data-stu-id="6b8c4-113">Normal</span></span>|<span data-ttu-id="6b8c4-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="6b8c4-114">CommonStates</span></span>|<span data-ttu-id="6b8c4-115">既定の状態です。</span><span class="sxs-lookup"><span data-stu-id="6b8c4-115">The default state.</span></span>|  
|<span data-ttu-id="6b8c4-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="6b8c4-116">MouseOver</span></span>|<span data-ttu-id="6b8c4-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="6b8c4-117">CommonStates</span></span>|<span data-ttu-id="6b8c4-118">マウス ポインターがコントロール上に配置されています。</span><span class="sxs-lookup"><span data-stu-id="6b8c4-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="6b8c4-119">押されている</span><span class="sxs-lookup"><span data-stu-id="6b8c4-119">Pressed</span></span>|<span data-ttu-id="6b8c4-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="6b8c4-120">CommonStates</span></span>|<span data-ttu-id="6b8c4-121">コントロールが押されています。</span><span class="sxs-lookup"><span data-stu-id="6b8c4-121">The control is pressed.</span></span>|  
|<span data-ttu-id="6b8c4-122">無効</span><span class="sxs-lookup"><span data-stu-id="6b8c4-122">Disabled</span></span>|<span data-ttu-id="6b8c4-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="6b8c4-123">CommonStates</span></span>|<span data-ttu-id="6b8c4-124">コントロールが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="6b8c4-124">The control is disabled.</span></span>|  
|<span data-ttu-id="6b8c4-125">フォーカスされている</span><span class="sxs-lookup"><span data-stu-id="6b8c4-125">Focused</span></span>|<span data-ttu-id="6b8c4-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="6b8c4-126">FocusStates</span></span>|<span data-ttu-id="6b8c4-127">コントロールにフォーカスがあります。</span><span class="sxs-lookup"><span data-stu-id="6b8c4-127">The control has focus.</span></span>|  
|<span data-ttu-id="6b8c4-128">フォーカスされていない</span><span class="sxs-lookup"><span data-stu-id="6b8c4-128">Unfocused</span></span>|<span data-ttu-id="6b8c4-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="6b8c4-129">FocusStates</span></span>|<span data-ttu-id="6b8c4-130">コントロールにフォーカスがありません。</span><span class="sxs-lookup"><span data-stu-id="6b8c4-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="6b8c4-131">有効</span><span class="sxs-lookup"><span data-stu-id="6b8c4-131">Valid</span></span>|<span data-ttu-id="6b8c4-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6b8c4-132">ValidationStates</span></span>|<span data-ttu-id="6b8c4-133">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="6b8c4-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="6b8c4-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="6b8c4-134">InvalidFocused</span></span>|<span data-ttu-id="6b8c4-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6b8c4-135">ValidationStates</span></span>|<span data-ttu-id="6b8c4-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`コントロールにフォーカスがあるとします。</span><span class="sxs-lookup"><span data-stu-id="6b8c4-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="6b8c4-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="6b8c4-137">InvalidUnfocused</span></span>|<span data-ttu-id="6b8c4-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6b8c4-138">ValidationStates</span></span>|<span data-ttu-id="6b8c4-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`コントロールにフォーカスがないとします。</span><span class="sxs-lookup"><span data-stu-id="6b8c4-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="6b8c4-140">ボタン ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="6b8c4-140">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="6b8c4-141">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Button>コントロール。</span><span class="sxs-lookup"><span data-stu-id="6b8c4-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="6b8c4-142">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="6b8c4-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="6b8c4-143">完全なサンプルについては、[Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b8c4-143">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b8c4-144">参照</span><span class="sxs-lookup"><span data-stu-id="6b8c4-144">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="6b8c4-145">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="6b8c4-145">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="6b8c4-146">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="6b8c4-146">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="6b8c4-147">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="6b8c4-147">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="6b8c4-148">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="6b8c4-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
