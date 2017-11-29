---
title: "TabControl コントロール (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TabControl control [Windows Forms]
- tab controls
- tab controls [Windows Forms], creating
- multipage dialog boxes
- dialog boxes [Windows Forms], creating multipage
- property pages [Windows Forms], creating
- tab dialog boxes
ms.assetid: 915091af-93ac-4d3d-8283-738dd2d21ea7
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fdeb5011e5f44eb45d553045c2f89b97f9e4d100
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="tabcontrol-control-windows-forms"></a><span data-ttu-id="ea0a5-102">TabControl コントロール (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="ea0a5-102">TabControl Control (Windows Forms)</span></span>
<span data-ttu-id="ea0a5-103">Windows フォーム `TabControl` は、ノートの仕切りや書類キャビネットのフォルダー セットのラベルに似た、複数のタブを表示します。</span><span class="sxs-lookup"><span data-stu-id="ea0a5-103">The Windows Forms `TabControl` displays multiple tabs, like dividers in a notebook or labels in a set of folders in a filing cabinet.</span></span> <span data-ttu-id="ea0a5-104">タブには画像やその他のコントロールを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ea0a5-104">The tabs can contain pictures and other controls.</span></span> <span data-ttu-id="ea0a5-105">プロパティ ページを作成するには、`TabControl` を使用します。</span><span class="sxs-lookup"><span data-stu-id="ea0a5-105">Use the `TabControl` to create property pages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ea0a5-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ea0a5-106">In This Section</span></span>  
 [<span data-ttu-id="ea0a5-107">TabControl コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="ea0a5-107">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 <span data-ttu-id="ea0a5-108">このコントロールの用途、主な機能、およびプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ea0a5-108">Explains what this control is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="ea0a5-109">方法: タブ ページにコントロールを追加する</span><span class="sxs-lookup"><span data-stu-id="ea0a5-109">How to: Add a Control to a Tab Page</span></span>](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 <span data-ttu-id="ea0a5-110">タブ ページにコントロールを表示するための手順を示します。</span><span class="sxs-lookup"><span data-stu-id="ea0a5-110">Gives directions for displaying controls on tab pages.</span></span>  
  
 [<span data-ttu-id="ea0a5-111">方法: Windows フォーム TabControl のタブを追加および削除する</span><span class="sxs-lookup"><span data-stu-id="ea0a5-111">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)  
 <span data-ttu-id="ea0a5-112">デザイナーまたはコードのタブを追加および削除する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="ea0a5-112">Gives directions for adding and removing tabs in the designer or in code.</span></span>  
  
 [<span data-ttu-id="ea0a5-113">方法: Windows フォーム TabControl の表示形式を変更する</span><span class="sxs-lookup"><span data-stu-id="ea0a5-113">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)  
 <span data-ttu-id="ea0a5-114">個々のタブの外観に影響するプロパティを調整するための手順を示します。</span><span class="sxs-lookup"><span data-stu-id="ea0a5-114">Gives directions for adjusting properties that affect the appearance of individual tabs.</span></span>  
  
 [<span data-ttu-id="ea0a5-115">方法: タブ ページを無効化する</span><span class="sxs-lookup"><span data-stu-id="ea0a5-115">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 <span data-ttu-id="ea0a5-116">ユーザーの資格情報に基づいて、タブのページへのアクセスを制限する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ea0a5-116">Explains how to restrict access to a tab page, possibly based on user credentials.</span></span>  
  
 <span data-ttu-id="ea0a5-117">参照してください[する方法: を追加し、デザイナーで Windows フォーム TabControl を使用して、削除がタブ](http://msdn.microsoft.com/library/ms233654\(v=vs.110\))、[する方法: タブ ページを使用して、デザイナーにコントロールを追加](http://msdn.microsoft.com/library/ms233668\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="ea0a5-117">Also see [How to: Add and Remove Tabs with the Windows Forms TabControl Using the Designer](http://msdn.microsoft.com/library/ms233654\(v=vs.110\)), [How to: Add a Control to a Tab Page Using the Designer](http://msdn.microsoft.com/library/ms233668\(v=vs.110\))</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ea0a5-118">参照</span><span class="sxs-lookup"><span data-stu-id="ea0a5-118">Reference</span></span>  
 <span data-ttu-id="ea0a5-119"><xref:System.Windows.Forms.TabControl> クラス</span><span class="sxs-lookup"><span data-stu-id="ea0a5-119"><xref:System.Windows.Forms.TabControl> class</span></span>  
 <span data-ttu-id="ea0a5-120">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="ea0a5-120">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ea0a5-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea0a5-121">Related Sections</span></span>  
 [<span data-ttu-id="ea0a5-122">Windows フォームのダイアログ ボックス</span><span class="sxs-lookup"><span data-stu-id="ea0a5-122">Dialog Boxes in Windows Forms</span></span>](../../../../docs/framework/winforms/dialog-boxes-in-windows-forms.md)  
 <span data-ttu-id="ea0a5-123">多くの場合、タブを表示するダイアログ ボックスのタスクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="ea0a5-123">Provides a list of tasks for dialog boxes, which often display tabs.</span></span>  
  
 [<span data-ttu-id="ea0a5-124">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="ea0a5-124">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="ea0a5-125">Windows フォーム コントロールの完全な一覧を、使用に関する情報リンクと共に提供します。</span><span class="sxs-lookup"><span data-stu-id="ea0a5-125">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
