---
title: '方法 : マウス ポインターが ToolStripItem 上にあることを検出する'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], detecting mouse movement
- ToolStrip control [Windows Forms], detecting mouse movement
- ToolStripItem class [Windows Forms], detecting mouse movement
- mouse [Windows Forms], detecting movement on toolbars
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
ms.openlocfilehash: 15a7562efd9a86a029754610ffd9e77c372d1ac2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-detect-when-the-mouse-pointer-is-over-a-toolstripitem"></a><span data-ttu-id="2e501-102">方法 : マウス ポインターが ToolStripItem 上にあることを検出する</span><span class="sxs-lookup"><span data-stu-id="2e501-102">How to: Detect When the Mouse Pointer Is Over a ToolStripItem</span></span>
<span data-ttu-id="2e501-103">マウス ポインターが上に検出するために、次の手順を使用して、<xref:System.Windows.Forms.ToolStripItem>です。</span><span class="sxs-lookup"><span data-stu-id="2e501-103">Use the following procedure to detect when the mouse pointer is over a <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-detect-when-the-pointer-is-over-a-toolstripitem"></a><span data-ttu-id="2e501-104">ポインターが ToolStripItem 上にあるときを検出するには</span><span class="sxs-lookup"><span data-stu-id="2e501-104">To detect when the pointer is over a ToolStripItem</span></span>  
  
-   <span data-ttu-id="2e501-105">使用して、<xref:System.Windows.Forms.ToolStripItem.Selected%2A>をアイテムのプロパティ<xref:System.Windows.Forms.ToolStripItem.CanSelect%2A>は`true`します。</span><span class="sxs-lookup"><span data-stu-id="2e501-105">Use the <xref:System.Windows.Forms.ToolStripItem.Selected%2A> property for items in which <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> is `true`.</span></span>  
  
     <span data-ttu-id="2e501-106">こうと、同期する必要はありません、<xref:System.Windows.Forms.ToolStripItem.MouseEnter>と<xref:System.Windows.Forms.ToolStripItem.MouseLeave>イベント。</span><span class="sxs-lookup"><span data-stu-id="2e501-106">This will prevent you from having to synchronize the <xref:System.Windows.Forms.ToolStripItem.MouseEnter> and <xref:System.Windows.Forms.ToolStripItem.MouseLeave> events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e501-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="2e501-107">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripItem.Selected%2A>  
 [<span data-ttu-id="2e501-108">ToolStrip コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="2e501-108">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
