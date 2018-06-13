---
title: '方法 : デザイナーを使用して ToolStripMenuItems を非表示にする'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
ms.openlocfilehash: b0018516b9ac337cea3716c4b2eddc6eb859dbb0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534367"
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="324ce-102">方法 : デザイナーを使用して ToolStripMenuItems を非表示にする</span><span class="sxs-lookup"><span data-stu-id="324ce-102">How to: Hide ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="324ce-103">メニュー項目を非表示には、アプリケーションのユーザー インターフェイス (UI) を制御し、ユーザーのコマンドを制限する方法です。</span><span class="sxs-lookup"><span data-stu-id="324ce-103">Hiding menu items is a way to control the user interface (UI) of your application and restrict user commands.</span></span> <span data-ttu-id="324ce-104">多くの場合、すべてのメニュー項目が利用できない場合は、メニュー全体を非表示にするされます。</span><span class="sxs-lookup"><span data-stu-id="324ce-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="324ce-105">これにより、ユーザーの混乱を避けることが少ないが表示されます。</span><span class="sxs-lookup"><span data-stu-id="324ce-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="324ce-106">さらに、ことができますを非表示にして、メニューまたはメニュー項目を無効にするように単独で非表示がショートカット キーを使用して、メニュー コマンドにアクセスできないユーザーを妨げません。</span><span class="sxs-lookup"><span data-stu-id="324ce-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span> <span data-ttu-id="324ce-107">メニュー項目を無効にする方法の詳細については、次を参照してください。[する方法: ToolStripMenuItems を無効にするデザイナーの使用](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md)です。</span><span class="sxs-lookup"><span data-stu-id="324ce-107">For more information on disabling menu items, see [How to: Disable ToolStripMenuItems Using the Designer](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="324ce-108">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="324ce-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="324ce-109">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="324ce-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="324ce-110">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="324ce-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a><span data-ttu-id="324ce-111">トップレベル メニューとサブメニュー項目を非表示にするには</span><span class="sxs-lookup"><span data-stu-id="324ce-111">To hide a top-level menu and its submenu items</span></span>  
  
1.  <span data-ttu-id="324ce-112">トップレベルのメニュー項目を選択し、設定、<xref:System.Windows.Forms.ToolStripItem.Visible%2A>または<xref:System.Windows.Forms.ToolStripItem.Available%2A>プロパティを`false`です。</span><span class="sxs-lookup"><span data-stu-id="324ce-112">Select the top-level menu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> or <xref:System.Windows.Forms.ToolStripItem.Available%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="324ce-113">トップレベルのメニュー項目を非表示にするときにそのメニュー内のすべてのメニュー項目も表示されません。</span><span class="sxs-lookup"><span data-stu-id="324ce-113">When you hide the top-level menu item, all menu items within that menu are also hidden.</span></span> <span data-ttu-id="324ce-114">クリックしてできる場所以外の場合、<xref:System.Windows.Forms.MenuStrip>設定後<xref:System.Windows.Forms.ToolStripItem.Visible%2A>に`false`、全体のトップレベル メニュー項目とサブメニュー項目の操作の実行時の効果を示すため、フォームから消失します。</span><span class="sxs-lookup"><span data-stu-id="324ce-114">If you click somewhere other than on the <xref:System.Windows.Forms.MenuStrip> after setting <xref:System.Windows.Forms.ToolStripItem.Visible%2A> to `false`, the entire top-level menu item and its submenu items disappear from your form, thus showing you the run-time effect of your action.</span></span> <span data-ttu-id="324ce-115">デザイン時に非表示のトップレベル メニュー項目を表示するのには、をクリックして、<xref:System.Windows.Forms.MenuStrip>で、**コンポーネント トレイ**の**ドキュメント アウトライン**、またはプロパティ グリッドの上部にあります。</span><span class="sxs-lookup"><span data-stu-id="324ce-115">To display the hidden top-level menu item at design time, click on the <xref:System.Windows.Forms.MenuStrip> in the **Component Tray**, in **Document Outline**, or at the top of the property grid.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="324ce-116">マージ シナリオでは複数のドキュメント インターフェイス (MDI) 子メニューを除くメニュー全体を非表示にはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="324ce-116">You will rarely hide an entire menu except for multiple document interface (MDI) child menus in a merging scenario.</span></span>  
  
### <a name="to-hide-a-submenu-item"></a><span data-ttu-id="324ce-117">サブメニュー項目を非表示にするには</span><span class="sxs-lookup"><span data-stu-id="324ce-117">To hide a submenu item</span></span>  
  
1.  <span data-ttu-id="324ce-118">サブメニュー項目を選択し、設定、<xref:System.Windows.Forms.ToolStripItem.Visible%2A>プロパティを`false`です。</span><span class="sxs-lookup"><span data-stu-id="324ce-118">Select the submenu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="324ce-119">サブメニュー項目を非表示にするときにそのまま表示されてデザイン時に、フォーム上の作業をさらに簡単に選択できるようにします。</span><span class="sxs-lookup"><span data-stu-id="324ce-119">When you hide a submenu item, it remains visible on your form at design time so that you can easily select it for further work.</span></span> <span data-ttu-id="324ce-120">実行時に実際には表示されません。</span><span class="sxs-lookup"><span data-stu-id="324ce-120">It will actually be hidden at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="324ce-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="324ce-121">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>  
 <xref:System.Windows.Forms.ToolStripItem.Available%2A>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>  
 [<span data-ttu-id="324ce-122">MenuStrip コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="324ce-122">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="324ce-123">方法: デザイナーを使用して ToolStripMenuItems を無効にする</span><span class="sxs-lookup"><span data-stu-id="324ce-123">How to: Disable ToolStripMenuItems Using the Designer</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md)
