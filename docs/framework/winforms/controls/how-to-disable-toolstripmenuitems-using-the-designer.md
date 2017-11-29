---
title: "方法 : デザイナーを使用して ToolStripMenuItems を無効にする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4958f315ff0415c3964d22dffff2553c0901eb91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="aff7b-102">方法 : デザイナーを使用して ToolStripMenuItems を無効にする</span><span class="sxs-lookup"><span data-stu-id="aff7b-102">How to: Disable ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="aff7b-103">制限またはを有効にして、ユーザー アクティビティを応答でのメニュー項目を無効にすると、ユーザーが実行できるコマンドの範囲を広げることができます。</span><span class="sxs-lookup"><span data-stu-id="aff7b-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="aff7b-104">メニュー項目は既定で有効には、作成されるが、これで調整できる場合に、<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="aff7b-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="aff7b-105">デザイン時にこのプロパティを操作することができます、**プロパティ**ウィンドウまたはプログラムによってコードで設定します。</span><span class="sxs-lookup"><span data-stu-id="aff7b-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span> <span data-ttu-id="aff7b-106">詳細については、次を参照してください。[する方法: ToolStripMenuItems を無効にする](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md)です。</span><span class="sxs-lookup"><span data-stu-id="aff7b-106">For more information, see [How to: Disable ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aff7b-107">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="aff7b-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="aff7b-108">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="aff7b-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="aff7b-109">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aff7b-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-disable-a-menu-item-at-design-time"></a><span data-ttu-id="aff7b-110">デザイン時にメニュー項目を無効にするには</span><span class="sxs-lookup"><span data-stu-id="aff7b-110">To disable a menu item at design time</span></span>  
  
1.  <span data-ttu-id="aff7b-111">フォームで選択されたメニュー項目を含む設定、<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>プロパティを`false`です。</span><span class="sxs-lookup"><span data-stu-id="aff7b-111">With the menu item selected on the form, set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="aff7b-112">メニューの最初または最上位レベルのメニュー項目を無効にするには、メニュー内に含まれるすべてのメニュー項目が無効にします。</span><span class="sxs-lookup"><span data-stu-id="aff7b-112">Disabling the first or top-level menu item in a menu disables all the menu items contained within the menu.</span></span> <span data-ttu-id="aff7b-113">同様に、サブメニュー項目を持つメニュー項目を無効にするには、サブメニュー項目が無効にします。</span><span class="sxs-lookup"><span data-stu-id="aff7b-113">Likewise, disabling a menu item that has submenu items disables the submenu items.</span></span> <span data-ttu-id="aff7b-114">指定されたメニュー上のすべてのコマンドがユーザーに利用可能な場合は、この場合は、クリーンなユーザー インターフェイスとして両方を非表示にし、メニュー全体を無効にすることをお勧めプログラミングと見なされます。</span><span class="sxs-lookup"><span data-stu-id="aff7b-114">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="aff7b-115">非表示にする必要があり、無効にします] メニューの [非表示にするだけでは、ショートカット キーを使用してメニュー コマンドにアクセスを妨げません。</span><span class="sxs-lookup"><span data-stu-id="aff7b-115">You should both hide and disable the menu, as hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="aff7b-116">設定、<xref:System.Windows.Forms.ToolStripItem.Visible%2A>をトップレベルのメニュー項目のプロパティ`false`メニュー全体を非表示にします。</span><span class="sxs-lookup"><span data-stu-id="aff7b-116">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aff7b-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="aff7b-117">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="aff7b-118">方法: ToolStripMenuItems を非表示にする</span><span class="sxs-lookup"><span data-stu-id="aff7b-118">How to: Hide ToolStripMenuItems</span></span>](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)  
 [<span data-ttu-id="aff7b-119">MenuStrip コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="aff7b-119">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
