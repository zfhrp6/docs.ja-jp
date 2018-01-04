---
title: "MainMenu コンポーネントの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MenuItem
- MainMenu
helpviewer_keywords:
- MainMenu control [Windows Forms], about MainMenu control
- menus
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c8681635f2f97e74893704513f57313106168e52
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="mainmenu-component-overview-windows-forms"></a><span data-ttu-id="cb65c-102">MainMenu コンポーネントの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="cb65c-102">MainMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="cb65c-103"><xref:System.Windows.Forms.MenuStrip>と<xref:System.Windows.Forms.ContextMenuStrip>交換し、する機能を追加、<xref:System.Windows.Forms.MainMenu>と<xref:System.Windows.Forms.ContextMenu>以前のバージョンでのコントロール<xref:System.Windows.Forms.MainMenu>と<xref:System.Windows.Forms.ContextMenu>を選択した場合、旧バージョンとの互換性と将来の使用の両方に保持されます。</span><span class="sxs-lookup"><span data-stu-id="cb65c-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="cb65c-104">Windows フォーム<xref:System.Windows.Forms.MainMenu>コンポーネントには、実行時にメニューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb65c-104">The Windows Forms <xref:System.Windows.Forms.MainMenu> component displays a menu at run time.</span></span> <span data-ttu-id="cb65c-105">メイン メニューと個々 の項目のすべてのサブメニューが<xref:System.Windows.Forms.MenuItem>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="cb65c-105">All submenus of the main menu and individual items are <xref:System.Windows.Forms.MenuItem> objects.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="cb65c-106">キー プロパティ</span><span class="sxs-lookup"><span data-stu-id="cb65c-106">Key Properties</span></span>  
 <span data-ttu-id="cb65c-107">メニュー項目は、設定して既定の項目として指定できる、<xref:System.Windows.Forms.MenuItem.DefaultItem%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="cb65c-107">A menu item can be designated as the default item by setting the <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> property to `true`.</span></span> <span data-ttu-id="cb65c-108">既定の項目は、メニューをクリックすると、太字のテキストに表示されます。</span><span class="sxs-lookup"><span data-stu-id="cb65c-108">The default item appears in bold text when the menu is clicked.</span></span> <span data-ttu-id="cb65c-109">メニュー項目の<xref:System.Windows.Forms.MenuItem.Checked%2A>プロパティが、`true`または`false`、メニュー項目が選択されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="cb65c-109">The menu item's <xref:System.Windows.Forms.MenuItem.Checked%2A> property is either `true` or `false`, and indicates whether the menu item is selected.</span></span> <span data-ttu-id="cb65c-110">メニュー項目の<xref:System.Windows.Forms.MenuItem.RadioCheck%2A>プロパティが選択された項目の外観をカスタマイズ: 場合<xref:System.Windows.Forms.MenuItem.RadioCheck%2A>に設定されている`true`場合に、アイテムの横にあるラジオ ボタンが表示されます<xref:System.Windows.Forms.MenuItem.RadioCheck%2A>に設定されている`false`項目の横にチェック マークを表示します。</span><span class="sxs-lookup"><span data-stu-id="cb65c-110">The menu item's <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> property customizes the appearance of the selected item: if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `true`, a radio button appears next to the item; if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `false`, a check mark appears next to the item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb65c-111">参照</span><span class="sxs-lookup"><span data-stu-id="cb65c-111">See Also</span></span>  
 <xref:System.Windows.Forms.MainMenu>  
 <xref:System.Windows.Forms.Menu>  
 <xref:System.Windows.Forms.MenuItem>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 [<span data-ttu-id="cb65c-112">MenuStrip コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="cb65c-112">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
