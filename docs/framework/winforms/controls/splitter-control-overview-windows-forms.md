---
title: "Splitter コントロールの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Splitter
helpviewer_keywords: Splitter control [Windows Forms], about Splitter control
ms.assetid: e2b6ab83-dfdd-40ec-9762-850702c82dcb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e4602796a1a7740adb9a352d0a21fb6c2a58959d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="splitter-control-overview-windows-forms"></a><span data-ttu-id="e3df7-102">Splitter コントロールの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="e3df7-102">Splitter Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="e3df7-103"><xref:System.Windows.Forms.SplitContainer>置換し、する機能を追加、<xref:System.Windows.Forms.Splitter>以前のバージョンでのコントロール<xref:System.Windows.Forms.Splitter>を選択した場合に、旧バージョンとの互換性と将来の使用の両方の保持されます。</span><span class="sxs-lookup"><span data-stu-id="e3df7-103">Although <xref:System.Windows.Forms.SplitContainer> replaces and adds functionality to the <xref:System.Windows.Forms.Splitter> control of previous versions, <xref:System.Windows.Forms.Splitter> is retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="e3df7-104">Windows フォーム<xref:System.Windows.Forms.Splitter>コントロールを使用すると、実行時にドッキングされたコントロールのサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="e3df7-104">Windows Forms <xref:System.Windows.Forms.Splitter> controls are used to resize docked controls at run time.</span></span> <span data-ttu-id="e3df7-105"><xref:System.Windows.Forms.Splitter>コントロールがフォーム上のコントロールを持つデータ ペインには、異なる時刻でさまざまな幅の情報が含まれて、Windows エクスプ ローラーのように、提示するデータのさまざまな長さでよく使用します。</span><span class="sxs-lookup"><span data-stu-id="e3df7-105">The <xref:System.Windows.Forms.Splitter> control is often used on forms with controls that have varying lengths of data to present, like Windows Explorer, whose data panes contain information of varying widths at different times.</span></span>  
  
## <a name="working-with-the-splitter-control"></a><span data-ttu-id="e3df7-106">Splitter コントロールの操作</span><span class="sxs-lookup"><span data-stu-id="e3df7-106">Working with the Splitter Control</span></span>  
 <span data-ttu-id="e3df7-107">ユーザーは、分割コントロールがサイズを変更できるコントロールのドッキングが解除されたエッジにマウス ポインターをポイント、ポインターは、コントロールのサイズを変更できることを示すために、外観を変更します。</span><span class="sxs-lookup"><span data-stu-id="e3df7-107">When the user points the mouse pointer at the undocked edge of a control that can be resized by a splitter control, the pointer changes its appearance to indicate that the control can be resized.</span></span> <span data-ttu-id="e3df7-108">分割コントロールが、ユーザーがすぐ前にあるドッキングされたコントロールをサイズ変更できます。</span><span class="sxs-lookup"><span data-stu-id="e3df7-108">With the splitter control, the user can resize the docked control that is immediately before it.</span></span> <span data-ttu-id="e3df7-109">そのため、実行時にドッキングされたコントロールのサイズを変更するユーザーを有効にするには、コントロールをコンテナーの端をサイズ変更を分割コントロールをそのコンテナーの同じ側にドッキングできます。</span><span class="sxs-lookup"><span data-stu-id="e3df7-109">Therefore, to enable the user to resize a docked control at run time, dock the control to be resized to an edge of a container, and then dock a splitter control to the same side of that container.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3df7-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="e3df7-110">See Also</span></span>  
 <xref:System.Windows.Forms.SplitContainer>  
 [<span data-ttu-id="e3df7-111">方法: Windows フォーム上のコントロールをドッキングする</span><span class="sxs-lookup"><span data-stu-id="e3df7-111">How to: Dock Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [<span data-ttu-id="e3df7-112">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="e3df7-112">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
