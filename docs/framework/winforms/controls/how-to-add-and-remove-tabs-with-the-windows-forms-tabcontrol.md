---
title: "方法 : Windows フォーム TabControl のタブを追加および削除する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tabs [Windows Forms], removing from pages
- TabPage control
- TabControl control [Windows Forms], adding and removing tabs
- tabs [Windows Forms], adding to pages
- tab pages
ms.assetid: 66d4dfca-41e8-44e3-9c80-fb7ac4cb1619
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7df8b785b2c05acbbec9c17e12e462d755d0cd3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol"></a><span data-ttu-id="45b30-102">方法 : Windows フォーム TabControl のタブを追加および削除する</span><span class="sxs-lookup"><span data-stu-id="45b30-102">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>
<span data-ttu-id="45b30-103">既定では、<xref:System.Windows.Forms.TabControl>コントロールでは、2 つ含まれている<xref:System.Windows.Forms.TabPage>コントロール。</span><span class="sxs-lookup"><span data-stu-id="45b30-103">By default, a <xref:System.Windows.Forms.TabControl> control contains two <xref:System.Windows.Forms.TabPage> controls.</span></span> <span data-ttu-id="45b30-104">これらのタブを通じてアクセスできる、<xref:System.Windows.Forms.TabControl.TabPages%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="45b30-104">You can access these tabs through the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
### <a name="to-add-a-tab-programmatically"></a><span data-ttu-id="45b30-105">プログラムを追加するタブ</span><span class="sxs-lookup"><span data-stu-id="45b30-105">To add a tab programmatically</span></span>  
  
-   <span data-ttu-id="45b30-106">使用して、<xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A>のメソッド、<xref:System.Windows.Forms.TabControl.TabPages%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="45b30-106">Use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
    ```vb  
    Dim myTabPage As New TabPage()  
    myTabPage.Text = "TabPage" & (TabControl1.TabPages.Count + 1)  
    TabControl1.TabPages.Add(myTabPage)  
    ```  
  
    ```csharp  
    string title = "TabPage " + (tabControl1.TabCount + 1).ToString();  
    TabPage myTabPage = new TabPage(title);  
    tabControl1.TabPages.Add(myTabPage);  
    ```  
  
    ```cpp  
    String^ title = String::Concat("TabPage ",  
       (tabControl1->TabCount + 1).ToString());  
    TabPage^ myTabPage = gcnew TabPage(title);  
    tabControl1->TabPages->Add(myTabPage);  
    ```  
  
### <a name="to-remove-a-tab-programmatically"></a><span data-ttu-id="45b30-107">プログラムで、タブを削除するには</span><span class="sxs-lookup"><span data-stu-id="45b30-107">To remove a tab programmatically</span></span>  
  
-   <span data-ttu-id="45b30-108">削除するには選択したタブを使用して、<xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A>のメソッド、<xref:System.Windows.Forms.TabControl.TabPages%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="45b30-108">To remove selected tabs, use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
     <span data-ttu-id="45b30-109">または</span><span class="sxs-lookup"><span data-stu-id="45b30-109">-or-</span></span>  
  
-   <span data-ttu-id="45b30-110">削除するにはすべてのタブを使用して、<xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A>のメソッド、<xref:System.Windows.Forms.TabControl.TabPages%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="45b30-110">To remove all tabs, use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
    ```vb  
    ' Removes the selected tab:  
    TabControl1.TabPages.Remove(TabControl1.SelectedTab)  
    ' Removes all the tabs:  
    TabControl1.TabPages.Clear()  
    ```  
  
    ```csharp  
    // Removes the selected tab:  
    tabControl1.TabPages.Remove(tabControl1.SelectedTab);  
    // Removes all the tabs:  
    tabControl1.TabPages.Clear();  
    ```  
  
    ```cpp  
    // Removes the selected tab:  
    tabControl1->TabPages->Remove(tabControl1->SelectedTab);  
    // Removes all the tabs:  
    tabControl1->TabPages->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="45b30-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="45b30-111">See Also</span></span>  
 [<span data-ttu-id="45b30-112">TabControl コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="45b30-112">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="45b30-113">方法: タブ ページにコントロールを追加する</span><span class="sxs-lookup"><span data-stu-id="45b30-113">How to: Add a Control to a Tab Page</span></span>](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [<span data-ttu-id="45b30-114">方法: タブ ページを無効化する</span><span class="sxs-lookup"><span data-stu-id="45b30-114">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [<span data-ttu-id="45b30-115">方法: Windows フォーム TabControl の表示形式を変更する</span><span class="sxs-lookup"><span data-stu-id="45b30-115">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
