---
title: "MenuStrip コントロールの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eb27503fffc798b644f95fd213f8f23bdb3e228a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="menustrip-control-overview-windows-forms"></a><span data-ttu-id="14cb9-102">MenuStrip コントロールの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="14cb9-102">MenuStrip Control Overview (Windows Forms)</span></span>
<span data-ttu-id="14cb9-103">メニューは、共通のテーマでグループ化されているコマンドを保持して、ユーザーに機能を公開します。</span><span class="sxs-lookup"><span data-stu-id="14cb9-103">Menus expose functionality to your users by holding commands that are grouped by a common theme.</span></span>  
  
 <span data-ttu-id="14cb9-104"><xref:System.Windows.Forms.MenuStrip>コントロールはこのバージョンの Visual Studio と .NET Framework に新しいです。</span><span class="sxs-lookup"><span data-stu-id="14cb9-104">The <xref:System.Windows.Forms.MenuStrip> control is new to this version of Visual Studio and the .NET Framework.</span></span> <span data-ttu-id="14cb9-105">コントロールで、Microsoft Office で見つかったものと同様のメニューを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="14cb9-105">With the control, you can easily create menus like those found in Microsoft Office.</span></span>  
  
 <span data-ttu-id="14cb9-106"><xref:System.Windows.Forms.MenuStrip>マルチ ドキュメント インターフェイス (MDI) とメニューのマージ、ツール ヒント、およびオーバーフロー コントロールをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="14cb9-106">The <xref:System.Windows.Forms.MenuStrip> control supports the multiple-document interface (MDI) and menu merging, tool tips, and overflow.</span></span> <span data-ttu-id="14cb9-107">アクセス キー、ショートカット キー、チェック マーク、イメージ、およびのセパレーター バーを追加することで、メニューの読みやすさと使いやすさを強化できます。</span><span class="sxs-lookup"><span data-stu-id="14cb9-107">You can enhance the usability and readability of your menus by adding access keys, shortcut keys, check marks, images, and separator bars.</span></span>  
  
 <span data-ttu-id="14cb9-108"><xref:System.Windows.Forms.MenuStrip>コントロールの置換し、する機能を追加、<xref:System.Windows.Forms.MainMenu>コントロール。 ただし、、<xref:System.Windows.Forms.MainMenu>を選択した場合、旧バージョンとの互換性および将来使用するコントロールは保持されます。</span><span class="sxs-lookup"><span data-stu-id="14cb9-108">The <xref:System.Windows.Forms.MenuStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.MainMenu> control; however, the <xref:System.Windows.Forms.MainMenu> control is retained for backward compatibility and future use if you choose.</span></span>  
  
## <a name="ways-to-use-the-menustrip-control"></a><span data-ttu-id="14cb9-109">MenuStrip コントロールの使用方法</span><span class="sxs-lookup"><span data-stu-id="14cb9-109">Ways to Use the MenuStrip Control</span></span>  
 <span data-ttu-id="14cb9-110">使用して、<xref:System.Windows.Forms.MenuStrip>を制御します。</span><span class="sxs-lookup"><span data-stu-id="14cb9-110">Use the <xref:System.Windows.Forms.MenuStrip> control to:</span></span>  
  
-   <span data-ttu-id="14cb9-111">拡張ユーザー テキストとイメージの並べ替えとアラインメント、ドラッグ アンド ドロップ操作、MDI、オーバーフロー、メニュー コマンドにアクセスするの代替モードなどのインターフェイスとレイアウトの機能をサポートするメニューは一般的に使用される、簡単にカスタマイズされた作成します。</span><span class="sxs-lookup"><span data-stu-id="14cb9-111">Create easily customized, commonly employed menus that support advanced user interface and layout features, such as text and image ordering and alignment, drag-and-drop operations, MDI, overflow, and alternate modes of accessing menu commands.</span></span>  
  
-   <span data-ttu-id="14cb9-112">標準的な外観とオペレーティング システムの動作をサポートします。</span><span class="sxs-lookup"><span data-stu-id="14cb9-112">Support the typical appearance and behavior of the operating system.</span></span>  
  
-   <span data-ttu-id="14cb9-113">その他のコントロールのイベントを処理する同じ方法ですべてのコンテナーおよびコンテナー内の項目を一貫してイベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="14cb9-113">Handle events consistently for all containers and contained items, in the same way you handle events for other controls.</span></span>  
  
 <span data-ttu-id="14cb9-114">次の表に、いくつかの特に重要なプロパティ<xref:System.Windows.Forms.MenuStrip>クラスに関連付けられているとします。</span><span class="sxs-lookup"><span data-stu-id="14cb9-114">The following table shows some particularly important properties of <xref:System.Windows.Forms.MenuStrip> and associated classes.</span></span>  
  
|<span data-ttu-id="14cb9-115">プロパティ</span><span class="sxs-lookup"><span data-stu-id="14cb9-115">Property</span></span>|<span data-ttu-id="14cb9-116">説明</span><span class="sxs-lookup"><span data-stu-id="14cb9-116">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|<span data-ttu-id="14cb9-117">取得または設定、 <xref:System.Windows.Forms.ToolStripMenuItem> MDI 子フォームの一覧の表示に使用されます。</span><span class="sxs-lookup"><span data-stu-id="14cb9-117">Gets or sets the <xref:System.Windows.Forms.ToolStripMenuItem> that is used to display a list of MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|<span data-ttu-id="14cb9-118">取得または MDI アプリケーションのメニューを親と子メニューをマージする方法を設定します。</span><span class="sxs-lookup"><span data-stu-id="14cb9-118">Gets or sets how child menus are merged with parent menus in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|<span data-ttu-id="14cb9-119">取得または MDI アプリケーションでメニュー内でマージされた項目の位置を設定します。</span><span class="sxs-lookup"><span data-stu-id="14cb9-119">Gets or sets the position of a merged item within a menu in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|<span data-ttu-id="14cb9-120">取得またはフォームが MDI 子フォームのコンテナーかどうかを示す値を設定します。</span><span class="sxs-lookup"><span data-stu-id="14cb9-120">Gets or sets a value indicating whether the form is a container for MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|<span data-ttu-id="14cb9-121">取得または設定のツール ヒントを表示するかどうかを示す値、<xref:System.Windows.Forms.MenuStrip>です。</span><span class="sxs-lookup"><span data-stu-id="14cb9-121">Gets or sets a value indicating whether tool tips are shown for the <xref:System.Windows.Forms.MenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|<span data-ttu-id="14cb9-122"><xref:System.Windows.Forms.MenuStrip> がオーバーフロー機能をサポートするかどうかを示す値を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="14cb9-122">Gets or sets a value indicating whether the <xref:System.Windows.Forms.MenuStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|<span data-ttu-id="14cb9-123">取得または設定に関連付けられているショートカット キー、<xref:System.Windows.Forms.ToolStripMenuItem>です。</span><span class="sxs-lookup"><span data-stu-id="14cb9-123">Gets or sets the shortcut keys associated with the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|<span data-ttu-id="14cb9-124">関連付けられたショートカット キーのキーかどうかを示す値を取得または設定、<xref:System.Windows.Forms.ToolStripMenuItem>横に表示されますが、<xref:System.Windows.Forms.ToolStripMenuItem>です。</span><span class="sxs-lookup"><span data-stu-id="14cb9-124">Gets or sets a value indicating whether the shortcut keys that are associated with the <xref:System.Windows.Forms.ToolStripMenuItem> are displayed next to the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
  
 <span data-ttu-id="14cb9-125">次の表は、重要な<xref:System.Windows.Forms.MenuStrip>コンパニオン クラスです。</span><span class="sxs-lookup"><span data-stu-id="14cb9-125">The following table shows the important <xref:System.Windows.Forms.MenuStrip> companion classes.</span></span>  
  
|<span data-ttu-id="14cb9-126">クラス</span><span class="sxs-lookup"><span data-stu-id="14cb9-126">Class</span></span>|<span data-ttu-id="14cb9-127">説明</span><span class="sxs-lookup"><span data-stu-id="14cb9-127">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<span data-ttu-id="14cb9-128">表示される選択可能なオプションを表す、<xref:System.Windows.Forms.MenuStrip>または<xref:System.Windows.Forms.ContextMenuStrip>です。</span><span class="sxs-lookup"><span data-stu-id="14cb9-128">Represents a selectable option displayed on a <xref:System.Windows.Forms.MenuStrip> or <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<span data-ttu-id="14cb9-129">ショートカット メニューを表します。</span><span class="sxs-lookup"><span data-stu-id="14cb9-129">Represents a shortcut menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="14cb9-130">ユーザーが、ユーザーがクリックしたときに表示される一覧から 1 つの項目を選択できるコントロールを表す、<xref:System.Windows.Forms.ToolStripDropDownButton>または高レベルのメニュー項目。</span><span class="sxs-lookup"><span data-stu-id="14cb9-130">Represents a control that allows the user to select a single item from a list that is displayed when the user clicks a <xref:System.Windows.Forms.ToolStripDropDownButton> or a higher-level menu item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|<span data-ttu-id="14cb9-131">派生したコントロールの基本的な機能を提供<xref:System.Windows.Forms.ToolStripItem>クリックされたときにドロップダウン項目を表示します。</span><span class="sxs-lookup"><span data-stu-id="14cb9-131">Provides basic functionality for controls derived from <xref:System.Windows.Forms.ToolStripItem> that display drop-down items when clicked.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14cb9-132">参照</span><span class="sxs-lookup"><span data-stu-id="14cb9-132">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripDropDown>
