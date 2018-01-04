---
title: "方法 : Windows フォーム内で実行時に ToolStrip 項目を並べ替えできるようにする"
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
- ToolStrip control [Windows Forms], examples
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], rearranging controls
- ToolStrip control [Windows Forms], reordering items
ms.assetid: 8480b69a-379f-4dc2-8dcf-365ed93692b2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e295e761f9ac0ec090bf950a67008d19cb350d75
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-reordering-of-toolstrip-items-at-run-time-in-windows-forms"></a><span data-ttu-id="39425-102">方法 : Windows フォーム内で実行時に ToolStrip 項目を並べ替えできるようにする</span><span class="sxs-lookup"><span data-stu-id="39425-102">How to: Enable Reordering of ToolStrip Items at Run Time in Windows Forms</span></span>
<span data-ttu-id="39425-103">再配置するユーザーを有効にすることができます<xref:System.Windows.Forms.ToolStripItem>コントロールに対して、<xref:System.Windows.Forms.ToolStrip>です。</span><span class="sxs-lookup"><span data-stu-id="39425-103">You can enable the user to rearrange <xref:System.Windows.Forms.ToolStripItem> controls on the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-enable-toolstripitem-rearrangement-at-run-time"></a><span data-ttu-id="39425-104">実行時に ToolStripItem 再配置を有効にするには</span><span class="sxs-lookup"><span data-stu-id="39425-104">To enable ToolStripItem rearrangement at run time</span></span>  
  
-   <span data-ttu-id="39425-105"><xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="39425-105">Set the <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> property to `true`.</span></span> <span data-ttu-id="39425-106">既定では、<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>は`false`します。</span><span class="sxs-lookup"><span data-stu-id="39425-106">By default, <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> is `false`.</span></span>  
  
     <span data-ttu-id="39425-107">実行時に、ユーザーを押したまま、ALT キーを押し、マウスの左ボタンをドラッグする、<xref:System.Windows.Forms.ToolStripItem>で別の場所に、<xref:System.Windows.Forms.ToolStrip>です。</span><span class="sxs-lookup"><span data-stu-id="39425-107">At run time, the user holds down the ALT key and the left mouse button to drag a <xref:System.Windows.Forms.ToolStripItem> to a different location on the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    toolStrip1.AllowItemReorder = True  
    ```  
  
    ```csharp  
    toolStrip1.AllowItemReorder = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="39425-108">参照</span><span class="sxs-lookup"><span data-stu-id="39425-108">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>  
 [<span data-ttu-id="39425-109">ToolStrip コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="39425-109">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="39425-110">ToolStrip コントロールのアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="39425-110">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="39425-111">ToolStrip テクノロジの概要</span><span class="sxs-lookup"><span data-stu-id="39425-111">ToolStrip Technology Summary</span></span>](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
