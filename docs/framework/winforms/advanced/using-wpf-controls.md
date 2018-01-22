---
title: "WPF コントロールの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5e616019d53648058d51a3d0df457b1380aaf3b1
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="using-wpf-controls"></a><span data-ttu-id="51300-102">WPF コントロールの使用</span><span class="sxs-lookup"><span data-stu-id="51300-102">Using WPF Controls</span></span>
<span data-ttu-id="51300-103">Windows フォーム ベースのアプリケーションでは、Windows Presentation Foundation (WPF) コントロールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="51300-103">You can use Windows Presentation Foundation (WPF) controls in your Windows Forms-based applications.</span></span> <span data-ttu-id="51300-104">これらは、次の 2 つの異なるビュー テクノロジが、相互運用スムーズに動作します。</span><span class="sxs-lookup"><span data-stu-id="51300-104">Although these are two different view technologies, they interoperate smoothly.</span></span>  
  
 <span data-ttu-id="51300-105">Windows フォーム デザイナーでは、Windows Presentation Foundation コントロールをホストするためのビジュアル デ ザイン環境を提供します。</span><span class="sxs-lookup"><span data-stu-id="51300-105">The Windows Forms Designer provides a visual design environment for hosting Windows Presentation Foundation controls.</span></span> <span data-ttu-id="51300-106">WPF コントロールがという名前を特別な Windows フォーム コントロールでホストされている<xref:System.Windows.Forms.Integration.ElementHost>です。</span><span class="sxs-lookup"><span data-stu-id="51300-106">A WPF control is hosted by a special Windows Forms control that is named <xref:System.Windows.Forms.Integration.ElementHost>.</span></span> <span data-ttu-id="51300-107">このコントロールは、フォームのレイアウトに参加して、キーボードとマウスのメッセージを受信する WPF コントロールを使用します。</span><span class="sxs-lookup"><span data-stu-id="51300-107">This control enables the WPF control to participate in the form's layout and to receive keyboard and mouse messages.</span></span> <span data-ttu-id="51300-108">デザイン時に配置することができます、<xref:System.Windows.Forms.Integration.ElementHost>同様の Windows フォーム コントロールを制御します。</span><span class="sxs-lookup"><span data-stu-id="51300-108">At design time, you can arrange the <xref:System.Windows.Forms.Integration.ElementHost> control just as you would any Windows Forms control.</span></span>  
  
 <span data-ttu-id="51300-109">また、WPF ベースのアプリケーションで Windows フォーム コントロールを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="51300-109">You can also use Windows Forms controls in your WPF-based applications.</span></span> <span data-ttu-id="51300-110">詳細については、次を参照してください。 [WPF デザイナー](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)です。</span><span class="sxs-lookup"><span data-stu-id="51300-110">For more information, see [WPF Designer](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="51300-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="51300-111">In This Section</span></span>  
 [<span data-ttu-id="51300-112">方法: デザイン時に ElementHost コントロールをコピーして貼り付ける</span><span class="sxs-lookup"><span data-stu-id="51300-112">How to: Copy and Paste an ElementHost Control at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-copy-and-paste-an-elementhost-control-at-design-time.md)  
 <span data-ttu-id="51300-113">Windows フォーム上の Windows Presentation Foundation コントロールをコピーする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="51300-113">Shows how to copy a Windows Presentation Foundation control on a Windows Form.</span></span>  
  
 [<span data-ttu-id="51300-114">チュートリアル: デザイン時の Windows フォームでの WPF コンテンツの配置</span><span class="sxs-lookup"><span data-stu-id="51300-114">Walkthrough: Arranging WPF Content on Windows Forms at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="51300-115">固定やスナップ線など、Windows フォームのレイアウト機能を使用して、Windows Presentation Foundation コントロールを配置する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="51300-115">Shows how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation controls.</span></span>  
  
 [<span data-ttu-id="51300-116">チュートリアル: デザイン時のホストされている WPF 要素のプロパティの変更</span><span class="sxs-lookup"><span data-stu-id="51300-116">Walkthrough: Changing Properties of a Hosted WPF Element at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time.md)  
 <span data-ttu-id="51300-117">Windows フォーム デザイナー間のワークフローを示しています、 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] WPF コントロールのプロパティを変更するためです。</span><span class="sxs-lookup"><span data-stu-id="51300-117">Shows the workflow between the Windows Forms Designer and the [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] for changing properties on WPF controls.</span></span>  
  
 [<span data-ttu-id="51300-118">チュートリアル: デザイン時の Windows フォームでの新しい WPF コンテンツの作成</span><span class="sxs-lookup"><span data-stu-id="51300-118">Walkthrough: Creating New WPF Content on Windows Forms at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="51300-119">Windows フォーム ベースのアプリケーションで使用される Windows Presentation Foundation コントロールを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="51300-119">Shows how to create a Windows Presentation Foundation control for use in your Windows Forms-based applications.</span></span>  
  
 [<span data-ttu-id="51300-120">チュートリアル: ElementHost コントロールの別の Windows フォームへのコピーと貼り付け</span><span class="sxs-lookup"><span data-stu-id="51300-120">Walkthrough: Copying and Pasting an ElementHost Control into Separate Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)  
 <span data-ttu-id="51300-121">Windows Presentation Foundation コントロールを別の 1 つの Windows フォームにコピーする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="51300-121">Shows how to copy a Windows Presentation Foundation control from one Windows Form to another.</span></span>  
  
 [<span data-ttu-id="51300-122">チュートリアル: デザイン時の Windows フォームでの WPF コンテンツの割り当て</span><span class="sxs-lookup"><span data-stu-id="51300-122">Walkthrough: Assigning WPF Content on Windows Forms at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="51300-123">フォームに表示する Windows Presentation Foundation コントロールの種類を選択する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="51300-123">Shows how to select the Windows Presentation Foundation control types you want to display on your form.</span></span>  
  
 [<span data-ttu-id="51300-124">チュートリアル: WPF コンテンツへのスタイルの適用</span><span class="sxs-lookup"><span data-stu-id="51300-124">Walkthrough: Styling WPF Content</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md)  
 <span data-ttu-id="51300-125">Windows フォーム デザイナー間のワークフローを示しています、 [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] Windows Presentation Foundation コントロールにスタイルを適用するためです。</span><span class="sxs-lookup"><span data-stu-id="51300-125">Shows the workflow between the Windows Forms Designer and the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] for applying styles to Windows Presentation Foundation controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="51300-126">参照</span><span class="sxs-lookup"><span data-stu-id="51300-126">Reference</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <span data-ttu-id="51300-127">Windows フォーム ベースのアプリケーションで Windows Presentation Foundation コントロールのホストに使用できるクラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="51300-127">Describes a class which you can use to host Windows Presentation Foundation controls in your Windows Forms-based applications.</span></span>  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 <span data-ttu-id="51300-128">Windows Presentation Foundation ベースのアプリケーションでホストの Windows フォーム コントロールを使用できるクラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="51300-128">Describes a class which you can use to host Windows Forms controls in your Windows Presentation Foundation-based application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="51300-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="51300-129">Related Sections</span></span>  
 [<span data-ttu-id="51300-130">移行と相互運用性</span><span class="sxs-lookup"><span data-stu-id="51300-130">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 <span data-ttu-id="51300-131">Windows Presentation Foundation と Windows フォームの技術間の相互運用を説明します。</span><span class="sxs-lookup"><span data-stu-id="51300-131">Describes interoperation between the Windows Presentation Foundation and Windows Forms technologies.</span></span>  
  
 [<span data-ttu-id="51300-132">WPF デザイナー</span><span class="sxs-lookup"><span data-stu-id="51300-132">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 <span data-ttu-id="51300-133">Windows Presentation Foundation コントロールをデザインする方法について説明[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="51300-133">Describes how to design Windows Presentation Foundation controls in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>
