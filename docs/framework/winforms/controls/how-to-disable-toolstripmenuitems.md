---
title: '方法 : ToolStripMenuItems を無効にする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], enabling
- ToolStripMenuItems [Windows Forms], disabling
- menu items [Windows Forms], disabling
- disabling menu items
- menu items [Windows Forms], enabling
- menus [Windows Forms], disabling menu items
ms.assetid: bcc1da84-50fd-41d2-8475-103b581d5654
ms.openlocfilehash: 20d0e13642aac3004a31ff416318cf6723207379
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532029"
---
# <a name="how-to-disable-toolstripmenuitems"></a><span data-ttu-id="7a6e9-102">方法 : ToolStripMenuItems を無効にする</span><span class="sxs-lookup"><span data-stu-id="7a6e9-102">How to: Disable ToolStripMenuItems</span></span>
<span data-ttu-id="7a6e9-103">制限またはを有効にして、ユーザー アクティビティを応答でのメニュー項目を無効にすると、ユーザーが実行できるコマンドの範囲を広げることができます。</span><span class="sxs-lookup"><span data-stu-id="7a6e9-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="7a6e9-104">メニュー項目は既定で有効には、作成されるが、これで調整できる場合に、<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="7a6e9-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="7a6e9-105">デザイン時にこのプロパティを操作することができます、**プロパティ**ウィンドウまたはプログラムによってコードで設定します。</span><span class="sxs-lookup"><span data-stu-id="7a6e9-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span>  
  
### <a name="to-disable-a-menu-item-programmatically"></a><span data-ttu-id="7a6e9-106">メニュー項目をプログラムで無効にするには</span><span class="sxs-lookup"><span data-stu-id="7a6e9-106">To disable a menu item programmatically</span></span>  
  
-   <span data-ttu-id="7a6e9-107">メニュー項目のプロパティを設定するメソッド内で設定するコードを追加、<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>プロパティを`false`です。</span><span class="sxs-lookup"><span data-stu-id="7a6e9-107">Within the method where you set the properties of the menu item, add code to set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>  
  
    ```vb  
    MenuItem1.Enabled = False  
    ```  
  
    ```csharp  
    menuItem1.Enabled = false;  
    ```  
  
    ```cpp  
    menuItem1->Enabled = false;  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="7a6e9-108">メニューの最初または最上位レベルのメニュー項目を無効にすると、メニュー内に含まれるすべてのメニュー項目を非表示が、それらを無効にしません。</span><span class="sxs-lookup"><span data-stu-id="7a6e9-108">Disabling the first or top-level menu item in a menu hides all the menu items contained within the menu, but does not disable them.</span></span> <span data-ttu-id="7a6e9-109">同様に、サブメニュー項目を持つメニュー項目を無効にするサブメニュー項目を非表示が、それらを無効にしません。</span><span class="sxs-lookup"><span data-stu-id="7a6e9-109">Likewise, disabling a menu item that has submenu items hides the submenu items, but does not disable them.</span></span> <span data-ttu-id="7a6e9-110">指定されたメニュー上のすべてのコマンドがユーザーに利用可能な場合は、この場合は、クリーンなユーザー インターフェイスとして両方を非表示にし、メニュー全体を無効にすることをお勧めプログラミングと見なされます。</span><span class="sxs-lookup"><span data-stu-id="7a6e9-110">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="7a6e9-111">非表示にする、メニューを無効にして単独で非表示にする場合、アクセスのショートカット キーを使用してメニュー コマンドにあるために、すべてのアイテムと、メニューのサブメニュー項目を無効にしてください。</span><span class="sxs-lookup"><span data-stu-id="7a6e9-111">You should hide and disable the menu, and disable every item and submenu item in the menu, because hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="7a6e9-112">設定、<xref:System.Windows.Forms.ToolStripItem.Visible%2A>をトップレベルのメニュー項目のプロパティ`false`メニュー全体を非表示にします。</span><span class="sxs-lookup"><span data-stu-id="7a6e9-112">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a6e9-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a6e9-113">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="7a6e9-114">方法: ToolStripMenuItems を非表示にする</span><span class="sxs-lookup"><span data-stu-id="7a6e9-114">How to: Hide ToolStripMenuItems</span></span>](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)  
 [<span data-ttu-id="7a6e9-115">MenuStrip コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="7a6e9-115">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
