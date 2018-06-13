---
title: '方法 : ToolStripMenuItems をコピーする'
ms.date: 03/30/2017
helpviewer_keywords:
- menu items [Windows Forms], copying and pasting
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], copying and pasting
ms.assetid: 17ef4207-e92e-4db2-b648-27246e6517ad
ms.openlocfilehash: 238516f18037a75b1d254d95086e22a970fadf09
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530482"
---
# <a name="how-to-copy-toolstripmenuitems"></a><span data-ttu-id="188fa-102">方法 : ToolStripMenuItems をコピーする</span><span class="sxs-lookup"><span data-stu-id="188fa-102">How to: Copy ToolStripMenuItems</span></span>
<span data-ttu-id="188fa-103">デザイン時に、トップレベル メニュー全体とそのサブメニュー項目を、 <xref:System.Windows.Forms.MenuStrip>の別の場所にコピーできます。</span><span class="sxs-lookup"><span data-stu-id="188fa-103">At design time, you can copy entire top-level menus and their submenu items to a different place on the <xref:System.Windows.Forms.MenuStrip>.</span></span> <span data-ttu-id="188fa-104">トップレベル メニュー間で個々のメニュー項目のコピーをすることも、またはメニュー内のメニュー項目の位置を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="188fa-104">You can also copy individual menu items between top-level menus or change the position of menu items within a menu.</span></span>  
  
### <a name="to-copy-a-top-level-menu-and-its-submenu-items-to-another-top-level-location"></a><span data-ttu-id="188fa-105">トップレベル メニューとサブメニュー項目を別のトップレベルの場所にコピーするには</span><span class="sxs-lookup"><span data-stu-id="188fa-105">To copy a top-level menu and its submenu items to another top-level location</span></span>  
  
1.  <span data-ttu-id="188fa-106">コピーするメニューを左クリックして、Ctrl + C キーを押します。または、メニューを右クリックして、ショートカット メニューから **[コピー]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="188fa-106">Left-click the menu that you want to copy and press CTRL+C, or right-click the menu and select **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="188fa-107">移動先となる新しい場所の後ろにあるトップレベル メニューを左クリックし、Ctrl + V キーを押します。または、移動先となる新しい場所の前にあるトップレベル メニュー項目を右クリックし、ショートカット メニューから **[貼り付け]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="188fa-107">Left-click the top-level menu that is after the intended new location and press CTRL+V, or right-click the top-level menu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="188fa-108">選んだトップレベル メニューの前に、コピーしたメニューが挿入されます。</span><span class="sxs-lookup"><span data-stu-id="188fa-108">The menu that you copied is inserted before the selected top-level menu.</span></span>  
  
### <a name="to-copy-a-top-level-menu-and-its-submenu-items-to-a-drop-down-location"></a><span data-ttu-id="188fa-109">トップレベル メニューとサブメニュー項目をドロップダウンの場所にコピーするには</span><span class="sxs-lookup"><span data-stu-id="188fa-109">To copy a top-level menu and its submenu items to a drop-down location</span></span>  
  
1.  <span data-ttu-id="188fa-110">移動するメニューを左クリックして、Ctrl + C キーを押します。または、メニューを右クリックして、ショートカット メニューから **[コピー]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="188fa-110">Left-click the menu that you want to move and press CTRL+C, or right-click the menu and select **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="188fa-111">宛先のトップレベル メニューで、移動先となる新しい場所の上にあるサブメニュー項目を左クリックし、Ctrl + V キーを押します。または、移動先となる新しい場所の上にあるサブメニュー項目を右クリックし、ショートカット メニューから **[貼り付け]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="188fa-111">In the destination top-level menu, left-click the submenu item that is above the intended new location and press CTRL+V, or right-click the submenu item that is above the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="188fa-112">選んだサブメニュー項目の前に、コピーしたメニューが挿入されます。</span><span class="sxs-lookup"><span data-stu-id="188fa-112">The menu that you copied is inserted before the selected submenu item.</span></span>  
  
### <a name="to-copy-a-submenu-item-to-another-menu"></a><span data-ttu-id="188fa-113">別のメニューにサブメニュー項目をコピーするには</span><span class="sxs-lookup"><span data-stu-id="188fa-113">To copy a submenu item to another menu</span></span>  
  
1.  <span data-ttu-id="188fa-114">コピーするサブメニュー項目を左クリックして、Ctrl + C キーを押します。または、サブメニュー項目を右クリックして、ショートカット メニューから **[コピー]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="188fa-114">Left-click the submenu item that you want to copy and press CTRL+C, or right-click the submenu item and choose **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="188fa-115">切り取ったサブメニュー項目を格納するメニューを左クリックします。</span><span class="sxs-lookup"><span data-stu-id="188fa-115">Left-click the menu that will contain the submenu item that you cut.</span></span>  
  
3.  <span data-ttu-id="188fa-116">移動先となる新しい場所の前にあるサブメニュー項目を左クリックし、Ctrl + V キーを押します。または、移動先となる新しい場所の前にあるサブメニュー項目を右クリックし、ショートカット メニューから **[貼り付け]** を選びます。</span><span class="sxs-lookup"><span data-stu-id="188fa-116">Left-click the submenu item that is before the intended new location and press CTRL+V, or right-click the submenu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="188fa-117">選んだサブメニュー項目の前に、コピーしたサブメニュー項目が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="188fa-117">The submenu item that you copied is inserted before the selected submenu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="188fa-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="188fa-118">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="188fa-119">MenuStrip コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="188fa-119">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
