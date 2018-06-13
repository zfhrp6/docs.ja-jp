---
title: '方法 : Windows フォーム ContextMenu コンポーネントのメニュー項目を追加および削除する'
ms.date: 03/30/2017
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
ms.openlocfilehash: 7cc11eaf4a671c76933c2705b41a4df6c35c0536
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524730"
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a>方法 : Windows フォーム ContextMenu コンポーネントのメニュー項目を追加および削除する
追加し、Windows フォームのショートカット メニュー項目を削除する方法について説明します。  
  
 Windows フォーム<xref:System.Windows.Forms.ContextMenu>コンポーネントは、選択したオブジェクトに関連する頻繁に使用されるコマンドのメニューを提供します。 ショートカット メニューに追加することで項目を追加することができます<xref:System.Windows.Forms.MenuItem>オブジェクトを<xref:System.Windows.Forms.Menu.MenuItems%2A>コレクション。  
  
 完全; ショートカット メニューから項目を削除できます。ただし、実行時にある可能性がありますを非表示にまたは、代わりに、項目を無効にする方が適しています。  
  
> [!IMPORTANT]
>  <xref:System.Windows.Forms.MenuStrip>と<xref:System.Windows.Forms.ContextMenuStrip>交換し、する機能を追加、<xref:System.Windows.Forms.MainMenu>と<xref:System.Windows.Forms.ContextMenu>以前のバージョンでのコントロール<xref:System.Windows.Forms.MainMenu>と<xref:System.Windows.Forms.ContextMenu>を選択した場合、旧バージョンとの互換性と将来の使用の両方に保持されます。  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a>ショートカット メニューから項目を削除するには  
  
1.  使用して、<xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A>または<xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A>のメソッド、<xref:System.Windows.Forms.Menu.MenuItems%2A>のコレクション、<xref:System.Windows.Forms.ContextMenu>特定のメニュー項目を削除するコンポーネントです。  
  
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
  
     - または -  
  
2.  使用して、`Clear`のメソッド、`MenuItems`のコレクション、 <xref:System.Windows.Forms.ContextMenu>  メニューからすべての項目を削除するコンポーネントです。  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ContextMenu>  
 [ContextMenu コンポーネント](../../../../docs/framework/winforms/controls/contextmenu-component-windows-forms.md)  
 [ContextMenu コンポーネントの概要](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)
