---
title: "方法 : ToolStripMenuItems を移動する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], moving
- menus [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], dragging and dropping
- menu items [Windows Forms], moving
- menu items [Windows Forms], cutting and pasting
- menu items [Windows Forms], dragging and dropping
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], cutting and pasting
ms.assetid: cab9e03e-4edd-4c25-b3e3-bd1edc602bd9
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfc1cb718b3738ac93b284b0b438b08d1e721349
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-move-toolstripmenuitems"></a><span data-ttu-id="7a7ec-102">方法 : ToolStripMenuItems を移動する</span><span class="sxs-lookup"><span data-stu-id="7a7ec-102">How to: Move ToolStripMenuItems</span></span>
<span data-ttu-id="7a7ec-103">デザイン時に行うことができますトップレベル メニュー全体とそのメニュー項目を別の場所、<xref:System.Windows.Forms.MenuStrip>です。</span><span class="sxs-lookup"><span data-stu-id="7a7ec-103">At design time, you can move entire top-level menus and their menu items to a different place on the <xref:System.Windows.Forms.MenuStrip>.</span></span> <span data-ttu-id="7a7ec-104">トップレベル メニュー間で個々 のメニュー項目を移動したり、メニュー内のメニュー項目の位置を変更できます。</span><span class="sxs-lookup"><span data-stu-id="7a7ec-104">You can also move individual menu items between top-level menus or change the position of menu items within a menu.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a7ec-105">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7a7ec-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7a7ec-106">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a7ec-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7a7ec-107">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a7ec-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a><span data-ttu-id="7a7ec-108">トップレベル メニューとそのメニュー項目を最上位レベルの別の場所に移動するには</span><span class="sxs-lookup"><span data-stu-id="7a7ec-108">To move a top-level menu and its menu items to another top-level location</span></span>  
  
1.  <span data-ttu-id="7a7ec-109">クリックして、移動するメニューにマウスの左ボタンを押したままにします。</span><span class="sxs-lookup"><span data-stu-id="7a7ec-109">Click and hold down the left mouse button on the menu that you want to move.</span></span>  
  
2.  <span data-ttu-id="7a7ec-110">前となる新しい場所にあるトップレベルのメニューにカーソルをドラッグし、マウスの左ボタンを離します。</span><span class="sxs-lookup"><span data-stu-id="7a7ec-110">Drag the insertion point to the top-level menu that is before the intended new location and release the left mouse button.</span></span>  
  
     <span data-ttu-id="7a7ec-111">選択されたメニューは、カーソルの右側に移動します。</span><span class="sxs-lookup"><span data-stu-id="7a7ec-111">The selected menu moves to the right of the insertion point.</span></span>  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a><span data-ttu-id="7a7ec-112">トップレベル メニューとそのメニュー項目をドロップダウンの場所に移動するには</span><span class="sxs-lookup"><span data-stu-id="7a7ec-112">To move a top-level menu and its menu items to a drop-down location</span></span>  
  
1.  <span data-ttu-id="7a7ec-113">移動、ctrl キーを押しながら X キーを押すかメニューを右クリックして、選択するメニューを左クリックして**切り取り**ショートカット メニューからです。</span><span class="sxs-lookup"><span data-stu-id="7a7ec-113">Left-click the menu that you want to move and press CTRL+X, or right-click the menu and select **Cut** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="7a7ec-114">宛先のトップレベル メニューで、メニュー項目となる新しい場所の上をクリックして、ctrl キーを押しながら V キーを押しますまたはとなる新しい場所の上のメニュー項目を右クリックし、選択**貼り付け**ショートカット メニューからです。</span><span class="sxs-lookup"><span data-stu-id="7a7ec-114">In the destination top-level menu, left-click the menu item above the intended new location and press CTRL+V, or right-click the menu item above the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="7a7ec-115">切り取ったメニューは、選択されたメニュー項目の後に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="7a7ec-115">The menu that you cut is inserted after the selected menu item.</span></span>  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a><span data-ttu-id="7a7ec-116">Items コレクション エディターを使用してメニュー内のメニュー項目を移動するには</span><span class="sxs-lookup"><span data-stu-id="7a7ec-116">To move a menu item within a menu using the Items Collection Editor</span></span>  
  
1.  <span data-ttu-id="7a7ec-117">移動するメニュー項目が含まれているメニューを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="7a7ec-117">Right-click the menu that contains the menu item you want to move.</span></span>  
  
2.  <span data-ttu-id="7a7ec-118">ショートカット メニューから選択**ドロップダウン項目の編集**です。</span><span class="sxs-lookup"><span data-stu-id="7a7ec-118">From the shortcut menu, choose **Edit DropDownItems**.</span></span>  
  
3.  <span data-ttu-id="7a7ec-119">**Items コレクション エディター**に移動するメニュー項目を左クリックします。</span><span class="sxs-lookup"><span data-stu-id="7a7ec-119">In the **Items Collection Editor**, left-click the menu item you want to move.</span></span>  
  
4.  <span data-ttu-id="7a7ec-120">メニュー内のメニュー項目を移動する上下矢印キーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a7ec-120">Click the UP and DOWN ARROW keys to move the menu item within the menu.</span></span>  
  
5.  <span data-ttu-id="7a7ec-121">**[OK]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a7ec-121">Click **OK**.</span></span>  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a><span data-ttu-id="7a7ec-122">キーボードを使用してメニュー内のメニュー項目を移動するには</span><span class="sxs-lookup"><span data-stu-id="7a7ec-122">To move a menu item within a menu using the keyboard</span></span>  
  
1.  <span data-ttu-id="7a7ec-123">キーを押して、ALT キーを押したままにします。</span><span class="sxs-lookup"><span data-stu-id="7a7ec-123">Press and hold down the ALT key.</span></span>  
  
2.  <span data-ttu-id="7a7ec-124">移動するメニュー項目をマウスの左ボタンを押したままにします。</span><span class="sxs-lookup"><span data-stu-id="7a7ec-124">Click and hold the left mouse button on the menu item that you want to move.</span></span>  
  
3.  <span data-ttu-id="7a7ec-125">メニュー項目を新しい場所にドラッグし、マウスの左ボタンを離します。</span><span class="sxs-lookup"><span data-stu-id="7a7ec-125">Drag the menu item to the new location and release the left mouse button.</span></span>  
  
### <a name="to-move-a-menu-item-to-another-menu"></a><span data-ttu-id="7a7ec-126">別のメニューにメニュー項目を移動するには</span><span class="sxs-lookup"><span data-stu-id="7a7ec-126">To move a menu item to another menu</span></span>  
  
1.  <span data-ttu-id="7a7ec-127">移動および ctrl キーを押しながら X キーを押しますまたはメニュー項目を右クリックしを選択するメニュー項目を左クリックして**切り取り**ショートカット メニューからです。</span><span class="sxs-lookup"><span data-stu-id="7a7ec-127">Left-click the menu item that you want to move and press CTRL+X, or right-click the menu item and choose **Cut** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="7a7ec-128">メニュー項目を格納するメニューをクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="7a7ec-128">Left-click the menu that will contain the menu item that you cut.</span></span>  
  
3.  <span data-ttu-id="7a7ec-129">前となる新しい場所にあるメニュー項目を左クリックし、ctrl キーを押しながら V キーを押してまたはメニュー項目となる新しい場所を選択する前にを右クリックして**貼り付け**ショートカット メニューからです。</span><span class="sxs-lookup"><span data-stu-id="7a7ec-129">Left-click the menu item that is before the intended new location and press CTRL+V, or right-click the menu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="7a7ec-130">切り取りするメニュー項目が選択されたメニュー項目の後に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="7a7ec-130">The menu item that you cut is inserted after the selected menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a7ec-131">参照</span><span class="sxs-lookup"><span data-stu-id="7a7ec-131">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="7a7ec-132">MenuStrip コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="7a7ec-132">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
