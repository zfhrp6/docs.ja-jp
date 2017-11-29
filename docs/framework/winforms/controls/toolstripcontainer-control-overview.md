---
title: "ToolStripContainer コントロールの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ToolStripContainer
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], about ToolStripContainer control
ms.assetid: c7d63bff-64e2-4a63-bd89-d31bc96dacb8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4abc783961177a55cdb81cefd21ed2d7aefb0620
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="toolstripcontainer-control-overview"></a><span data-ttu-id="0ab41-102">ToolStripContainer コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="0ab41-102">ToolStripContainer Control Overview</span></span>
<span data-ttu-id="0ab41-103">A<xref:System.Windows.Forms.ToolStripContainer>左、右、上との配置とラフティングの下側にパネル<xref:System.Windows.Forms.ToolStrip>、 <xref:System.Windows.Forms.MenuStrip>、および<xref:System.Windows.Forms.StatusStrip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="0ab41-103">A <xref:System.Windows.Forms.ToolStripContainer> has panels on its left, right, top, and bottom sides for positioning and rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="0ab41-104">複数の <xref:System.Windows.Forms.ToolStrip> コントロールを左右の <xref:System.Windows.Forms.ToolStripContainer> に配置すると、コントロールは垂直方向に積み重ねられます。</span><span class="sxs-lookup"><span data-stu-id="0ab41-104">Multiple <xref:System.Windows.Forms.ToolStrip> controls stack vertically if you put them in the left or right <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="0ab41-105">上または下の <xref:System.Windows.Forms.ToolStripContainer> に配置すると、コントロールは水平方向に積み重ねられます。</span><span class="sxs-lookup"><span data-stu-id="0ab41-105">They stack horizontally if you put them in the top or bottom <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="0ab41-106"><xref:System.Windows.Forms.ToolStripContainer> の中央の <xref:System.Windows.Forms.ToolStripContentPanel> を使用すると、従来のコントロールをフォーム上に配置できます。</span><span class="sxs-lookup"><span data-stu-id="0ab41-106">You can use the central <xref:System.Windows.Forms.ToolStripContentPanel> of the <xref:System.Windows.Forms.ToolStripContainer> to position traditional controls on the form.</span></span>  
  
 <span data-ttu-id="0ab41-107">一部または全部の <xref:System.Windows.Forms.ToolStripContainer> コントロールを、デザイン時に直接選択して削除できます。</span><span class="sxs-lookup"><span data-stu-id="0ab41-107">Any or all <xref:System.Windows.Forms.ToolStripContainer> controls are directly selectable at design time and can be deleted.</span></span> <span data-ttu-id="0ab41-108">各パネル、<xref:System.Windows.Forms.ToolStripContainer>展開および折りたたみ可能なおよびそれに含まれるコントロールのサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="0ab41-108">Each panel of a <xref:System.Windows.Forms.ToolStripContainer> is expandable and collapsible, and resizes with the controls that it contains.</span></span>  
  
### <a name="important-toolstripcontainer-members"></a><span data-ttu-id="0ab41-109">ToolStripContainer の重要なメンバー</span><span class="sxs-lookup"><span data-stu-id="0ab41-109">Important ToolStripContainer Members</span></span>  
  
|<span data-ttu-id="0ab41-110">名前</span><span class="sxs-lookup"><span data-stu-id="0ab41-110">Name</span></span>|<span data-ttu-id="0ab41-111">説明</span><span class="sxs-lookup"><span data-stu-id="0ab41-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanel%2A>|<span data-ttu-id="0ab41-112">下のパネルを取得、<xref:System.Windows.Forms.ToolStripContainer>です。</span><span class="sxs-lookup"><span data-stu-id="0ab41-112">Gets the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanelVisible%2A>|<span data-ttu-id="0ab41-113">取得または設定を示す値かどうかの下のパネル、<xref:System.Windows.Forms.ToolStripContainer>が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0ab41-113">Gets or sets a value indicating whether the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanel%2A>|<span data-ttu-id="0ab41-114">左側のパネルを取得、<xref:System.Windows.Forms.ToolStripContainer>です。</span><span class="sxs-lookup"><span data-stu-id="0ab41-114">Gets the left panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanelVisible%2A>|<span data-ttu-id="0ab41-115">取得または設定を示す値かどうかの左側のパネル、<xref:System.Windows.Forms.ToolStripContainer>が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0ab41-115">Gets or sets a value indicating whether the left panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanel%2A>|<span data-ttu-id="0ab41-116">右側のパネルを取得、<xref:System.Windows.Forms.ToolStripContainer>です。</span><span class="sxs-lookup"><span data-stu-id="0ab41-116">Gets the right panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanelVisible%2A>|<span data-ttu-id="0ab41-117">取得または設定を示す値かどうかの右側のパネル、<xref:System.Windows.Forms.ToolStripContainer>が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0ab41-117">Gets or sets a value indicating whether the right panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A>|<span data-ttu-id="0ab41-118">上のパネルを取得、<xref:System.Windows.Forms.ToolStripContainer>です。</span><span class="sxs-lookup"><span data-stu-id="0ab41-118">Gets the top panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanelVisible%2A>|<span data-ttu-id="0ab41-119">取得または設定を示す値かどうかの上のパネル、<xref:System.Windows.Forms.ToolStripContainer>が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0ab41-119">Gets or sets a value indicating whether the top panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0ab41-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ab41-120">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 <xref:System.Windows.Forms.ToolStripContentPanel>
