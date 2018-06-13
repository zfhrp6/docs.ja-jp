---
title: ContextMenu コンポーネントの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
ms.openlocfilehash: 5d548815533e8f9bb37ad00129a5ae526612ea08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526124"
---
# <a name="contextmenu-component-overview-windows-forms"></a><span data-ttu-id="3a49f-102">ContextMenu コンポーネントの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="3a49f-102">ContextMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="3a49f-103"><xref:System.Windows.Forms.MenuStrip>と<xref:System.Windows.Forms.ContextMenuStrip>交換し、する機能を追加、<xref:System.Windows.Forms.MainMenu>と<xref:System.Windows.Forms.ContextMenu>以前のバージョンでのコントロール<xref:System.Windows.Forms.MainMenu>と<xref:System.Windows.Forms.ContextMenu>を選択した場合、旧バージョンとの互換性と将来の使用の両方に保持されます。</span><span class="sxs-lookup"><span data-stu-id="3a49f-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="3a49f-104">Windows フォームで<xref:System.Windows.Forms.ContextMenu>コンポーネント、選択したオブジェクトに関連付けられている頻繁に使用されるコマンドを簡単にアクセスできるショートカット メニューをユーザーに提供できます。</span><span class="sxs-lookup"><span data-stu-id="3a49f-104">With the Windows Forms <xref:System.Windows.Forms.ContextMenu> component, you can provide users with an easily accessible shortcut menu of frequently used commands that are associated with the selected object.</span></span> <span data-ttu-id="3a49f-105">ショートカット メニューの項目は、多くの場合、アプリケーションでの場所に表示されるメイン メニューの項目のサブセットです。</span><span class="sxs-lookup"><span data-stu-id="3a49f-105">The items in a shortcut menu are frequently a subset of the items from main menus that appear elsewhere in the application.</span></span> <span data-ttu-id="3a49f-106">ユーザーは、マウスを右クリックしてショートカット メニューを通常アクセスできます。</span><span class="sxs-lookup"><span data-stu-id="3a49f-106">A user can typically access a shortcut menu by right-clicking the mouse.</span></span> <span data-ttu-id="3a49f-107">Windows フォームでは、ショートカット メニューは、コントロールに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="3a49f-107">On Windows Forms, shortcut menus are associated with controls.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="3a49f-108">キー プロパティ</span><span class="sxs-lookup"><span data-stu-id="3a49f-108">Key Properties</span></span>  
 <span data-ttu-id="3a49f-109">コントロールにするには、コントロールのショートカット メニューを関連付けることができます<xref:System.Windows.Forms.Control.ContextMenu%2A>プロパティを<xref:System.Windows.Forms.ContextMenu>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="3a49f-109">You can associate a shortcut menu with a control by setting the control's <xref:System.Windows.Forms.Control.ContextMenu%2A> property to the <xref:System.Windows.Forms.ContextMenu> component.</span></span> <span data-ttu-id="3a49f-110">1 つのショートカット メニューは、複数のコントロールを関連付けることができますが、各コントロールが 1 つだけのショートカット メニューを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="3a49f-110">A single shortcut menu can be associated with multiple controls, but each control can have only one shortcut menu.</span></span>  
  
 <span data-ttu-id="3a49f-111">キー プロパティ、<xref:System.Windows.Forms.ContextMenu>コンポーネントは、<xref:System.Windows.Forms.Menu.MenuItems%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="3a49f-111">The key property of the <xref:System.Windows.Forms.ContextMenu> component is the <xref:System.Windows.Forms.Menu.MenuItems%2A> property.</span></span> <span data-ttu-id="3a49f-112">メニュー項目を追加するにはプログラムで作成することで<xref:System.Windows.Forms.MenuItem>オブジェクトとに追加すること、<xref:System.Windows.Forms.Menu.MenuItemCollection>のショートカット メニュー。</span><span class="sxs-lookup"><span data-stu-id="3a49f-112">You can add menu items by programmatically creating <xref:System.Windows.Forms.MenuItem> objects and adding them to the <xref:System.Windows.Forms.Menu.MenuItemCollection> of the shortcut menu.</span></span> <span data-ttu-id="3a49f-113">ショートカット メニューの項目は通常、その他のメニューから描画、ためにをコピーしてショートカット メニューに項目を最も頻繁に追加します。</span><span class="sxs-lookup"><span data-stu-id="3a49f-113">Because the items in a shortcut menu are usually drawn from other menus, you will most frequently add items to a shortcut menu by copying them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a49f-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="3a49f-114">See Also</span></span>  
 <xref:System.Windows.Forms.ContextMenu>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>
