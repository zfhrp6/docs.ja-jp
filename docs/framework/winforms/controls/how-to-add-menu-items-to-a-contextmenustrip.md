---
title: '方法 : メニュー項目を ContextMenuStrip に追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrips [Windows Forms], adding menu items
- shortcut menus [Windows Forms], adding items
- context menus [Windows Forms], adding menu items
ms.assetid: 1ec14776-3ea2-4752-bd22-4fae0fd19e1a
ms.openlocfilehash: d044cf92cf7ce6db3425aacf397d6c7b4f111324
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524626"
---
# <a name="how-to-add-menu-items-to-a-contextmenustrip"></a><span data-ttu-id="c766a-102">方法 : メニュー項目を ContextMenuStrip に追加する</span><span class="sxs-lookup"><span data-stu-id="c766a-102">How to: Add Menu Items to a ContextMenuStrip</span></span>
<span data-ttu-id="c766a-103">一度に 1 つのメニュー項目または複数の項目を追加することができます、<xref:System.Windows.Forms.ContextMenuStrip>です。</span><span class="sxs-lookup"><span data-stu-id="c766a-103">You can add just one menu item or several items at a time to a <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
### <a name="to-add-a-single-menu-item-to-a-contextmenustrip"></a><span data-ttu-id="c766a-104">単一のメニュー項目を ContextMenuStrip に追加するには</span><span class="sxs-lookup"><span data-stu-id="c766a-104">To add a single menu item to a ContextMenuStrip</span></span>  
  
-   <span data-ttu-id="c766a-105">使用して、<xref:System.Windows.Forms.ToolStripItemCollection.Add%2A>を 1 つのメニュー項目を追加するメソッドを<xref:System.Windows.Forms.ContextMenuStrip>です。</span><span class="sxs-lookup"><span data-stu-id="c766a-105">Use the <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> method to add one menu item to a <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
    ```vb  
    Me.contextMenuStrip1.Items.Add(Me.toolStripMenuItem1)  
    ```  
  
    ```csharp  
    this.contextMenuStrip1.Items.Add(toolStripMenuItem1);  
    ```  
  
### <a name="to-add-several-menu-items-to-a-contextmenustrip"></a><span data-ttu-id="c766a-106">いくつかのメニュー項目を ContextMenuStrip に追加するには</span><span class="sxs-lookup"><span data-stu-id="c766a-106">To add several menu items to a ContextMenuStrip</span></span>  
  
-   <span data-ttu-id="c766a-107">使用して、<xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A>をいくつかのメニュー項目を追加するメソッドを<xref:System.Windows.Forms.ContextMenuStrip>です。</span><span class="sxs-lookup"><span data-stu-id="c766a-107">Use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> method to add several menu items to a <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
    ```vb  
    Me.contextMenuStrip1.Items.AddRange(New _  
       System.Windows.Forms.ToolStripItem() {Me.toolStripMenuItem1, _  
          Me.toolStripMenuItem2})  
    ```  
  
    ```csharp  
    this.contextMenuStrip1.Items.AddRange(new   
       System.Windows.Forms.ToolStripItem[] {  
          this.toolStripMenuItem1, this.toolStripMenuItem2});  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c766a-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="c766a-108">See Also</span></span>  
 [<span data-ttu-id="c766a-109">ContextMenuStrip コントロール</span><span class="sxs-lookup"><span data-stu-id="c766a-109">ContextMenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
