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
ms.workload: dotnet
ms.openlocfilehash: 3a1a4c9c77e1f347f95c0a5e17ab0d37e0013d6b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="toolstripcontainer-control-overview"></a><span data-ttu-id="4f91c-102">ToolStripContainer コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="4f91c-102">ToolStripContainer Control Overview</span></span>
<span data-ttu-id="4f91c-103">A<xref:System.Windows.Forms.ToolStripContainer>左、右、上との配置とラフティングの下側にパネル<xref:System.Windows.Forms.ToolStrip>、 <xref:System.Windows.Forms.MenuStrip>、および<xref:System.Windows.Forms.StatusStrip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="4f91c-103">A <xref:System.Windows.Forms.ToolStripContainer> has panels on its left, right, top, and bottom sides for positioning and rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="4f91c-104">複数の <xref:System.Windows.Forms.ToolStrip> コントロールを左右の <xref:System.Windows.Forms.ToolStripContainer> に配置すると、コントロールは垂直方向に積み重ねられます。</span><span class="sxs-lookup"><span data-stu-id="4f91c-104">Multiple <xref:System.Windows.Forms.ToolStrip> controls stack vertically if you put them in the left or right <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="4f91c-105">上または下の <xref:System.Windows.Forms.ToolStripContainer> に配置すると、コントロールは水平方向に積み重ねられます。</span><span class="sxs-lookup"><span data-stu-id="4f91c-105">They stack horizontally if you put them in the top or bottom <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="4f91c-106"><xref:System.Windows.Forms.ToolStripContainer> の中央の <xref:System.Windows.Forms.ToolStripContentPanel> を使用すると、従来のコントロールをフォーム上に配置できます。</span><span class="sxs-lookup"><span data-stu-id="4f91c-106">You can use the central <xref:System.Windows.Forms.ToolStripContentPanel> of the <xref:System.Windows.Forms.ToolStripContainer> to position traditional controls on the form.</span></span>  
  
 <span data-ttu-id="4f91c-107">一部または全部の <xref:System.Windows.Forms.ToolStripContainer> コントロールを、デザイン時に直接選択して削除できます。</span><span class="sxs-lookup"><span data-stu-id="4f91c-107">Any or all <xref:System.Windows.Forms.ToolStripContainer> controls are directly selectable at design time and can be deleted.</span></span> <span data-ttu-id="4f91c-108">各パネル、<xref:System.Windows.Forms.ToolStripContainer>展開および折りたたみ可能なおよびそれに含まれるコントロールのサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="4f91c-108">Each panel of a <xref:System.Windows.Forms.ToolStripContainer> is expandable and collapsible, and resizes with the controls that it contains.</span></span>  
  
### <a name="important-toolstripcontainer-members"></a><span data-ttu-id="4f91c-109">ToolStripContainer の重要なメンバー</span><span class="sxs-lookup"><span data-stu-id="4f91c-109">Important ToolStripContainer Members</span></span>  
  
|<span data-ttu-id="4f91c-110">name</span><span class="sxs-lookup"><span data-stu-id="4f91c-110">Name</span></span>|<span data-ttu-id="4f91c-111">説明</span><span class="sxs-lookup"><span data-stu-id="4f91c-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanel%2A>|<span data-ttu-id="4f91c-112">下のパネルを取得、<xref:System.Windows.Forms.ToolStripContainer>です。</span><span class="sxs-lookup"><span data-stu-id="4f91c-112">Gets the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanelVisible%2A>|<span data-ttu-id="4f91c-113">取得または設定を示す値かどうかの下のパネル、<xref:System.Windows.Forms.ToolStripContainer>が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f91c-113">Gets or sets a value indicating whether the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanel%2A>|<span data-ttu-id="4f91c-114">左側のパネルを取得、<xref:System.Windows.Forms.ToolStripContainer>です。</span><span class="sxs-lookup"><span data-stu-id="4f91c-114">Gets the left panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanelVisible%2A>|<span data-ttu-id="4f91c-115">取得または設定を示す値かどうかの左側のパネル、<xref:System.Windows.Forms.ToolStripContainer>が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f91c-115">Gets or sets a value indicating whether the left panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanel%2A>|<span data-ttu-id="4f91c-116">右側のパネルを取得、<xref:System.Windows.Forms.ToolStripContainer>です。</span><span class="sxs-lookup"><span data-stu-id="4f91c-116">Gets the right panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanelVisible%2A>|<span data-ttu-id="4f91c-117">取得または設定を示す値かどうかの右側のパネル、<xref:System.Windows.Forms.ToolStripContainer>が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f91c-117">Gets or sets a value indicating whether the right panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A>|<span data-ttu-id="4f91c-118">上のパネルを取得、<xref:System.Windows.Forms.ToolStripContainer>です。</span><span class="sxs-lookup"><span data-stu-id="4f91c-118">Gets the top panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanelVisible%2A>|<span data-ttu-id="4f91c-119">取得または設定を示す値かどうかの上のパネル、<xref:System.Windows.Forms.ToolStripContainer>が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f91c-119">Gets or sets a value indicating whether the top panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4f91c-120">参照</span><span class="sxs-lookup"><span data-stu-id="4f91c-120">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 <xref:System.Windows.Forms.ToolStripContentPanel>
