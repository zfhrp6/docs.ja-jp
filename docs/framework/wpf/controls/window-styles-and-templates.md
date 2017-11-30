---
title: "ウィンドウのスタイルとテンプレート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], Window
- templates [WPF], Window
- styles [WPF], Window
- ControlTemplate [WPF], Window
- Window [WPF], styles and templates
- states [WPF], Window
ms.assetid: 2dfdf025-347b-4342-bf28-95206c273f35
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0415bfae8e1065759efaac1a779655444451fa24
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="window-styles-and-templates"></a><span data-ttu-id="23b85-102">ウィンドウのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="23b85-102">Window Styles and Templates</span></span>
<span data-ttu-id="23b85-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Window>コントロール。</span><span class="sxs-lookup"><span data-stu-id="23b85-103">This topic describes the styles and templates for the <xref:System.Windows.Window> control.</span></span> <span data-ttu-id="23b85-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="23b85-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="23b85-105">詳細については、「[Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23b85-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="window-parts"></a><span data-ttu-id="23b85-106">ウィンドウの一部</span><span class="sxs-lookup"><span data-stu-id="23b85-106">Window Parts</span></span>  
 <span data-ttu-id="23b85-107"><xref:System.Windows.Window>コントロールには、その名前付きの部分はありません。</span><span class="sxs-lookup"><span data-stu-id="23b85-107">The <xref:System.Windows.Window> control does not have any named parts.</span></span>  
  
## <a name="window-states"></a><span data-ttu-id="23b85-108">ウィンドウの状態</span><span class="sxs-lookup"><span data-stu-id="23b85-108">Window States</span></span>  
 <span data-ttu-id="23b85-109">次の表に、用ビジュアル状態、<xref:System.Windows.Window>コントロール。</span><span class="sxs-lookup"><span data-stu-id="23b85-109">The following table lists the visual states for the <xref:System.Windows.Window> control.</span></span>  
  
|<span data-ttu-id="23b85-110">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="23b85-110">VisualState Name</span></span>|<span data-ttu-id="23b85-111">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="23b85-111">VisualStateGroup Name</span></span>|<span data-ttu-id="23b85-112">説明</span><span class="sxs-lookup"><span data-stu-id="23b85-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="23b85-113">有効</span><span class="sxs-lookup"><span data-stu-id="23b85-113">Valid</span></span>|<span data-ttu-id="23b85-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="23b85-114">ValidationStates</span></span>|<span data-ttu-id="23b85-115">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="23b85-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="23b85-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="23b85-116">InvalidFocused</span></span>|<span data-ttu-id="23b85-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="23b85-117">ValidationStates</span></span>|<span data-ttu-id="23b85-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="23b85-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="23b85-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="23b85-119">InvalidUnfocused</span></span>|<span data-ttu-id="23b85-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="23b85-120">ValidationStates</span></span>|<span data-ttu-id="23b85-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="23b85-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="window-controltemplate-example"></a><span data-ttu-id="23b85-122">ウィンドウ ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="23b85-122">Window ControlTemplate Example</span></span>  
 <span data-ttu-id="23b85-123">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Window>コントロール。</span><span class="sxs-lookup"><span data-stu-id="23b85-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Window> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Window](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/window.xaml#window)]  
  
 <span data-ttu-id="23b85-124"><xref:System.Windows.Controls.ControlTemplate>次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="23b85-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="23b85-125">完全なサンプルについては、[Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23b85-125">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23b85-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="23b85-126">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="23b85-127">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="23b85-127">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="23b85-128">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="23b85-128">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="23b85-129">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="23b85-129">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="23b85-130">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="23b85-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
