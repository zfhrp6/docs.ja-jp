---
title: "方法 : Windows フォーム ContextMenu コンポーネントのメニュー項目を追加および削除する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- context menus [Windows Forms], removing items
- ContextMenu component [Windows Forms], adding items
- shortcut menus [Windows Forms], removing items
- shortcut menus [Windows Forms], examples
- context menus [Windows Forms], adding items
- shortcut menus [Windows Forms], adding items
- ContextMenu component [Windows Forms], removing items
- context menus [Windows Forms], examples
- examples [Windows Forms], context menus
ms.assetid: 426d1eaf-7fb8-4b0b-8a33-5e8721786ea4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cf0e579d5cf377169eeb4d394c4127d53fd54540
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a><span data-ttu-id="f5858-102">方法 : Windows フォーム ContextMenu コンポーネントのメニュー項目を追加および削除する</span><span class="sxs-lookup"><span data-stu-id="f5858-102">How to: Add and Remove Menu Items with the Windows Forms ContextMenu Component</span></span>
<span data-ttu-id="f5858-103">追加し、Windows フォームのショートカット メニュー項目を削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f5858-103">Explains how to add and remove shortcut menu items in Windows Forms.</span></span>  
  
 <span data-ttu-id="f5858-104">Windows フォーム<xref:System.Windows.Forms.ContextMenu>コンポーネントは、選択したオブジェクトに関連する頻繁に使用されるコマンドのメニューを提供します。</span><span class="sxs-lookup"><span data-stu-id="f5858-104">The Windows Forms <xref:System.Windows.Forms.ContextMenu> component provides a menu of frequently used commands that are relevant to the selected object.</span></span> <span data-ttu-id="f5858-105">ショートカット メニューに追加することで項目を追加することができます<xref:System.Windows.Forms.MenuItem>オブジェクトを<xref:System.Windows.Forms.Menu.MenuItems%2A>コレクション。</span><span class="sxs-lookup"><span data-stu-id="f5858-105">You can add items to the shortcut menu by adding <xref:System.Windows.Forms.MenuItem> objects to the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection.</span></span>  
  
 <span data-ttu-id="f5858-106">完全; ショートカット メニューから項目を削除できます。ただし、実行時にある可能性がありますを非表示にまたは、代わりに、項目を無効にする方が適しています。</span><span class="sxs-lookup"><span data-stu-id="f5858-106">You can remove items from a shortcut menu permanently; however, at run time it may be more appropriate to hide or disable the items instead.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f5858-107"><xref:System.Windows.Forms.MenuStrip>と<xref:System.Windows.Forms.ContextMenuStrip>交換し、する機能を追加、<xref:System.Windows.Forms.MainMenu>と<xref:System.Windows.Forms.ContextMenu>以前のバージョンでのコントロール<xref:System.Windows.Forms.MainMenu>と<xref:System.Windows.Forms.ContextMenu>を選択した場合、旧バージョンとの互換性と将来の使用の両方に保持されます。</span><span class="sxs-lookup"><span data-stu-id="f5858-107">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a><span data-ttu-id="f5858-108">ショートカット メニューから項目を削除するには</span><span class="sxs-lookup"><span data-stu-id="f5858-108">To remove items from a shortcut menu</span></span>  
  
1.  <span data-ttu-id="f5858-109">使用して、<xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A>または<xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A>のメソッド、<xref:System.Windows.Forms.Menu.MenuItems%2A>のコレクション、<xref:System.Windows.Forms.ContextMenu>特定のメニュー項目を削除するコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="f5858-109">Use the <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> or <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection of the <xref:System.Windows.Forms.ContextMenu> component to remove a particular menu item.</span></span>  
  
    ```vb  
    ' Removes the first item in the shortcut menu.  
    ContextMenu1.MenuItems.RemoveAt(0)  
    ' Removes a particular object from the shortcut menu.  
    ContextMenu1.MenuItems.Remove(mnuItemNew)  
    ```  
  
    ```csharp  
    // Removes the first item in the shortcut menu.  
    contextMenu1.MenuItems.RemoveAt(0);  
    // Removes a particular object from the shortcut menu.  
    contextMenu1.MenuItems.Remove(mnuItemNew);  
    ```  
  
    ```cpp  
    // Removes the first item in the shortcut menu.  
    contextMenu1->MenuItems->RemoveAt(0);  
    // Removes a particular object from the shortcut menu.  
    contextMenu1->MenuItems->Remove(mnuItemNew);  
    ```  
  
     <span data-ttu-id="f5858-110">または</span><span class="sxs-lookup"><span data-stu-id="f5858-110">-or-</span></span>  
  
2.  <span data-ttu-id="f5858-111">使用して、`Clear`のメソッド、`MenuItems`のコレクション、 <xref:System.Windows.Forms.ContextMenu>  メニューからすべての項目を削除するコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="f5858-111">Use the `Clear` method of the `MenuItems` collection of the <xref:System.Windows.Forms.ContextMenu> component to remove all items from the menu.</span></span>  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f5858-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5858-112">See Also</span></span>  
 <xref:System.Windows.Forms.ContextMenu>  
 [<span data-ttu-id="f5858-113">ContextMenu コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f5858-113">ContextMenu Component</span></span>](../../../../docs/framework/winforms/controls/contextmenu-component-windows-forms.md)  
 [<span data-ttu-id="f5858-114">ContextMenu コンポーネントの概要</span><span class="sxs-lookup"><span data-stu-id="f5858-114">ContextMenu Component Overview</span></span>](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)
