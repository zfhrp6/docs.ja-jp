---
title: "SplitContainer コントロール (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- splitter windows
- SplitContainer control [Windows Forms]
ms.assetid: 2e36f17f-5c39-4fb4-bb09-7ce3ef823402
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 336243cc4db7039225ba272cac1ba7a3f173f361
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="splitcontainer-control-windows-forms"></a><span data-ttu-id="df772-102">SplitContainer コントロール (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="df772-102">SplitContainer Control (Windows Forms)</span></span>
<span data-ttu-id="df772-103">Windows フォームの `SplitContainer` コントロールは複合と考えることができ、移動可能なバーで区切られた 2 つのパネルです。</span><span class="sxs-lookup"><span data-stu-id="df772-103">The Windows Forms `SplitContainer` control can be thought of as a composite; it is two panels separated by a movable bar.</span></span> <span data-ttu-id="df772-104">マウス ポインターがバーの上に移動すると、ポインターの形が変わり、バーが移動可能であることを示します。</span><span class="sxs-lookup"><span data-stu-id="df772-104">When the mouse pointer is over the bar, the pointer changes shape to show that the bar is movable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df772-105">**ツールボックス**、この置換を制御、 <xref:System.Windows.Forms.Splitter> Visual Studio の以前のバージョンに存在していたコントロール。</span><span class="sxs-lookup"><span data-stu-id="df772-105">In the **Toolbox**, this control replaces the <xref:System.Windows.Forms.Splitter> control that was there in the previous version of Visual Studio.</span></span> <span data-ttu-id="df772-106">`SplitContainer` コントロールは <xref:System.Windows.Forms.Splitter> コントロールより優先されます。</span><span class="sxs-lookup"><span data-stu-id="df772-106">The `SplitContainer` control is much preferred over the <xref:System.Windows.Forms.Splitter> control.</span></span> <span data-ttu-id="df772-107"><xref:System.Windows.Forms.Splitter> クラスは、既存のアプリケーションの互換性のために .NET Framework に含まれていますが、新しいプロジェクトでは `SplitContainer` コントロールを使用することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="df772-107">The <xref:System.Windows.Forms.Splitter> class is still included in the .NET Framework for compatibility with existing applications, but we strongly encourage you to use the `SplitContainer` control for new projects.</span></span>  
  
 <span data-ttu-id="df772-108">`SplitContainer` コントロールでは複雑なユーザー インターフェイスを作成できます。多くの場合、1 つのパネルの選択項目が、もう一方のパネルに表示されるオブジェクトを決定します。</span><span class="sxs-lookup"><span data-stu-id="df772-108">The `SplitContainer` control lets you create complex user interfaces; often, a selection in one panel determines what objects are shown in the other panel.</span></span> <span data-ttu-id="df772-109">この配置は、情報の表示と参照に対して非常に効果的です。</span><span class="sxs-lookup"><span data-stu-id="df772-109">This arrangement is very effective for displaying and browsing information.</span></span> <span data-ttu-id="df772-110">2 つのパネルを使用することで、情報を領域に集約でき、バーまたは「分割」により、ユーザーがパネルを簡単にサイズ変更できます。</span><span class="sxs-lookup"><span data-stu-id="df772-110">Having two panels allow you to aggregate information in areas, and the bar, or "splitter," makes it easy for users to resize the panels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="df772-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="df772-111">In This Section</span></span>  
 [<span data-ttu-id="df772-112">SplitContainer コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="df772-112">SplitContainer Control Overview</span></span>](../../../../docs/framework/winforms/controls/splitcontainer-control-overview-windows-forms.md)  
 <span data-ttu-id="df772-113">`SplitContainer` コントロールを導入し、一般的に使用されるプロパティ、メソッド、およびイベントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="df772-113">Introduces the `SplitContainer` control and describes the commonly used properties, methods, and events.</span></span>  
  
 [<span data-ttu-id="df772-114">方法: 分割ウィンドウでのサイズ変更および位置指定動作を定義する</span><span class="sxs-lookup"><span data-stu-id="df772-114">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](../../../../docs/framework/winforms/controls/how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 <span data-ttu-id="df772-115">`SplitContainer` コントロール内のスプリッターを制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="df772-115">Describes how to control the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="df772-116">方法: ウィンドウを水平方向に分割する</span><span class="sxs-lookup"><span data-stu-id="df772-116">How to: Split a Window Horizontally</span></span>](../../../../docs/framework/winforms/controls/how-to-split-a-window-horizontally.md)  
 <span data-ttu-id="df772-117">`SplitContainer` コントロール内のスプリッターの方向を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="df772-117">Describes how to control the orientation of the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="df772-118">方法: Windows フォームでマルチペイン ユーザー インターフェイスを作成する</span><span class="sxs-lookup"><span data-stu-id="df772-118">How to: Create a Multipane User Interface with Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="df772-119">Microsoft Outlook で使用されるような複数ペインのユーザー インターフェイスを作成します。</span><span class="sxs-lookup"><span data-stu-id="df772-119">Creates a multi-pane user interface that is similar to the one used in Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="df772-120">参照してください[する方法: 分割ウィンドウ幅を使用して、デザイナー](http://msdn.microsoft.com/library/ms233667\(v=vs.110\))、[する方法: Windows フォームで Windows エクスプ ローラー スタイルのインターフェイスを作成する](http://msdn.microsoft.com/library/zh2fe5a5\(v=vs.110\))、[する方法: Multipane ユーザー インターフェイスを作成します。Windows フォーム デザイナーを使用して](http://msdn.microsoft.com/library/ms233661\(v=vs.110\))です。</span><span class="sxs-lookup"><span data-stu-id="df772-120">Also see [How to: Split a Window Horizontally Using the Designer](http://msdn.microsoft.com/library/ms233667\(v=vs.110\)), [How to: Create a Windows Explorer–Style Interface on a Windows Form](http://msdn.microsoft.com/library/zh2fe5a5\(v=vs.110\)), [How to: Create a Multipane User Interface with Windows Forms Using the Designer](http://msdn.microsoft.com/library/ms233661\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="df772-121">参照</span><span class="sxs-lookup"><span data-stu-id="df772-121">Reference</span></span>  
 <span data-ttu-id="df772-122"><xref:System.Windows.Forms.SplitContainer> クラス</span><span class="sxs-lookup"><span data-stu-id="df772-122"><xref:System.Windows.Forms.SplitContainer> class</span></span>  
 <span data-ttu-id="df772-123">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="df772-123">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="df772-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="df772-124">Related Sections</span></span>  
 [<span data-ttu-id="df772-125">Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="df772-125">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 <span data-ttu-id="df772-126">Windows フォームでの操作専用に設計されているコントロールについてのトピックへのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="df772-126">Provides links to topics about the controls designed specifically to work with Windows Forms.</span></span>  
  
 [<span data-ttu-id="df772-127">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="df772-127">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="df772-128">Windows フォーム コントロールの完全な一覧を、使用に関する情報リンクと共に提供します。</span><span class="sxs-lookup"><span data-stu-id="df772-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
