---
title: "ProgressBar コントロールの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ProgressBar
helpviewer_keywords:
- ProgressBar control [Windows Forms], about ProgressBar control
- progress controls [Windows Forms], about progress controls
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c5ca5fd908124b0f38643c7b2833ba591be3b980
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="progressbar-control-overview-windows-forms"></a><span data-ttu-id="9a617-102">ProgressBar コントロールの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="9a617-102">ProgressBar Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="9a617-103"><xref:System.Windows.Forms.ToolStripProgressBar> コントロールは、<xref:System.Windows.Forms.ProgressBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.ProgressBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。</span><span class="sxs-lookup"><span data-stu-id="9a617-103">The <xref:System.Windows.Forms.ToolStripProgressBar> control replaces and adds functionality to the <xref:System.Windows.Forms.ProgressBar> control; however, the <xref:System.Windows.Forms.ProgressBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="9a617-104">Windows フォーム<xref:System.Windows.Forms.ProgressBar>コントロールが水平のバーに配置された四角形の適切な数を表示することによって、プロセスの進行状況を示します。</span><span class="sxs-lookup"><span data-stu-id="9a617-104">The Windows Forms <xref:System.Windows.Forms.ProgressBar> control indicates the progress of a process by displaying an appropriate number of rectangles arranged in a horizontal bar.</span></span> <span data-ttu-id="9a617-105">プロセスが完了すると、バーが入力されます。</span><span class="sxs-lookup"><span data-stu-id="9a617-105">When the process is complete, the bar is filled.</span></span> <span data-ttu-id="9a617-106">進行状況バーが方法の概要を把握するためによく使用されるまで、プロセスを完了するまでの待機時間たとえば、ときにサイズの大きなファイルが読み込まれています。</span><span class="sxs-lookup"><span data-stu-id="9a617-106">Progress bars are commonly used to give the user an idea of how long to wait for a process to complete; for instance, when a large file is being loaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a617-107"><xref:System.Windows.Forms.ProgressBar>コントロールがフォームに水平方向でのみことができます。</span><span class="sxs-lookup"><span data-stu-id="9a617-107">The <xref:System.Windows.Forms.ProgressBar> control can only be oriented horizontally on the form.</span></span>  
  
## <a name="key-properties-and-methods"></a><span data-ttu-id="9a617-108">キー プロパティとメソッド</span><span class="sxs-lookup"><span data-stu-id="9a617-108">Key Properties and Methods</span></span>  
 <span data-ttu-id="9a617-109">キー プロパティ、<xref:System.Windows.Forms.ProgressBar>コントロールは<xref:System.Windows.Forms.ProgressBar.Value%2A>、 <xref:System.Windows.Forms.ProgressBar.Minimum%2A>、および<xref:System.Windows.Forms.ProgressBar.Maximum%2A>です。</span><span class="sxs-lookup"><span data-stu-id="9a617-109">The key properties of the <xref:System.Windows.Forms.ProgressBar> control are <xref:System.Windows.Forms.ProgressBar.Value%2A>, <xref:System.Windows.Forms.ProgressBar.Minimum%2A>, and <xref:System.Windows.Forms.ProgressBar.Maximum%2A>.</span></span> <span data-ttu-id="9a617-110"><xref:System.Windows.Forms.ProgressBar.Minimum%2A>と<xref:System.Windows.Forms.ProgressBar.Maximum%2A>プロパティが、進行状況バーが表示できる最大と最小値を設定します。</span><span class="sxs-lookup"><span data-stu-id="9a617-110">The <xref:System.Windows.Forms.ProgressBar.Minimum%2A> and <xref:System.Windows.Forms.ProgressBar.Maximum%2A> properties set the maximum and minimum values the progress bar can display.</span></span> <span data-ttu-id="9a617-111"><xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティが行われた操作の完了に向けた進行状況を表します。</span><span class="sxs-lookup"><span data-stu-id="9a617-111">The <xref:System.Windows.Forms.ProgressBar.Value%2A> property represents the progress that has been made toward completing the operation.</span></span> <span data-ttu-id="9a617-112">値がによって表示される、コントロールに表示されるバーがブロックで構成されるため、<xref:System.Windows.Forms.ProgressBar>コントロールのみ概算するための<xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティの現在の値。</span><span class="sxs-lookup"><span data-stu-id="9a617-112">Because the bar displayed in the control is composed of blocks, the value displayed by the <xref:System.Windows.Forms.ProgressBar> control only approximates the <xref:System.Windows.Forms.ProgressBar.Value%2A> property's current value.</span></span> <span data-ttu-id="9a617-113">サイズに基づいて、<xref:System.Windows.Forms.ProgressBar>コントロール、<xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティには、次のブロックを表示するタイミングを決定します。</span><span class="sxs-lookup"><span data-stu-id="9a617-113">Based on the size of the <xref:System.Windows.Forms.ProgressBar> control, the <xref:System.Windows.Forms.ProgressBar.Value%2A> property determines when to display the next block.</span></span>  
  
 <span data-ttu-id="9a617-114">現在の進行状況の値を更新する最も一般的な方法を設定するコードを記述する、<xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="9a617-114">The most common way to update the current progress value is to write code to set the <xref:System.Windows.Forms.ProgressBar.Value%2A> property.</span></span> <span data-ttu-id="9a617-115">サイズの大きなファイルの読み込みの例では、キロバイト単位でファイルのサイズを最大値を設定する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9a617-115">In the example of loading a large file, you might set the maximum to the size of the file in kilobytes.</span></span> <span data-ttu-id="9a617-116">などの場合、<xref:System.Windows.Forms.ProgressBar.Maximum%2A>プロパティが 100 に設定、<xref:System.Windows.Forms.ProgressBar.Minimum%2A>プロパティが 10 に設定と<xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティが設定されて 50 に 5 つの四角形が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9a617-116">For example, if the <xref:System.Windows.Forms.ProgressBar.Maximum%2A> property is set to 100, the <xref:System.Windows.Forms.ProgressBar.Minimum%2A> property is set to 10, and the <xref:System.Windows.Forms.ProgressBar.Value%2A> property is set to 50, 5 rectangles will be displayed.</span></span> <span data-ttu-id="9a617-117">これは、表示可能な数の半分です。</span><span class="sxs-lookup"><span data-stu-id="9a617-117">This is half of the number that can be displayed.</span></span>  
  
 <span data-ttu-id="9a617-118">ただし、他の方法で表示される値を変更するのには、<xref:System.Windows.Forms.ProgressBar>設定とは別のコントロール、<xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティを直接です。</span><span class="sxs-lookup"><span data-stu-id="9a617-118">However, there are other ways to modify the value displayed by the <xref:System.Windows.Forms.ProgressBar> control, aside from setting the <xref:System.Windows.Forms.ProgressBar.Value%2A> property directly.</span></span> <span data-ttu-id="9a617-119"><xref:System.Windows.Forms.ProgressBar.Step%2A>をインクリメントする値を指定するプロパティを使用することができます、<xref:System.Windows.Forms.ProgressBar.Value%2A>によってプロパティです。</span><span class="sxs-lookup"><span data-stu-id="9a617-119">The <xref:System.Windows.Forms.ProgressBar.Step%2A> property can be used to specify a value to increment the <xref:System.Windows.Forms.ProgressBar.Value%2A> property by.</span></span> <span data-ttu-id="9a617-120">呼び出すことで、<xref:System.Windows.Forms.ProgressBar.PerformStep%2A>メソッドには、値が 1 ずつ増分されます。</span><span class="sxs-lookup"><span data-stu-id="9a617-120">Then, calling the <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> method will increment the value.</span></span> <span data-ttu-id="9a617-121">増分値を変更するには、使用することができます、<xref:System.Windows.Forms.ProgressBar.Increment%2A>メソッドを増分する値を指定し、<xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="9a617-121">To vary the increment value, you can use the <xref:System.Windows.Forms.ProgressBar.Increment%2A> method and specify a value with which to increment the <xref:System.Windows.Forms.ProgressBar.Value%2A> property.</span></span>  
  
 <span data-ttu-id="9a617-122">現在の操作について、ユーザーに通知してグラフィカルに表示する別のコントロールは、<xref:System.Windows.Forms.StatusBar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="9a617-122">Another control that graphically informs the user about a current action is the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9a617-123"><xref:System.Windows.Forms.StatusStrip>と<xref:System.Windows.Forms.ToolStripStatusLabel>コントロールの置換し、する機能を追加、<xref:System.Windows.Forms.StatusBar>と<xref:System.Windows.Forms.StatusBarPanel>コントロールですただし、、<xref:System.Windows.Forms.StatusBar>と<xref:System.Windows.Forms.StatusBarPanel>場合、旧バージョンとの互換性と将来の使用の両方のコントロールが保持されますします。選択します。</span><span class="sxs-lookup"><span data-stu-id="9a617-123">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a617-124">参照</span><span class="sxs-lookup"><span data-stu-id="9a617-124">See Also</span></span>  
 <xref:System.Windows.Forms.ProgressBar>  
 [<span data-ttu-id="9a617-125">ProgressBar コントロール</span><span class="sxs-lookup"><span data-stu-id="9a617-125">ProgressBar Control</span></span>](../../../../docs/framework/winforms/controls/progressbar-control-windows-forms.md)
