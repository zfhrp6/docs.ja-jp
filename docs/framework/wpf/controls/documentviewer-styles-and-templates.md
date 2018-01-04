---
title: "DocumentViewer のスタイルとテンプレート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [WPF], DocumentViewer
- DocumentViewer [WPF], styles and templates
- states [WPF], DocumentViewer
- ControlTemplate [WPF], DocumentViewer
- parts [WPF], DocumentViewer
- styles [WPF], DocumentViewer
ms.assetid: 6bd4ff8f-ea6a-4084-ac58-e7a67446ce1c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 33631b0a63b69f848cb3f09b4dcb617fb328b06c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="documentviewer-styles-and-templates"></a><span data-ttu-id="8e385-102">DocumentViewer のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="8e385-102">DocumentViewer Styles and Templates</span></span>
<span data-ttu-id="8e385-103">このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.DocumentViewer>コントロール。</span><span class="sxs-lookup"><span data-stu-id="8e385-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span> <span data-ttu-id="8e385-104">既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。</span><span class="sxs-lookup"><span data-stu-id="8e385-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="8e385-105">詳細については、「[Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e385-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="documentviewer-parts"></a><span data-ttu-id="8e385-106">DocumentViewer のパーツ</span><span class="sxs-lookup"><span data-stu-id="8e385-106">DocumentViewer Parts</span></span>  
 <span data-ttu-id="8e385-107">次の表に、名前付きのパーツの<xref:System.Windows.Controls.DocumentViewer>コントロール。</span><span class="sxs-lookup"><span data-stu-id="8e385-107">The following table lists the named parts for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="8e385-108">パーツ</span><span class="sxs-lookup"><span data-stu-id="8e385-108">Part</span></span>|<span data-ttu-id="8e385-109">型</span><span class="sxs-lookup"><span data-stu-id="8e385-109">Type</span></span>|<span data-ttu-id="8e385-110">説明</span><span class="sxs-lookup"><span data-stu-id="8e385-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="8e385-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="8e385-111">PART_ContentHost</span></span>|<xref:System.Windows.Controls.ScrollViewer>|<span data-ttu-id="8e385-112">コンテンツと領域をスクロールします。</span><span class="sxs-lookup"><span data-stu-id="8e385-112">The content and scrolling area.</span></span>|  
|<span data-ttu-id="8e385-113">PART_FindToolBarHost</span><span class="sxs-lookup"><span data-stu-id="8e385-113">PART_FindToolBarHost</span></span>|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="8e385-114">既定では下部にある検索ボックス。</span><span class="sxs-lookup"><span data-stu-id="8e385-114">The search box, at the bottom by default.</span></span>|  
  
## <a name="documentviewer-states"></a><span data-ttu-id="8e385-115">DocumentViewer の状態</span><span class="sxs-lookup"><span data-stu-id="8e385-115">DocumentViewer States</span></span>  
 <span data-ttu-id="8e385-116">次の表に、用ビジュアル状態、<xref:System.Windows.Controls.DocumentViewer>コントロール。</span><span class="sxs-lookup"><span data-stu-id="8e385-116">The following table lists the visual states for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="8e385-117">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="8e385-117">VisualState Name</span></span>|<span data-ttu-id="8e385-118">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="8e385-118">VisualStateGroup Name</span></span>|<span data-ttu-id="8e385-119">説明</span><span class="sxs-lookup"><span data-stu-id="8e385-119">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="8e385-120">有効</span><span class="sxs-lookup"><span data-stu-id="8e385-120">Valid</span></span>|<span data-ttu-id="8e385-121">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8e385-121">ValidationStates</span></span>|<span data-ttu-id="8e385-122">コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="8e385-122">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="8e385-123">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="8e385-123">InvalidFocused</span></span>|<span data-ttu-id="8e385-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8e385-124">ValidationStates</span></span>|<span data-ttu-id="8e385-125"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。</span><span class="sxs-lookup"><span data-stu-id="8e385-125">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="8e385-126">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="8e385-126">InvalidUnfocused</span></span>|<span data-ttu-id="8e385-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8e385-127">ValidationStates</span></span>|<span data-ttu-id="8e385-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。</span><span class="sxs-lookup"><span data-stu-id="8e385-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="documentviewer-controltemplate-example"></a><span data-ttu-id="8e385-129">DocumentViewer ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="8e385-129">DocumentViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="8e385-130">次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.DocumentViewer>コントロール。</span><span class="sxs-lookup"><span data-stu-id="8e385-130">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#DocumentViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/documentviewer.xaml#documentviewer)]  
  
 <span data-ttu-id="8e385-131">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="8e385-131">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="8e385-132">完全なサンプルについては、[Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e385-132">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e385-133">参照</span><span class="sxs-lookup"><span data-stu-id="8e385-133">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="8e385-134">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="8e385-134">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="8e385-135">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="8e385-135">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="8e385-136">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="8e385-136">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="8e385-137">ControlTemplate の作成による既存のコントロールの外観のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="8e385-137">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
