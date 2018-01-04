---
title: "Windows フォーム コントロール開発の基本概念"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], derivation types
- programming concepts [Windows Forms], Windows Forms controls
- controls [Windows Forms], creating
ms.assetid: 6277bb81-90f7-4c5b-9f4b-b02bb42dd316
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bcf06f4dc0d8c70ae85d5add5a2fee078238d5e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-control-development-basics"></a><span data-ttu-id="7ddda-102">Windows フォーム コントロール開発の基本概念</span><span class="sxs-lookup"><span data-stu-id="7ddda-102">Windows Forms Control Development Basics</span></span>
<span data-ttu-id="7ddda-103">Windows フォーム コントロールから直接または間接的に派生したクラスは、<xref:System.Windows.Forms.Control?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="7ddda-103">A Windows Forms control is a class that derives directly or indirectly from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7ddda-104">次の一覧には、Windows フォーム コントロールを開発するための一般的なシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7ddda-104">The following list describes common scenarios for developing Windows Forms controls:</span></span>  
  
-   <span data-ttu-id="7ddda-105">複合コントロールを作成する既存の組み合わせを制御します。</span><span class="sxs-lookup"><span data-stu-id="7ddda-105">Combining existing controls to author a composite control.</span></span>  
  
     <span data-ttu-id="7ddda-106">複合コントロールには、コントロールとして再利用可能なユーザー インターフェイスがカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="7ddda-106">Composite controls encapsulate a user interface that can be reused as a control.</span></span> <span data-ttu-id="7ddda-107">複合コントロールの例は、テキスト ボックスと [リセット] ボタンで構成されるコントロールです。</span><span class="sxs-lookup"><span data-stu-id="7ddda-107">An example of a composite control is a control that consists of a text box and a reset button.</span></span> <span data-ttu-id="7ddda-108">ビジュアル デザイナーでは、複合コントロールを作成するための豊富なサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="7ddda-108">Visual designers offer rich support for creating composite controls.</span></span> <span data-ttu-id="7ddda-109">派生する複合コントロールを作成するには、<xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="7ddda-109">To author a composite control, derive from <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7ddda-110">基本クラス<xref:System.Windows.Forms.UserControl>キーボード ルーティングを提供する子コントロールおよび子コントロールがグループとして動作できるようにします。</span><span class="sxs-lookup"><span data-stu-id="7ddda-110">The base class <xref:System.Windows.Forms.UserControl> provides keyboard routing for child controls and enables child controls to work as a group.</span></span> <span data-ttu-id="7ddda-111">詳細については、「[複合 Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ddda-111">For more information, see [Developing a Composite Windows Forms Control](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md).</span></span>  
  
-   <span data-ttu-id="7ddda-112">それをカスタマイズする、またはその機能に追加する既存のコントロールを拡張します。</span><span class="sxs-lookup"><span data-stu-id="7ddda-112">Extending an existing control to customize it or to add to its functionality.</span></span>  
  
     <span data-ttu-id="7ddda-113">色を変更することはできません ボタンとボタンがクリックしてされた回数を追跡する追加のプロパティを持つ拡張コントロールの例に示します。</span><span class="sxs-lookup"><span data-stu-id="7ddda-113">A button whose color cannot be changed and a button that has an additional property that tracks how many times it has been clicked are examples of extended controls.</span></span> <span data-ttu-id="7ddda-114">クラスを派生し、プロパティ、メソッド、およびイベントを追加、またはオーバーライドして、Windows フォーム コントロールをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="7ddda-114">You can customize any Windows Forms control by deriving from it and overriding or adding properties, methods, and events.</span></span>  
  
-   <span data-ttu-id="7ddda-115">結合や既存のコントロールを拡張しないコントロールを作成します。</span><span class="sxs-lookup"><span data-stu-id="7ddda-115">Authoring a control that does not combine or extend existing controls.</span></span>  
  
     <span data-ttu-id="7ddda-116">このシナリオでは、基本クラスからコントロールを派生<xref:System.Windows.Forms.Control>です。</span><span class="sxs-lookup"><span data-stu-id="7ddda-116">In this scenario, derive your control from the base class <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="7ddda-117">追加したり、プロパティ、メソッド、および基本クラスのイベントを上書きしたりします。</span><span class="sxs-lookup"><span data-stu-id="7ddda-117">You can add as well as override properties, methods, and events of the base class.</span></span> <span data-ttu-id="7ddda-118">最初に、次を参照してください。[する方法: シンプルな Windows フォーム コントロールを開発](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="7ddda-118">To get started, see [How to: Develop a Simple Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md).</span></span>  
  
 <span data-ttu-id="7ddda-119">Windows フォーム コントロールの基底クラス<xref:System.Windows.Forms.Control>、Windows ベースのクライアント側アプリケーションでのビジュアル表示に必要な組み込みを提供します。</span><span class="sxs-lookup"><span data-stu-id="7ddda-119">The base class for Windows Forms controls, <xref:System.Windows.Forms.Control>, provides the plumbing required for visual display in client-side Windows-based applications.</span></span> <span data-ttu-id="7ddda-120"><xref:System.Windows.Forms.Control>ウィンドウ ハンドル、メッセージのルーティングの処理し、マウスとキーボード イベントだけでなく他の多くのユーザー インターフェイスのイベントを提供します。</span><span class="sxs-lookup"><span data-stu-id="7ddda-120"><xref:System.Windows.Forms.Control> provides a window handle, handles message routing, and provides mouse and keyboard events as well as many other user interface events.</span></span> <span data-ttu-id="7ddda-121">高度なレイアウトを提供し、視覚的に表示する固有のプロパティをなどが<xref:System.Windows.Forms.Control.ForeColor%2A>、 <xref:System.Windows.Forms.Control.BackColor%2A>、 <xref:System.Windows.Forms.Control.Height%2A>、 <xref:System.Windows.Forms.Control.Width%2A>、およびその他の多くのです。</span><span class="sxs-lookup"><span data-stu-id="7ddda-121">It provides advanced layout and has properties specific to visual display, such as <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, and many others.</span></span> <span data-ttu-id="7ddda-122">さらに、セキュリティ、スレッド処理のサポート、および ActiveX コントロールとの相互運用性を提供します。</span><span class="sxs-lookup"><span data-stu-id="7ddda-122">Additionally, it provides security, threading support, and interoperability with ActiveX controls.</span></span> <span data-ttu-id="7ddda-123">インフラストラクチャの大部分は基本クラスによって提供されるため、独自の Windows フォーム コントロールを比較的簡単に開発できます。</span><span class="sxs-lookup"><span data-stu-id="7ddda-123">Because so much of the infrastructure is provided by the base class, it is relatively easy to develop your own Windows Forms controls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ddda-124">参照</span><span class="sxs-lookup"><span data-stu-id="7ddda-124">See Also</span></span>  
 [<span data-ttu-id="7ddda-125">方法: シンプルな Windows フォーム コントロールを開発する</span><span class="sxs-lookup"><span data-stu-id="7ddda-125">How to: Develop a Simple Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [<span data-ttu-id="7ddda-126">複合 Windows フォーム コントロールの開発</span><span class="sxs-lookup"><span data-stu-id="7ddda-126">Developing a Composite Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)  
 [<span data-ttu-id="7ddda-127">方法: 進行状況を示す Windows フォーム コントロールを作成する</span><span class="sxs-lookup"><span data-stu-id="7ddda-127">How to: Create a Windows Forms Control That Shows Progress</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)  
 [<span data-ttu-id="7ddda-128">さまざまなカスタム コントロール</span><span class="sxs-lookup"><span data-stu-id="7ddda-128">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
