---
title: "コントロールのカスタム描画およびレンダリング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- user controls [Windows Forms], painting
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 355a5842348aa4395d1841d0343080ddef634456
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="custom-control-painting-and-rendering"></a><span data-ttu-id="bfe88-102">コントロールのカスタム描画およびレンダリング</span><span class="sxs-lookup"><span data-stu-id="bfe88-102">Custom Control Painting and Rendering</span></span>
<span data-ttu-id="bfe88-103">コントロールのカスタム描画は、.NET Framework で簡単に作成する多くの複雑なタスクのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="bfe88-103">Custom painting of controls is one of the many complicated tasks made easy by the .NET Framework.</span></span> <span data-ttu-id="bfe88-104">カスタム コントロールを作成するときに、コントロールの外観に関する多くのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="bfe88-104">When authoring a custom control, you have many options regarding your control's graphical appearance.</span></span> <span data-ttu-id="bfe88-105">継承されるコントロールを作成している場合、 `Control`、グラフィカル表示を表示するために、コントロールを可能にするコードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bfe88-105">If you are authoring a control that inherits from the `Control`, you must provide code that allows your control to render its graphical representation.</span></span> <span data-ttu-id="bfe88-106">継承することで、ユーザー コントロールを作成するかどうかは、 `UserControl`、継承、または Windows フォーム コントロールのいずれかでは、標準のグラフィカル表示をオーバーライドして、独自のグラフィックス コードを提供します。</span><span class="sxs-lookup"><span data-stu-id="bfe88-106">If you are creating a user control by inheriting from the `UserControl`, or are inheriting from one of the Windows Forms controls, you may override the standard graphical representation and provide your own graphics code.</span></span> <span data-ttu-id="bfe88-107">内在コントロールのカスタムの表示を提供するかどうか、`UserControl`オーサリングするは、これは、オプションが制限されますが、コントロールとアプリケーションのグラフィカル表現の広範な許可を許可します。</span><span class="sxs-lookup"><span data-stu-id="bfe88-107">If you want to provide custom rendering for the constituent controls of a `UserControl` you are authoring, your options become more limited, but still allow a wide range of graphical possibilities for your controls and applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bfe88-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="bfe88-108">In This Section</span></span>  
 [<span data-ttu-id="bfe88-109">Windows フォーム コントロールのレンダリング</span><span class="sxs-lookup"><span data-stu-id="bfe88-109">Rendering a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 <span data-ttu-id="bfe88-110">コントロールを表示するロジックをプログラミングする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bfe88-110">Shows how to program the logic that displays a control.</span></span>  
  
 [<span data-ttu-id="bfe88-111">ユーザー描画コントロール</span><span class="sxs-lookup"><span data-stu-id="bfe88-111">User-Drawn Controls</span></span>](../../../../docs/framework/winforms/controls/user-drawn-controls.md)  
 <span data-ttu-id="bfe88-112">コントロールの表示コードをオーバーライドしたりする書き込みに必要な手順の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="bfe88-112">Gives an overview of the steps involved in writing and overriding rendering code for your control.</span></span>  
  
 [<span data-ttu-id="bfe88-113">内在コントロール</span><span class="sxs-lookup"><span data-stu-id="bfe88-113">Constituent Controls</span></span>](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 <span data-ttu-id="bfe88-114">ユーザー コントロールおよびフォームに内在コントロールのカスタム表示コードを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bfe88-114">Describes how to implement custom rendering code for constituent controls in your user controls and forms.</span></span>  
  
 [<span data-ttu-id="bfe88-115">方法: 実行時にコントロールを非表示にする</span><span class="sxs-lookup"><span data-stu-id="bfe88-115">How to: Make Your Control Invisible at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-make-your-control-invisible-at-run-time.md)  
 <span data-ttu-id="bfe88-116">使用する方法を示します、<xref:System.Windows.Forms.Control.Visible%2A>プロパティ コントロールの表示し、非表示にします。</span><span class="sxs-lookup"><span data-stu-id="bfe88-116">Shows how to use the <xref:System.Windows.Forms.Control.Visible%2A> property to hide and show a control.</span></span>  
  
 [<span data-ttu-id="bfe88-117">方法: コントロールに透明な背景を指定する</span><span class="sxs-lookup"><span data-stu-id="bfe88-117">How to: Give Your Control a Transparent Background</span></span>](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 <span data-ttu-id="bfe88-118">使用する方法を示します、<xref:System.Windows.Forms.Control.SetStyle%2A>メソッドを非透過、透明で、または部分的に透明な背景色を作成します。</span><span class="sxs-lookup"><span data-stu-id="bfe88-118">Shows how to use the <xref:System.Windows.Forms.Control.SetStyle%2A> method to create a background color that is opaque, transparent, or partially transparent.</span></span>  
  
 [<span data-ttu-id="bfe88-119">visual スタイルが使用されているコントロールのレンダリング</span><span class="sxs-lookup"><span data-stu-id="bfe88-119">Rendering Controls with Visual Styles</span></span>](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 <span data-ttu-id="bfe88-120">それらをサポートするオペレーティング システムで visual スタイルを使用してコントロールをレンダリングする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bfe88-120">Shows how to render controls using visual styles in operating systems that support them.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="bfe88-121">参照</span><span class="sxs-lookup"><span data-stu-id="bfe88-121">Reference</span></span>  
 <xref:System.Windows.Forms.Control>  
 <span data-ttu-id="bfe88-122">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="bfe88-122">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl>  
 <span data-ttu-id="bfe88-123">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="bfe88-123">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <span data-ttu-id="bfe88-124">このメソッドをについて説明します。</span><span class="sxs-lookup"><span data-stu-id="bfe88-124">Describes this method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bfe88-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="bfe88-125">Related Sections</span></span>  
 [<span data-ttu-id="bfe88-126">方法: 描画する Graphics オブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="bfe88-126">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 <span data-ttu-id="bfe88-127">紹介[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]詳細については、Visual Studio によりとパースペクティブのリンクからグラフィックス機能します。</span><span class="sxs-lookup"><span data-stu-id="bfe88-127">Introduces [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] graphics functionality from a Visual Studio perspective and gives links to more information.</span></span>  
  
 [<span data-ttu-id="bfe88-128">さまざまなカスタム コントロール</span><span class="sxs-lookup"><span data-stu-id="bfe88-128">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 <span data-ttu-id="bfe88-129">作成できるカスタム コントロールの種類について説明します。</span><span class="sxs-lookup"><span data-stu-id="bfe88-129">Describes the kinds of custom controls you can author.</span></span>
