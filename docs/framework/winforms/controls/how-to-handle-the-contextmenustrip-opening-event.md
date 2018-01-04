---
title: "方法 : ContextMenuStrip のオープン イベントを処理する"
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
helpviewer_keywords:
- ContextMenuStrip control [Windows Forms]
- context menus [Windows Forms], event handling
- ToolStrip control [Windows Forms]
- event handling [Windows Forms], context menus
- shortcut menus [Windows Forms], event handling
ms.assetid: b661b3dd-7815-4cc2-a1aa-a9a391ab3427
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5de244abd35c83bce329882d679df8303ef3a833
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-the-contextmenustrip-opening-event"></a><span data-ttu-id="a7a89-102">方法 : ContextMenuStrip のオープン イベントを処理する</span><span class="sxs-lookup"><span data-stu-id="a7a89-102">How to: Handle the ContextMenuStrip Opening Event</span></span>
<span data-ttu-id="a7a89-103">動作をカスタマイズすることができます、<xref:System.Windows.Forms.ContextMenuStrip>処理によって制御、<xref:System.Windows.Forms.ToolStripDropDown.Opening>イベント。</span><span class="sxs-lookup"><span data-stu-id="a7a89-103">You can customize the behavior of your <xref:System.Windows.Forms.ContextMenuStrip> control by handling the <xref:System.Windows.Forms.ToolStripDropDown.Opening> event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7a89-104">例</span><span class="sxs-lookup"><span data-stu-id="a7a89-104">Example</span></span>  
 <span data-ttu-id="a7a89-105">次のコード例は、処理する方法を示します、<xref:System.Windows.Forms.ToolStripDropDown.Opening>イベント。</span><span class="sxs-lookup"><span data-stu-id="a7a89-105">The following code example demonstrates how to handle the <xref:System.Windows.Forms.ToolStripDropDown.Opening> event.</span></span> <span data-ttu-id="a7a89-106">イベント ハンドラーが動的に項目を追加、<xref:System.Windows.Forms.ContextMenuStrip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="a7a89-106">The event handler adds items dynamically to a <xref:System.Windows.Forms.ContextMenuStrip> control.</span></span> <span data-ttu-id="a7a89-107">完全なコード例は、次を参照してください。[する方法: ToolStrip の項目を動的に追加](../../../../docs/framework/winforms/controls/how-to-add-toolstrip-items-dynamically.md)です。</span><span class="sxs-lookup"><span data-stu-id="a7a89-107">For the complete code example, see [How to: Add ToolStrip Items Dynamically](../../../../docs/framework/winforms/controls/how-to-add-toolstrip-items-dynamically.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#42)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#42)]  
  
 <span data-ttu-id="a7a89-108">設定、<xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType>プロパティを`true`して、メニューを開かないようにします。</span><span class="sxs-lookup"><span data-stu-id="a7a89-108">Set the <xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType> property to `true` to prevent the menu from opening.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7a89-109">参照</span><span class="sxs-lookup"><span data-stu-id="a7a89-109">See Also</span></span>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>  
 <xref:System.Windows.Forms.ToolStripDropDown>  
 [<span data-ttu-id="a7a89-110">ToolStrip コントロール</span><span class="sxs-lookup"><span data-stu-id="a7a89-110">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
