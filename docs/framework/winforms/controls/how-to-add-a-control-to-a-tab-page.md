---
title: '方法 : タブ ページにコントロールを追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TabPage control
- tab controls [Windows Forms], tab order
- tab pages [Windows Forms], adding controls
ms.assetid: b092532e-7346-469f-b9a1-897f9bea4fb7
ms.openlocfilehash: 1bb2233cf9e288ae89ebb8cab3df4f6451dc8eed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526697"
---
# <a name="how-to-add-a-control-to-a-tab-page"></a><span data-ttu-id="6dfc6-102">方法 : タブ ページにコントロールを追加する</span><span class="sxs-lookup"><span data-stu-id="6dfc6-102">How to: Add a Control to a Tab Page</span></span>
<span data-ttu-id="6dfc6-103">Windows フォームを使用することができます<xref:System.Windows.Forms.TabControl>を組織的に他のコントロールを表示します。</span><span class="sxs-lookup"><span data-stu-id="6dfc6-103">You can use the Windows Forms <xref:System.Windows.Forms.TabControl> to display other controls in an organized fashion.</span></span> <span data-ttu-id="6dfc6-104">次の手順では、最初のタブにボタンを追加する方法を示します。タブ ページのラベルの一部にアイコンを追加する方法の詳細については、次を参照してください。[する方法: Windows フォーム TabControl の外観を変更](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)です。</span><span class="sxs-lookup"><span data-stu-id="6dfc6-104">The following procedure shows how to add a button to the first tab. For information about adding an icon to the label part of a tab page, see [How to: Change the Appearance of the Windows Forms TabControl](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).</span></span>  
  
### <a name="to-add-a-control-programmatically"></a><span data-ttu-id="6dfc6-105">コントロールをプログラムで追加するには</span><span class="sxs-lookup"><span data-stu-id="6dfc6-105">To add a control programmatically</span></span>  
  
1.  <span data-ttu-id="6dfc6-106">使用して、<xref:System.Windows.Forms.Control.ControlCollection.Add%2A>メソッドによって返されるコレクションの<xref:System.Windows.Forms.Control.Controls%2A>プロパティ<xref:System.Windows.Forms.TabPage>:</span><span class="sxs-lookup"><span data-stu-id="6dfc6-106">Use the <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> method of the collection returned by the <xref:System.Windows.Forms.Control.Controls%2A> property of <xref:System.Windows.Forms.TabPage>:</span></span>  
  
     [!code-cpp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cpp/add.cpp#1)]
     [!code-csharp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cs/add.cs#1)]
     [!code-vb[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/vb/add.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6dfc6-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="6dfc6-107">See Also</span></span>  
 [<span data-ttu-id="6dfc6-108">TabControl コントロール</span><span class="sxs-lookup"><span data-stu-id="6dfc6-108">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [<span data-ttu-id="6dfc6-109">TabControl コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="6dfc6-109">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="6dfc6-110">方法: Windows フォーム TabControl の表示形式を変更する</span><span class="sxs-lookup"><span data-stu-id="6dfc6-110">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)  
 [<span data-ttu-id="6dfc6-111">方法: タブ ページを無効化する</span><span class="sxs-lookup"><span data-stu-id="6dfc6-111">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [<span data-ttu-id="6dfc6-112">方法: Windows フォーム TabControl のタブを追加および削除する</span><span class="sxs-lookup"><span data-stu-id="6dfc6-112">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
