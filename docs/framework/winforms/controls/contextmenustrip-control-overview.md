---
title: "ContextMenuStrip コントロールの概要"
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
- ContextMenuStrip
helpviewer_keywords:
- context menus [Windows Forms], ContextMenuStrip control [Windows Forms]
- shortcut menus [Windows Forms], ContextMenuStrip control [Windows Forms]
- ContextMenuStrip control [Windows Forms], about ContextMenuStrip control
ms.assetid: 9787cdb3-88f1-4198-972f-eefd9524ce39
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 11d5de760b8a03d7bc35adabb631048a70e20264
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="contextmenustrip-control-overview"></a><span data-ttu-id="dc6cb-102">ContextMenuStrip コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="dc6cb-102">ContextMenuStrip Control Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="dc6cb-103"><xref:System.Windows.Forms.ContextMenuStrip>コントロールの置換し、する機能を追加、<xref:System.Windows.Forms.ContextMenu>コントロール。 ただし、、<xref:System.Windows.Forms.ContextMenu>を選択した場合、旧バージョンとの互換性および将来使用するコントロールは保持されます。</span><span class="sxs-lookup"><span data-stu-id="dc6cb-103">The <xref:System.Windows.Forms.ContextMenuStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ContextMenu> control; however, the <xref:System.Windows.Forms.ContextMenu> control is retained for backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="dc6cb-104">ユーザーがマウスの右ボタンをクリックしたときに、マウスの位置にショートカット メニューのコンテキスト メニューとも呼ばれますが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dc6cb-104">Shortcut menus, also called context menus, appear at the mouse position when the user clicks the right mouse button.</span></span> <span data-ttu-id="dc6cb-105">ショートカット*メニュー*クライアント領域またはマウスのポインターの位置にコントロールのオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="dc6cb-105">Shortcut *menus* provide options for the client area or the control at the mouse pointer location.</span></span>  
  
 <span data-ttu-id="dc6cb-106"><xref:System.Windows.Forms.ContextMenuStrip>コントロールが新しいしてシームレスに動作するように設計<xref:System.Windows.Forms.ToolStrip>関連付けることができますが、関連するコントロールと、<xref:System.Windows.Forms.ContextMenuStrip>と同様に簡単に他のコントロールとします。</span><span class="sxs-lookup"><span data-stu-id="dc6cb-106">The <xref:System.Windows.Forms.ContextMenuStrip> control is designed to work seamlessly with the new <xref:System.Windows.Forms.ToolStrip> and related controls, but you can associate a <xref:System.Windows.Forms.ContextMenuStrip> with other controls just as easily.</span></span>  
  
 <span data-ttu-id="dc6cb-107">次の表は、重要な<xref:System.Windows.Forms.ContextMenuStrip>コンパニオン クラスです。</span><span class="sxs-lookup"><span data-stu-id="dc6cb-107">The following table shows the important <xref:System.Windows.Forms.ContextMenuStrip> companion classes.</span></span>  
  
|<span data-ttu-id="dc6cb-108">クラス</span><span class="sxs-lookup"><span data-stu-id="dc6cb-108">Class</span></span>|<span data-ttu-id="dc6cb-109">説明</span><span class="sxs-lookup"><span data-stu-id="dc6cb-109">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<span data-ttu-id="dc6cb-110">表示される選択可能なオプションを表す、<xref:System.Windows.Forms.MenuStrip>または<xref:System.Windows.Forms.ContextMenuStrip>です。</span><span class="sxs-lookup"><span data-stu-id="dc6cb-110">Represents a selectable option displayed on a <xref:System.Windows.Forms.MenuStrip> or <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="dc6cb-111">ユーザーが、ユーザーがクリックしたときに表示される一覧から 1 つの項目を選択できるようにするコントロールを表します、<xref:System.Windows.Forms.ToolStripDropDownButton>または高レベルのメニュー項目。</span><span class="sxs-lookup"><span data-stu-id="dc6cb-111">Represents a control that enables the user to select a single item from a list that is displayed when the user clicks a <xref:System.Windows.Forms.ToolStripDropDownButton> or a higher-level menu item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|<span data-ttu-id="dc6cb-112">派生したコントロールの基本的な機能を提供<xref:System.Windows.Forms.ToolStripItem>クリックされたときにドロップダウン項目を表示します。</span><span class="sxs-lookup"><span data-stu-id="dc6cb-112">Provides basic functionality for controls derived from <xref:System.Windows.Forms.ToolStripItem> that display drop-down items when clicked.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc6cb-113">参照</span><span class="sxs-lookup"><span data-stu-id="dc6cb-113">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 <xref:System.Windows.Forms.ToolStripDropDown>
