---
title: "ToolStripProgressBar コントロールの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ToolStripProgressBar
helpviewer_keywords:
- toolbars [Windows Forms], progress bars
- progress controls [Windows Forms]
- ToolStripProgressBar control [Windows Forms], about ToolStripProgressBar control
ms.assetid: ec3ab522-5fe4-4b4d-a551-bc19e84f4774
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0db69185df691fe13781e5aed96dedee239d7c9d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="toolstripprogressbar-control-overview"></a><span data-ttu-id="7ad7a-102">ToolStripProgressBar コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="7ad7a-102">ToolStripProgressBar Control Overview</span></span>
<span data-ttu-id="7ad7a-103"><xref:System.Windows.Forms.ToolStripProgressBar>ラフティングとすべての表示機能を組み合わせた<xref:System.Windows.Forms.ToolStrip>の一般的なプロセスの追跡機能を持つコントロール。</span><span class="sxs-lookup"><span data-stu-id="7ad7a-103">The <xref:System.Windows.Forms.ToolStripProgressBar> combines the rafting and rendering functionality of all <xref:System.Windows.Forms.ToolStrip> controls with its typical process-tracking functionality.</span></span> <span data-ttu-id="7ad7a-104">A<xref:System.Windows.Forms.ToolStripProgressBar>によってホストされる最も通常<xref:System.Windows.Forms.StatusStrip>、によって頻繁に小さく、<xref:System.Windows.Forms.ToolStrip>です。</span><span class="sxs-lookup"><span data-stu-id="7ad7a-104">A <xref:System.Windows.Forms.ToolStripProgressBar> is most usually hosted by <xref:System.Windows.Forms.StatusStrip>, and less frequently by a <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
 <span data-ttu-id="7ad7a-105"><xref:System.Windows.Forms.ToolStripProgressBar>置き換え、以前のバージョン コントロール機能が追加<xref:System.Windows.Forms.ToolStripProgressBar>は、必要な場合は旧バージョンとの互換性と将来の使用の両方に保持されます。</span><span class="sxs-lookup"><span data-stu-id="7ad7a-105">Although <xref:System.Windows.Forms.ToolStripProgressBar> replaces and adds functionality to the control in previous versions, <xref:System.Windows.Forms.ToolStripProgressBar> is retained for both backward compatibility and future use if desired.</span></span>  
  
### <a name="important-toolstripprogressbar-members"></a><span data-ttu-id="7ad7a-106">重要な ToolStripProgressBar メンバー</span><span class="sxs-lookup"><span data-stu-id="7ad7a-106">Important ToolStripProgressBar Members</span></span>  
  
|<span data-ttu-id="7ad7a-107">名前</span><span class="sxs-lookup"><span data-stu-id="7ad7a-107">Name</span></span>|<span data-ttu-id="7ad7a-108">説明</span><span class="sxs-lookup"><span data-stu-id="7ad7a-108">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripProgressBar.MarqueeAnimationSpeed%2A>|<span data-ttu-id="7ad7a-109">それぞれの間の遅延を表す値の設定を取得または<xref:System.Windows.Forms.ProgressBarStyle.Marquee>ミリ秒単位で更新プログラムを表示します。</span><span class="sxs-lookup"><span data-stu-id="7ad7a-109">Gets or sets a value representing the delay between each <xref:System.Windows.Forms.ProgressBarStyle.Marquee> display update, in milliseconds.</span></span>|  
|<xref:System.Windows.Forms.ProgressBar.Maximum%2A>|<span data-ttu-id="7ad7a-110">これに対して定義されている範囲の上限値の設定を取得または<xref:System.Windows.Forms.ToolStripProgressBar>です。</span><span class="sxs-lookup"><span data-stu-id="7ad7a-110">Gets or sets the upper bound of the range that is defined for this <xref:System.Windows.Forms.ToolStripProgressBar>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar.Minimum%2A>|<span data-ttu-id="7ad7a-111">これに対して定義されている範囲の下限値の設定を取得または<xref:System.Windows.Forms.ToolStripProgressBar>です。</span><span class="sxs-lookup"><span data-stu-id="7ad7a-111">Gets or sets the lower bound of the range that is defined for this <xref:System.Windows.Forms.ToolStripProgressBar>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar.Style%2A>|<span data-ttu-id="7ad7a-112">取得または設定、スタイル、<xref:System.Windows.Forms.ToolStripProgressBar>を使用して、操作の進行状況を表示します。</span><span class="sxs-lookup"><span data-stu-id="7ad7a-112">Gets or sets the style that the <xref:System.Windows.Forms.ToolStripProgressBar> uses to display the progress of an operation.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar.Value%2A>|<span data-ttu-id="7ad7a-113">取得または設定の現在の値、<xref:System.Windows.Forms.ToolStripProgressBar>です。</span><span class="sxs-lookup"><span data-stu-id="7ad7a-113">Gets or sets the current value of the <xref:System.Windows.Forms.ToolStripProgressBar>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProgressBar.PerformStep%2A>|<span data-ttu-id="7ad7a-114">進行状況バーの現在の位置を進めますの量、<xref:System.Windows.Forms.ToolStripProgressBar.Step%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="7ad7a-114">Advances the current position of the progress bar by the amount of the <xref:System.Windows.Forms.ToolStripProgressBar.Step%2A> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7ad7a-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ad7a-115">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripProgressBar>
