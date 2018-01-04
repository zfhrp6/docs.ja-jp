---
title: "ToolStripPanel コントロールの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ToolStripPanel
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms], about ToolStripPanel control
ms.assetid: ce54a60c-5eba-4b4c-bd77-cf0748a666cc
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c7976e4641f5bda02d6569ab17e7f1de139c59a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="toolstrippanel-control-overview"></a><span data-ttu-id="efc19-102">ToolStripPanel コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="efc19-102">ToolStripPanel Control Overview</span></span>
<span data-ttu-id="efc19-103">A<xref:System.Windows.Forms.ToolStripPanel>では、1 つの領域の配置とラフティング<xref:System.Windows.Forms.ToolStrip>、 <xref:System.Windows.Forms.MenuStrip>、および<xref:System.Windows.Forms.StatusStrip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="efc19-103">A <xref:System.Windows.Forms.ToolStripPanel> provides a single area for positioning and rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="efc19-104">複数<xref:System.Windows.Forms.ToolStrip>コントロールに応じて垂直または水平方向のスタック、<xref:System.Windows.Forms.ToolStripPanelRow.Orientation%2A>の<xref:System.Windows.Forms.ToolStripPanel>です。</span><span class="sxs-lookup"><span data-stu-id="efc19-104">Multiple <xref:System.Windows.Forms.ToolStrip> controls stack vertically or horizontally depending on the <xref:System.Windows.Forms.ToolStripPanelRow.Orientation%2A> of the <xref:System.Windows.Forms.ToolStripPanel>.</span></span>  
  
### <a name="important-toolstrippanel-members"></a><span data-ttu-id="efc19-105">重要な ToolStripPanel メンバー</span><span class="sxs-lookup"><span data-stu-id="efc19-105">Important ToolStripPanel Members</span></span>  
  
|<span data-ttu-id="efc19-106">name</span><span class="sxs-lookup"><span data-stu-id="efc19-106">Name</span></span>|<span data-ttu-id="efc19-107">説明</span><span class="sxs-lookup"><span data-stu-id="efc19-107">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripPanel.Orientation%2A>|<span data-ttu-id="efc19-108">取得または水平方向または垂直方向を示す値を設定、<xref:System.Windows.Forms.ToolStripPanel>です。</span><span class="sxs-lookup"><span data-stu-id="efc19-108">Gets or sets a value indicating the horizontal or vertical orientation of the <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.Renderer%2A>|<span data-ttu-id="efc19-109">取得または設定、<xref:System.Windows.Forms.ToolStripRenderer>の外観をカスタマイズするために使用する<xref:System.Windows.Forms.ToolStripPanel>です。</span><span class="sxs-lookup"><span data-stu-id="efc19-109">Gets or sets a <xref:System.Windows.Forms.ToolStripRenderer> used to customize the appearance of a <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.RenderMode%2A>|<span data-ttu-id="efc19-110">取得または設定に適用される描画スタイル、<xref:System.Windows.Forms.ToolStripPanel>です。</span><span class="sxs-lookup"><span data-stu-id="efc19-110">Gets or sets the painting styles to be applied to the <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.RowMargin%2A>|<span data-ttu-id="efc19-111">取得または設定、間隔 (ピクセル単位) 間、<xref:System.Windows.Forms.ToolStripPanelRow>と<xref:System.Windows.Forms.ToolStripPanel>です。</span><span class="sxs-lookup"><span data-stu-id="efc19-111">Gets or sets the spacing, in pixels, between the <xref:System.Windows.Forms.ToolStripPanelRow> and the <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.Rows%2A>|<span data-ttu-id="efc19-112">取得、<xref:System.Windows.Forms.ToolStripPanelRow>この<xref:System.Windows.Forms.ToolStripPanel>です。</span><span class="sxs-lookup"><span data-stu-id="efc19-112">Gets the <xref:System.Windows.Forms.ToolStripPanelRow> in this <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.Join%2A>|<span data-ttu-id="efc19-113">追加、<xref:System.Windows.Forms.ToolStrip>を<xref:System.Windows.Forms.ToolStripPanel>です。</span><span class="sxs-lookup"><span data-stu-id="efc19-113">Adds a <xref:System.Windows.Forms.ToolStrip> to a <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="efc19-114">参照</span><span class="sxs-lookup"><span data-stu-id="efc19-114">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 <xref:System.Windows.Forms.ToolStripContentPanel>  
 [<span data-ttu-id="efc19-115">ToolStrip のサンプル</span><span class="sxs-lookup"><span data-stu-id="efc19-115">ToolStrip Sample</span></span>](http://msdn.microsoft.com/en-us/b7352439-184a-4a3a-b2ad-07465d3af9ed)
