---
title: "方法 : デザイナーを使ってタブ ページにコントロールを追加する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TabPage control
- tab controls [Windows Forms], tab order
- tab pages [Windows Forms], adding controls
ms.assetid: 7ee734e1-e31e-4ed0-bbc0-a7e8a1f20fef
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 30c8a73d23a1a0d27f049c09752d76dd7d2d6ef2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-a-control-to-a-tab-page-using-the-designer"></a><span data-ttu-id="4284c-102">方法 : デザイナーを使ってタブ ページにコントロールを追加する</span><span class="sxs-lookup"><span data-stu-id="4284c-102">How to: Add a Control to a Tab Page Using the Designer</span></span>
<span data-ttu-id="4284c-103">Windows フォームの使用<xref:System.Windows.Forms.TabControl>組織的に他のコントロールを表示することです。</span><span class="sxs-lookup"><span data-stu-id="4284c-103">The use of the Windows Forms <xref:System.Windows.Forms.TabControl> is to display other controls in an organized fashion.</span></span> <span data-ttu-id="4284c-104">これらの手順を使用すると、タブ ページのメイン部分に画像を表示します。</span><span class="sxs-lookup"><span data-stu-id="4284c-104">You can use these instructions to display a picture on the main part of a tab page.</span></span> <span data-ttu-id="4284c-105">タブ ページのラベルの一部にアイコンを追加する方法の詳細については、次を参照してください。[する方法: Windows フォーム TabControl の外観を変更](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)です。</span><span class="sxs-lookup"><span data-stu-id="4284c-105">For information about adding an icon to the label part of a tab page, see [How to: Change the Appearance of the Windows Forms TabControl](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).</span></span>  
  
 <span data-ttu-id="4284c-106">次の手順が必要です、 **Windows アプリケーション**が含まれているフォーム プロジェクト、<xref:System.Windows.Forms.TabControl>コントロール。</span><span class="sxs-lookup"><span data-stu-id="4284c-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TabControl> control.</span></span> <span data-ttu-id="4284c-107">このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="4284c-107">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4284c-108">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="4284c-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="4284c-109">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4284c-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="4284c-110">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4284c-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-a-control-using-the-designer"></a><span data-ttu-id="4284c-111">デザイナーを使用してコントロールを追加するには</span><span class="sxs-lookup"><span data-stu-id="4284c-111">To add a control using the designer</span></span>  
  
1.  <span data-ttu-id="4284c-112">上部に表示されるように、適切なタブ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4284c-112">Click the appropriate tab page so that it appears on top.</span></span>  
  
2.  <span data-ttu-id="4284c-113">タブ ページ上のコントロールを描画します。</span><span class="sxs-lookup"><span data-stu-id="4284c-113">Draw the control on the tab page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4284c-114">参照</span><span class="sxs-lookup"><span data-stu-id="4284c-114">See Also</span></span>  
 [<span data-ttu-id="4284c-115">TabControl コントロール</span><span class="sxs-lookup"><span data-stu-id="4284c-115">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [<span data-ttu-id="4284c-116">TabControl コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="4284c-116">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="4284c-117">方法: Windows フォーム TabControl の表示形式を変更する</span><span class="sxs-lookup"><span data-stu-id="4284c-117">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)  
 [<span data-ttu-id="4284c-118">方法: タブ ページを無効化する</span><span class="sxs-lookup"><span data-stu-id="4284c-118">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [<span data-ttu-id="4284c-119">方法: Windows フォーム TabControl のタブを追加および削除する</span><span class="sxs-lookup"><span data-stu-id="4284c-119">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
