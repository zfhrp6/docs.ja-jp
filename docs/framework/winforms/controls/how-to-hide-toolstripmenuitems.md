---
title: "方法 : ToolStripMenuItems を非表示にする"
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
- ToolStripMenuItems [Windows Forms], hiding
- MenuStrip control [Windows Forms], hiding menu items
- menus [Windows Forms], hiding menu items
- menu items [Windows Forms], hiding
- hiding menu items
ms.assetid: 418a768f-808a-44cd-8cef-f4e161883621
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f5491cfbfc312b2ce3e35170ddc4edc8ee39a61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hide-toolstripmenuitems"></a><span data-ttu-id="1a077-102">方法 : ToolStripMenuItems を非表示にする</span><span class="sxs-lookup"><span data-stu-id="1a077-102">How to: Hide ToolStripMenuItems</span></span>
<span data-ttu-id="1a077-103">メニュー項目を非表示には、アプリケーションのユーザー インターフェイスを制御し、ユーザーのコマンドを制限する方法です。</span><span class="sxs-lookup"><span data-stu-id="1a077-103">Hiding menu items is a way to control the user interface of your application and restrict user commands.</span></span> <span data-ttu-id="1a077-104">多くの場合、すべてのメニュー項目が利用できない場合は、メニュー全体を非表示にするされます。</span><span class="sxs-lookup"><span data-stu-id="1a077-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="1a077-105">これにより、ユーザーの混乱を避けることが少ないが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1a077-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="1a077-106">さらに、ことができますを非表示にして、メニューまたはメニュー項目を無効にするように単独で非表示がショートカット キーを使用して、メニュー コマンドにアクセスできないユーザーを妨げません。</span><span class="sxs-lookup"><span data-stu-id="1a077-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span>  
  
### <a name="to-hide-any-menu-item-programmatically"></a><span data-ttu-id="1a077-107">メニュー項目をプログラムで非表示にするには</span><span class="sxs-lookup"><span data-stu-id="1a077-107">To hide any menu item programmatically</span></span>  
  
-   <span data-ttu-id="1a077-108">メニュー項目のプロパティを設定するメソッド内で設定するコードを追加、<xref:System.Windows.Forms.ToolStripItem.Visible%2A>プロパティを`false`です。</span><span class="sxs-lookup"><span data-stu-id="1a077-108">Within the method where you set the properties of the menu item, add code to set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>  
  
    ```vb  
    MenuItem3.Visible = False  
    ```  
  
    ```csharp  
    menuItem3.Visible = false;  
    ```  
  
    ```cpp  
    menuItem3->Visible = false;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1a077-109">参照</span><span class="sxs-lookup"><span data-stu-id="1a077-109">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
 <xref:System.Windows.Forms.MenuStrip>  
 [<span data-ttu-id="1a077-110">MenuStrip コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="1a077-110">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="1a077-111">方法: ToolStripMenuItems を無効にする</span><span class="sxs-lookup"><span data-stu-id="1a077-111">How to: Disable ToolStripMenuItems</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md)
