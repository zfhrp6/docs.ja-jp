---
title: "ToolStrip コントロールの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Toolstrip
helpviewer_keywords:
- ToolStrip control [Windows Forms], about ToolStrip control
- toolbars [Windows Forms], what's new in Windows Forms
- toolbars [Windows Forms]
- what's new [Windows Forms], toolbars
ms.assetid: 81d067ed-297c-4dad-90de-1bcac15336ec
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 45dab820072b3eb0bcc448ce32251e3ff5a3e622
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="toolstrip-control-overview-windows-forms"></a><span data-ttu-id="5c080-102">ToolStrip コントロールの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="5c080-102">ToolStrip Control Overview (Windows Forms)</span></span>
<span data-ttu-id="5c080-103">Windows フォーム<xref:System.Windows.Forms.ToolStrip>コントロールとその関連クラスは、ツールバー、ステータス バー、およびメニューにユーザー インターフェイス要素を結合するため、共通のフレームワークを提供します。</span><span class="sxs-lookup"><span data-stu-id="5c080-103">The Windows Forms <xref:System.Windows.Forms.ToolStrip> control and its associated classes provide a common framework for combining user interface elements into toolbars, status bars, and menus.</span></span> <span data-ttu-id="5c080-104"><xref:System.Windows.Forms.ToolStrip>コントロールは、水平または垂直のスペースを共有するツールバーの機能は、インプレース アクティブ化と編集、カスタム レイアウト、およびラフティング、豊富なデザイン時のエクスペリエンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="5c080-104"><xref:System.Windows.Forms.ToolStrip> controls offer a rich design-time experience that includes in-place activation and editing, custom layout, and rafting, which is the ability of toolbars to share horizontal or vertical space.</span></span>  
  
 <span data-ttu-id="5c080-105"><xref:System.Windows.Forms.ToolStrip>置き換え、以前のバージョン コントロール機能が追加<xref:System.Windows.Forms.ToolBar>は、必要な場合は旧バージョンとの互換性と将来の使用の両方に保持されます。</span><span class="sxs-lookup"><span data-stu-id="5c080-105">Although <xref:System.Windows.Forms.ToolStrip> replaces and adds functionality to the control in previous versions, <xref:System.Windows.Forms.ToolBar> is retained for both backward compatibility and future use if desired.</span></span>  
  
## <a name="features-of-the-toolstrip-controls"></a><span data-ttu-id="5c080-106">ToolStrip コントロールの機能</span><span class="sxs-lookup"><span data-stu-id="5c080-106">Features of the ToolStrip Controls</span></span>  
 <span data-ttu-id="5c080-107">使用して、<xref:System.Windows.Forms.ToolStrip>を制御します。</span><span class="sxs-lookup"><span data-stu-id="5c080-107">Use the <xref:System.Windows.Forms.ToolStrip> control to:</span></span>  
  
-   <span data-ttu-id="5c080-108">コンテナーで共通のユーザー インターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="5c080-108">Present a common user interface across containers.</span></span>  
  
-   <span data-ttu-id="5c080-109">一般的に使用されるサポートするツールバーがユーザー インターフェイスとレイアウト機能、高度なテキストとイメージ、ドロップダウン ボタン、およびコントロールのドッキング、ラフティング、ボタンなどオーバーフロー ボタン、および実行時の並べ替えを実行、簡単にカスタマイズされた<xref:System.Windows.Forms.ToolStrip>項目。</span><span class="sxs-lookup"><span data-stu-id="5c080-109">Create easily customized, commonly employed toolbars that support advanced user interface and layout features, such as docking, rafting, buttons with text and images, drop-down buttons and controls, overflow buttons, and run-time reordering of <xref:System.Windows.Forms.ToolStrip> items.</span></span>  
  
-   <span data-ttu-id="5c080-110">オーバーフローおよび実行時の項目の並べ替えをサポートします。</span><span class="sxs-lookup"><span data-stu-id="5c080-110">Support overflow and run-time item reordering.</span></span> <span data-ttu-id="5c080-111">オーバーフロー機能は、アイテムに移動ドロップダウン メニューに表示する十分な領域がない場合、<xref:System.Windows.Forms.ToolStrip>です。</span><span class="sxs-lookup"><span data-stu-id="5c080-111">The overflow feature moves items to a drop-down menu when there is not enough room to display them in a <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
-   <span data-ttu-id="5c080-112">標準的な外観と一般的なレンダリング モデルにより、オペレーティング システムの動作をサポートします。</span><span class="sxs-lookup"><span data-stu-id="5c080-112">Support the typical appearance and behavior of the operating system through a common rendering model.</span></span>  
  
-   <span data-ttu-id="5c080-113">その他のコントロールのイベントを処理する同じ方法ですべてのコンテナーおよびコンテナー内の項目を一貫してイベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="5c080-113">Handle events consistently for all containers and contained items, in the same way you handle events for other controls.</span></span>  
  
-   <span data-ttu-id="5c080-114">いずれかから項目をドラッグ<xref:System.Windows.Forms.ToolStrip>別内、または、<xref:System.Windows.Forms.ToolStrip>です。</span><span class="sxs-lookup"><span data-stu-id="5c080-114">Drag items from one <xref:System.Windows.Forms.ToolStrip> to another or within a <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
-   <span data-ttu-id="5c080-115">ドロップダウン コントロールとユーザー インターフェイスの型エディターで高度なレイアウトを作成、<xref:System.Windows.Forms.ToolStripDropDown>です。</span><span class="sxs-lookup"><span data-stu-id="5c080-115">Create drop-down controls and user interface type editors with advanced layouts in a <xref:System.Windows.Forms.ToolStripDropDown>.</span></span>  
  
 <span data-ttu-id="5c080-116">使用して、<xref:System.Windows.Forms.ToolStripControlHost>クラスを他のコントロールを使用して、<xref:System.Windows.Forms.ToolStrip>でき<xref:System.Windows.Forms.ToolStrip>それらの機能です。</span><span class="sxs-lookup"><span data-stu-id="5c080-116">Use the <xref:System.Windows.Forms.ToolStripControlHost> class to use other controls on a <xref:System.Windows.Forms.ToolStrip> and gain <xref:System.Windows.Forms.ToolStrip> functionality for them.</span></span>  
  
 <span data-ttu-id="5c080-117">機能を拡張しを使用して外観と動作を変更することができます、 <xref:System.Windows.Forms.ToolStripRenderer>、 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>、および<xref:System.Windows.Forms.ToolStripManager>と共に、<xref:System.Windows.Forms.ToolStripRenderMode>と<xref:System.Windows.Forms.ToolStripManagerRenderMode>列挙体です。</span><span class="sxs-lookup"><span data-stu-id="5c080-117">You can extend the functionality and modify the appearance and behavior by using the <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, and <xref:System.Windows.Forms.ToolStripManager> along with the <xref:System.Windows.Forms.ToolStripRenderMode> and <xref:System.Windows.Forms.ToolStripManagerRenderMode> enumerations.</span></span>  
  
 <span data-ttu-id="5c080-118"><xref:System.Windows.Forms.ToolStrip>コントロールが高い構成可能な拡張可能な多くのプロパティ、メソッド、および外観と動作をカスタマイズするイベントを提供します。</span><span class="sxs-lookup"><span data-stu-id="5c080-118">The <xref:System.Windows.Forms.ToolStrip> control is highly configurable and extensible, and it provides many properties, methods, and events to customize appearance and behavior.</span></span> <span data-ttu-id="5c080-119">いくつかの重要なメンバーを次に示します。</span><span class="sxs-lookup"><span data-stu-id="5c080-119">Below are some noteworthy members:</span></span>  
  
### <a name="important-toolstrip-members"></a><span data-ttu-id="5c080-120">ToolStrip の重要なメンバー</span><span class="sxs-lookup"><span data-stu-id="5c080-120">Important ToolStrip Members</span></span>  
  
|<span data-ttu-id="5c080-121">name</span><span class="sxs-lookup"><span data-stu-id="5c080-121">Name</span></span>|<span data-ttu-id="5c080-122">説明</span><span class="sxs-lookup"><span data-stu-id="5c080-122">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStrip.Dock%2A>|<span data-ttu-id="5c080-123">取得または設定の親コンテナーの端、<xref:System.Windows.Forms.ToolStrip>にドッキングします。</span><span class="sxs-lookup"><span data-stu-id="5c080-123">Gets or sets which edge of the parent container a <xref:System.Windows.Forms.ToolStrip> is docked to.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>|<span data-ttu-id="5c080-124"><xref:System.Windows.Forms.ToolStrip> クラスがドラッグ アンド ドロップおよび項目の並べ替えをプライベートで処理するかどうかを示す値を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="5c080-124">Gets or sets a value indicating whether drag-and-drop and item reordering are handled privately by the <xref:System.Windows.Forms.ToolStrip> class.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>|<span data-ttu-id="5c080-125">取得または設定を示す値、<xref:System.Windows.Forms.ToolStrip>その項目をレイアウトします。</span><span class="sxs-lookup"><span data-stu-id="5c080-125">Gets or sets a value indicating how the <xref:System.Windows.Forms.ToolStrip> lays out its items.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>|<span data-ttu-id="5c080-126">取得または設定するかどうか、<xref:System.Windows.Forms.ToolStripItem>にアタッチされて、<xref:System.Windows.Forms.ToolStrip>または<xref:System.Windows.Forms.ToolStripOverflowButton>または float 型の 2 つのことができます。</span><span class="sxs-lookup"><span data-stu-id="5c080-126">Gets or sets whether a <xref:System.Windows.Forms.ToolStripItem> is attached to the <xref:System.Windows.Forms.ToolStrip> or <xref:System.Windows.Forms.ToolStripOverflowButton> or can float between the two.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.IsDropDown%2A>|<span data-ttu-id="5c080-127">示す値を取得するかどうか、<xref:System.Windows.Forms.ToolStripItem>ドロップダウン リストでその他の項目を表示します。 場合の一覧、<xref:System.Windows.Forms.ToolStripItem>をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5c080-127">Gets a value indicating whether a <xref:System.Windows.Forms.ToolStripItem> displays other items in a drop-down list when the <xref:System.Windows.Forms.ToolStripItem> is clicked.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.OverflowButton%2A>|<span data-ttu-id="5c080-128">オーバーフローが有効な <xref:System.Windows.Forms.ToolStrip> のオーバーフロー ボタンである <xref:System.Windows.Forms.ToolStripItem> を取得します。</span><span class="sxs-lookup"><span data-stu-id="5c080-128">Gets the <xref:System.Windows.Forms.ToolStripItem> that is the overflow button for a <xref:System.Windows.Forms.ToolStrip> with overflow enabled.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.Renderer%2A>|<span data-ttu-id="5c080-129">取得または設定、<xref:System.Windows.Forms.ToolStripRenderer>の (ルック アンド フィール) の動作と外観をカスタマイズするために使用する<xref:System.Windows.Forms.ToolStrip>です。</span><span class="sxs-lookup"><span data-stu-id="5c080-129">Gets or sets a <xref:System.Windows.Forms.ToolStripRenderer> used to customize the appearance and behavior (look and feel) of a <xref:System.Windows.Forms.ToolStrip>.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>|<span data-ttu-id="5c080-130">取得または設定に適用される描画スタイル、<xref:System.Windows.Forms.ToolStrip>です。</span><span class="sxs-lookup"><span data-stu-id="5c080-130">Gets or sets the painting styles to be applied to the <xref:System.Windows.Forms.ToolStrip>.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.RendererChanged>|<span data-ttu-id="5c080-131">いつ発生するか、<xref:System.Windows.Forms.ToolStrip.Renderer%2A>プロパティが変更されました。</span><span class="sxs-lookup"><span data-stu-id="5c080-131">Raised when the <xref:System.Windows.Forms.ToolStrip.Renderer%2A> property changes.</span></span>|  
  
 <span data-ttu-id="5c080-132"><xref:System.Windows.Forms.ToolStrip>に多数のコンパニオン クラスを使用してコントロールの柔軟性を実現します。</span><span class="sxs-lookup"><span data-stu-id="5c080-132">The <xref:System.Windows.Forms.ToolStrip> control's flexibility is achieved through the use of a number of companion classes.</span></span> <span data-ttu-id="5c080-133">最も注目すべきことの一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5c080-133">Below are some of the most noteworthy:</span></span>  
  
### <a name="important-toolstrip-companion-classes"></a><span data-ttu-id="5c080-134">ToolStrip の重要なコンパニオン クラス</span><span class="sxs-lookup"><span data-stu-id="5c080-134">Important ToolStrip Companion Classes</span></span>  
  
|<span data-ttu-id="5c080-135">name</span><span class="sxs-lookup"><span data-stu-id="5c080-135">Name</span></span>|<span data-ttu-id="5c080-136">説明</span><span class="sxs-lookup"><span data-stu-id="5c080-136">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip>|<span data-ttu-id="5c080-137">置き換えする機能を追加、<xref:System.Windows.Forms.MainMenu>クラスです。</span><span class="sxs-lookup"><span data-stu-id="5c080-137">Replaces and adds functionality to the <xref:System.Windows.Forms.MainMenu> class.</span></span>|  
|<xref:System.Windows.Forms.StatusStrip>|<span data-ttu-id="5c080-138">置き換えする機能を追加、<xref:System.Windows.Forms.StatusBar>クラスです。</span><span class="sxs-lookup"><span data-stu-id="5c080-138">Replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> class.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<span data-ttu-id="5c080-139">置き換えする機能を追加、<xref:System.Windows.Forms.ContextMenu>クラスです。</span><span class="sxs-lookup"><span data-stu-id="5c080-139">Replaces and adds functionality to the <xref:System.Windows.Forms.ContextMenu> class.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem>|<span data-ttu-id="5c080-140">抽象基本クラスのイベントとすべての要素のレイアウトを管理すること、 <xref:System.Windows.Forms.ToolStrip>、 <xref:System.Windows.Forms.ToolStripControlHost>、または<xref:System.Windows.Forms.ToolStripDropDown>含めることができます。</span><span class="sxs-lookup"><span data-stu-id="5c080-140">Abstract base class that manages events and layout for all the elements that a <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripControlHost>, or <xref:System.Windows.Forms.ToolStripDropDown> can contain.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer>|<span data-ttu-id="5c080-141">さまざまな方法でコントロールを配置するフォームの各辺にパネルにコンテナーを提供します。</span><span class="sxs-lookup"><span data-stu-id="5c080-141">Provides a container with a panel on each side of the form in which controls can be arranged in various ways.</span></span>|  
|<xref:System.Windows.Forms.ToolStripRenderer>|<span data-ttu-id="5c080-142">描画機能を処理<xref:System.Windows.Forms.ToolStrip>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5c080-142">Handles the painting functionality for <xref:System.Windows.Forms.ToolStrip> objects.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProfessionalRenderer>|<span data-ttu-id="5c080-143">Microsoft Office スタイルの外観を提供します。</span><span class="sxs-lookup"><span data-stu-id="5c080-143">Provides Microsoft Office-style appearance.</span></span>|  
|<xref:System.Windows.Forms.ToolStripManager>|<span data-ttu-id="5c080-144">コントロール<xref:System.Windows.Forms.ToolStrip>レンダリングはラフティング、およびマージ<xref:System.Windows.Forms.MenuStrip>、 <xref:System.Windows.Forms.ToolStripDropDownMenu>、および<xref:System.Windows.Forms.ToolStripMenuItem>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5c080-144">Controls <xref:System.Windows.Forms.ToolStrip> rendering and rafting, and the merging of <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu>, and <xref:System.Windows.Forms.ToolStripMenuItem> objects.</span></span>|  
|<xref:System.Windows.Forms.ToolStripManagerRenderMode>|<span data-ttu-id="5c080-145">指定の倍数に適用される描画スタイル (ユーザー設定、Windows XP、または Microsoft Office Professional)<xref:System.Windows.Forms.ToolStrip>フォームに含まれるオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5c080-145">Specifies the painting style (custom, Windows XP, or Microsoft Office Professional) applied to multiple <xref:System.Windows.Forms.ToolStrip> objects contained in a form.</span></span>|  
|<xref:System.Windows.Forms.ToolStripRenderMode>|<span data-ttu-id="5c080-146">いずれかに適用される描画スタイル (ユーザー設定、Windows XP、または Microsoft Office Professional) を指定<xref:System.Windows.Forms.ToolStrip>フォームに含まれるオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5c080-146">Specifies the painting style (custom, Windows XP, or Microsoft Office Professional) applied to one <xref:System.Windows.Forms.ToolStrip> object contained in a form.</span></span>|  
|<xref:System.Windows.Forms.ToolStripControlHost>|<span data-ttu-id="5c080-147">具体的にはないその他のコントロールをホスト<xref:System.Windows.Forms.ToolStrip>コントロールが対象となる<xref:System.Windows.Forms.ToolStrip>機能します。</span><span class="sxs-lookup"><span data-stu-id="5c080-147">Hosts other controls that are not specifically <xref:System.Windows.Forms.ToolStrip> controls but for which you want <xref:System.Windows.Forms.ToolStrip> functionality.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItemPlacement>|<span data-ttu-id="5c080-148">指定するかどうか、<xref:System.Windows.Forms.ToolStripItem>は主にレイアウトする<xref:System.Windows.Forms.ToolStrip>、オーバーフローに<xref:System.Windows.Forms.ToolStrip>、またはどちらもします。</span><span class="sxs-lookup"><span data-stu-id="5c080-148">Specifies whether a <xref:System.Windows.Forms.ToolStripItem> is to be laid out on the main <xref:System.Windows.Forms.ToolStrip>, on the overflow <xref:System.Windows.Forms.ToolStrip>, or neither.</span></span>|  
  
 <span data-ttu-id="5c080-149">詳細については、次を参照してください。 [ToolStrip テクノロジの概要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)と[ToolStrip コントロールのアーキテクチャ](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)です。</span><span class="sxs-lookup"><span data-stu-id="5c080-149">For more information, see [ToolStrip Technology Summary](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md) and [ToolStrip Control Architecture](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c080-150">参照</span><span class="sxs-lookup"><span data-stu-id="5c080-150">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripDropDown>
