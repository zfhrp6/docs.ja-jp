---
title: "ListView コントロール (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lists
- checked list items [Windows Forms], Windows Forms controls
- user interface [Windows Forms], creating
- lists [Windows Forms], items with icons
- icons [Windows Forms], listing with items
- list views
- ListView control [Windows Forms]
- list controls [Windows Forms], List view
ms.assetid: 9f71cf5c-82da-488a-a04e-ef52c0817187
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8328bc705349ffeaa78d95e95ed0955ac6faa5c3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="listview-control-windows-forms"></a><span data-ttu-id="7ae92-102">ListView コントロール (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="7ae92-102">ListView Control (Windows Forms)</span></span>
<span data-ttu-id="7ae92-103">Windows フォーム `ListView` コントロールにはアイコン表示で項目の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7ae92-103">The Windows Forms `ListView` control displays a list of items with icons.</span></span> <span data-ttu-id="7ae92-104">リスト ビューを使用すると、Windows エクスプローラーの右側のペインのようなユーザー インターフェイスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="7ae92-104">You can use a list view to create a user interface like the right pane of Windows Explorer.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7ae92-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="7ae92-105">In This Section</span></span>  
 [<span data-ttu-id="7ae92-106">ListView コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="7ae92-106">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 <span data-ttu-id="7ae92-107">このコントロールの用途、主な機能、およびプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7ae92-107">Describes this control and its key features and properties.</span></span>  
  
 [<span data-ttu-id="7ae92-108">方法: Windows フォーム ListView コントロールで項目を追加および削除する</span><span class="sxs-lookup"><span data-stu-id="7ae92-108">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 <span data-ttu-id="7ae92-109">リスト ビューから項目を追加または削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7ae92-109">Describes how to add or remove items from a list view.</span></span>  
  
 [<span data-ttu-id="7ae92-110">方法: Windows フォーム ListView コントロールに列を追加する</span><span class="sxs-lookup"><span data-stu-id="7ae92-110">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 <span data-ttu-id="7ae92-111">各リスト項目に関する情報を表示するために列を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7ae92-111">Describes how to create columns in order to display information about each list item.</span></span>  
  
 [<span data-ttu-id="7ae92-112">方法: Windows フォーム ListView コントロールのアイコンを表示する</span><span class="sxs-lookup"><span data-stu-id="7ae92-112">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 <span data-ttu-id="7ae92-113">大きいアイコンまたは小さいアイコンを表示するための適切なイメージ リストとリスト ビューを関連付ける方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7ae92-113">Describes how to associate a list view with an appropriate image list for displaying large or small icons.</span></span>  
  
 [<span data-ttu-id="7ae92-114">方法: Windows フォーム ListView コントロールの列にサブ項目を表示する</span><span class="sxs-lookup"><span data-stu-id="7ae92-114">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 <span data-ttu-id="7ae92-115">列の各リスト項目に関する情報を表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7ae92-115">Describes how to display information about each list item in columns.</span></span>  
  
 [<span data-ttu-id="7ae92-116">方法: Windows フォーム ListView コントロール内の項目を選択する</span><span class="sxs-lookup"><span data-stu-id="7ae92-116">How to: Select an Item in the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-an-item-in-the-windows-forms-listview-control.md)  
 <span data-ttu-id="7ae92-117">プログラムによって項目を選択する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7ae92-117">Describes how to programmatically select an item.</span></span>  
  
 [<span data-ttu-id="7ae92-118">方法: Windows フォーム ListView コントロールの項目をグループ化する</span><span class="sxs-lookup"><span data-stu-id="7ae92-118">How to: Group Items in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="7ae92-119">カテゴリ別表示用のグループを作成して各グループに項目を割り当てる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7ae92-119">Describes how to create groups for categorized display and how to assign items to each group.</span></span>  
  
 <span data-ttu-id="7ae92-120">この機能は、[!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="7ae92-120">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="7ae92-121">方法: Windows フォーム ListView コントロールの "並べて表示" ビューを有効にする</span><span class="sxs-lookup"><span data-stu-id="7ae92-121">How to: Enable Tile View in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-tile-view-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="7ae92-122">大きいアイコンと複数行のテキストで構成される項目のタイル表示の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7ae92-122">Describes how to display items as tiles, each of which is comprised of a large icon and multiple lines of text.</span></span>  
  
 <span data-ttu-id="7ae92-123">この機能は、[!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="7ae92-123">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="7ae92-124">方法: Windows フォーム ListView コントロールに挿入マークを表示する</span><span class="sxs-lookup"><span data-stu-id="7ae92-124">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="7ae92-125">挿入マークがマウス ポインターの位置ごとにドロップする場所を示す、ドラッグ アンド ドロップ操作のためのユーザー フィードバックを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7ae92-125">Describes how to implement user-feedback for drag-and-drop operations in which an insertion mark indicates the drop location for each mouse-pointer position.</span></span>  
  
 <span data-ttu-id="7ae92-126">この機能は、[!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="7ae92-126">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="7ae92-127">方法: ListView コントロールに検索機能を追加する</span><span class="sxs-lookup"><span data-stu-id="7ae92-127">How to: Add Search Capabilities to a ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
 <span data-ttu-id="7ae92-128">プログラムでいずれかのテキストの検索または画面座標を使用してアイテムを検索する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7ae92-128">Describes how to programmatically find an item using either text search or screen coordinates.</span></span>  
  
-   <span data-ttu-id="7ae92-129">[方法: デザイナーを使って Windows フォーム ListView コントロールの "並べて表示" ビューを有効にする](http://msdn.microsoft.com/library/ms233655\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="7ae92-129">[How to: Enable Tile View in a Windows Forms ListView Control Using the Designer](http://msdn.microsoft.com/library/ms233655\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="7ae92-130">[方法: デザイナーで Windows フォーム ListView コントロールを使って項目を追加および削除する](http://msdn.microsoft.com/library/ms233671\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="7ae92-130">[How to: Add and Remove Items with the Windows Forms ListView Control Using the Designer](http://msdn.microsoft.com/library/ms233671\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="7ae92-131">[方法: デザイナーを使って Windows フォーム ListView コントロールに列を追加する](http://msdn.microsoft.com/library/ms233652\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="7ae92-131">[How to: Add Columns to the Windows Forms ListView Control Using the Designer](http://msdn.microsoft.com/library/ms233652\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="7ae92-132">[方法: デザイナーを使って Windows フォーム ListView コントロールの項目をグループ化する](http://msdn.microsoft.com/library/ms233663\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="7ae92-132">[How to: Group Items in a Windows Forms ListView Control Using the Designer](http://msdn.microsoft.com/library/ms233663\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="7ae92-133">[チュートリアル: デザイナーを使用した、ListView コントロールと TreeView コントロールを含むエクスプローラー スタイルのインターフェイスの作成](http://msdn.microsoft.com/library/ms171645\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="7ae92-133">[Walkthrough: Creating an Explorer Style Interface with the ListView and TreeView Controls Using the Designer](http://msdn.microsoft.com/library/ms171645\(v=vs.110\))</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7ae92-134">参照</span><span class="sxs-lookup"><span data-stu-id="7ae92-134">Reference</span></span>  
 <span data-ttu-id="7ae92-135"><xref:System.Windows.Forms.ListView> クラス</span><span class="sxs-lookup"><span data-stu-id="7ae92-135"><xref:System.Windows.Forms.ListView> class</span></span>  
 <span data-ttu-id="7ae92-136">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="7ae92-136">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7ae92-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ae92-137">Related Sections</span></span>  
 [<span data-ttu-id="7ae92-138">方法: TreeView コントロールまたは ListView コントロール (Windows フォーム) にカスタム情報を追加する</span><span class="sxs-lookup"><span data-stu-id="7ae92-138">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 <span data-ttu-id="7ae92-139">リスト ビュー内のアイテムまたはツリー ビュー内のノードから継承して、必要なフィールド、メソッド、またはコンストラクターを追加するための手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="7ae92-139">Describes how to inherit from an item in a list view or a node in a tree view in order to add any fields, methods, or constructors you need.</span></span>  
  
 [<span data-ttu-id="7ae92-140">ImageList コンポーネント</span><span class="sxs-lookup"><span data-stu-id="7ae92-140">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)  
 <span data-ttu-id="7ae92-141">イメージ リストの用途、主な機能、およびプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7ae92-141">Explains what an image list is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="7ae92-142">方法: Windows フォームでマルチペイン ユーザー インターフェイスを作成する</span><span class="sxs-lookup"><span data-stu-id="7ae92-142">How to: Create a Multipane User Interface with Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="7ae92-143">複数のペインで Windows フォームのレイアウトを設定するための方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="7ae92-143">Gives instructions for laying out a Windows Form with multiple panes.</span></span>  
  
 [<span data-ttu-id="7ae92-144">Windows XP の機能と Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="7ae92-144">Windows XP Features and Windows Forms Controls</span></span>](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 <span data-ttu-id="7ae92-145"><xref:System.Windows.Forms.ListView> コントロールに適用される、Windows XP に固有の機能を活用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7ae92-145">Explains how to take advantage of Windows XP-specific features that apply to the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ae92-146">参照</span><span class="sxs-lookup"><span data-stu-id="7ae92-146">See Also</span></span>  
 [<span data-ttu-id="7ae92-147">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="7ae92-147">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
