---
title: "方法 : デザイナーで Windows フォーム TabControl を使ってタブを追加および削除する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tabs [Windows Forms], removing from pages
- TabPage control
- TabPage control [Windows Forms], adding and removing tabs
- tabs [Windows Forms], adding to pages
- tab pages
ms.assetid: 480633db-413a-45d2-9c8f-0427cc13adbe
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 666cade349220e9975a5770328e03db0e948d7d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol-using-the-designer"></a><span data-ttu-id="f3992-102">方法 : デザイナーで Windows フォーム TabControl を使ってタブを追加および削除する</span><span class="sxs-lookup"><span data-stu-id="f3992-102">How to: Add and Remove Tabs with the Windows Forms TabControl Using the Designer</span></span>
<span data-ttu-id="f3992-103">配置するとき、<xref:System.Windows.Forms.TabControl>コントロール フォームで、既定では 2 つのタブがあります。</span><span class="sxs-lookup"><span data-stu-id="f3992-103">When you place a <xref:System.Windows.Forms.TabControl> control on your form, it contains two tabs by default.</span></span> <span data-ttu-id="f3992-104">追加するか、デザイナーを使用してタブを削除します。</span><span class="sxs-lookup"><span data-stu-id="f3992-104">You can add or remove tabs using the designer.</span></span>  
  
 <span data-ttu-id="f3992-105">次の手順が必要です、 **Windows アプリケーション**が含まれているフォーム プロジェクト、<xref:System.Windows.Forms.TabControl>コントロール。</span><span class="sxs-lookup"><span data-stu-id="f3992-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TabControl> control.</span></span> <span data-ttu-id="f3992-106">このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="f3992-106">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3992-107">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f3992-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="f3992-108">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3992-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="f3992-109">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3992-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-or-remove-a-tab-using-the-designer"></a><span data-ttu-id="f3992-110">追加またはデザイナーを使用して、タブを削除するには</span><span class="sxs-lookup"><span data-stu-id="f3992-110">To add or remove a tab using the designer</span></span>  
  
-   <span data-ttu-id="f3992-111">コントロールのスマート タグでは、をクリックして**タブの追加**または**タブの削除**</span><span class="sxs-lookup"><span data-stu-id="f3992-111">On the control's smart tag, click **Add Tab** or **Remove Tab**</span></span>  
  
     <span data-ttu-id="f3992-112">- または -</span><span class="sxs-lookup"><span data-stu-id="f3992-112">-or-</span></span>  
  
     <span data-ttu-id="f3992-113">**プロパティ**ウィンドウで、をクリックして、**省略記号**ボタン (![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) の横に<xref:System.Windows.Forms.TabControl.TabPages%2A>プロパティを開くには、 **TabPage コレクション エディター**です。</span><span class="sxs-lookup"><span data-stu-id="f3992-113">In the **Properties** window, click the **Ellipsis** button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.TabControl.TabPages%2A> property to open the **TabPage Collection Editor**.</span></span> <span data-ttu-id="f3992-114">クリックして、**追加**または**削除**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f3992-114">Click the **Add** or **Remove** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3992-115">参照</span><span class="sxs-lookup"><span data-stu-id="f3992-115">See Also</span></span>  
 [<span data-ttu-id="f3992-116">TabControl コントロール</span><span class="sxs-lookup"><span data-stu-id="f3992-116">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [<span data-ttu-id="f3992-117">TabControl コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="f3992-117">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="f3992-118">方法: タブ ページにコントロールを追加する</span><span class="sxs-lookup"><span data-stu-id="f3992-118">How to: Add a Control to a Tab Page</span></span>](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [<span data-ttu-id="f3992-119">方法: タブ ページを無効化する</span><span class="sxs-lookup"><span data-stu-id="f3992-119">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [<span data-ttu-id="f3992-120">方法: Windows フォーム TabControl の表示形式を変更する</span><span class="sxs-lookup"><span data-stu-id="f3992-120">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
