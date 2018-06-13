---
title: '方法 : ToolStripMenuItems を非表示にする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding
- MenuStrip control [Windows Forms], hiding menu items
- menus [Windows Forms], hiding menu items
- menu items [Windows Forms], hiding
- hiding menu items
ms.assetid: 418a768f-808a-44cd-8cef-f4e161883621
ms.openlocfilehash: 73f67bbe6b2d51a59b6f72ab5faf21db9d6db12d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531954"
---
# <a name="how-to-hide-toolstripmenuitems"></a><span data-ttu-id="b4672-102">方法 : ToolStripMenuItems を非表示にする</span><span class="sxs-lookup"><span data-stu-id="b4672-102">How to: Hide ToolStripMenuItems</span></span>
<span data-ttu-id="b4672-103">メニュー項目を非表示には、アプリケーションのユーザー インターフェイスを制御し、ユーザーのコマンドを制限する方法です。</span><span class="sxs-lookup"><span data-stu-id="b4672-103">Hiding menu items is a way to control the user interface of your application and restrict user commands.</span></span> <span data-ttu-id="b4672-104">多くの場合、すべてのメニュー項目が利用できない場合は、メニュー全体を非表示にするされます。</span><span class="sxs-lookup"><span data-stu-id="b4672-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="b4672-105">これにより、ユーザーの混乱を避けることが少ないが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4672-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="b4672-106">さらに、ことができますを非表示にして、メニューまたはメニュー項目を無効にするように単独で非表示がショートカット キーを使用して、メニュー コマンドにアクセスできないユーザーを妨げません。</span><span class="sxs-lookup"><span data-stu-id="b4672-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span>  
  
### <a name="to-hide-any-menu-item-programmatically"></a><span data-ttu-id="b4672-107">メニュー項目をプログラムで非表示にするには</span><span class="sxs-lookup"><span data-stu-id="b4672-107">To hide any menu item programmatically</span></span>  
  
-   <span data-ttu-id="b4672-108">メニュー項目のプロパティを設定するメソッド内で設定するコードを追加、<xref:System.Windows.Forms.ToolStripItem.Visible%2A>プロパティを`false`です。</span><span class="sxs-lookup"><span data-stu-id="b4672-108">Within the method where you set the properties of the menu item, add code to set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>  
  
    ```vb  
    MenuItem3.Visible = False  
    ```  
  
    ```csharp  
    menuItem3.Visible = false;  
    ```  
  
    ```cpp  
    menuItem3->Visible = false;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b4672-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4672-109">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
 <xref:System.Windows.Forms.MenuStrip>  
 [<span data-ttu-id="b4672-110">MenuStrip コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="b4672-110">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="b4672-111">方法: ToolStripMenuItems を無効にする</span><span class="sxs-lookup"><span data-stu-id="b4672-111">How to: Disable ToolStripMenuItems</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md)
