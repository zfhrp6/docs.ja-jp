---
title: "HScrollBar コントロールと VScrollBar コントロールの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- HScrollBar
- VScrollBar
helpviewer_keywords:
- ScrollBar control [Windows Forms]
- HScrollBar control [Windows Forms], about HScrollBar
- VScrollBar control [Windows Forms], about VScrollBar control
- ScrollBar control [Windows Forms], about ScrollBar control
- scroll bars [Windows Forms], about scroll bars
ms.assetid: 8b307679-1cae-41d8-99aa-3d1efd207cd6
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c7a6f1d569234f7cee4b5eedc81fcc68a41fcf0e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="hscrollbar-and-vscrollbar-controls-overview-windows-forms"></a><span data-ttu-id="4fc75-102">HScrollBar コントロールと VScrollBar コントロールの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="4fc75-102">HScrollBar and VScrollBar Controls Overview (Windows Forms)</span></span>
<span data-ttu-id="4fc75-103">Windows フォーム<xref:System.Windows.Forms.ScrollBar>または垂直方向に水平方向にスクロールすることにより、アプリケーションまたはコントロール内で簡単にナビゲート長い一覧の項目または大量の情報を提供するコントロールを使用します。</span><span class="sxs-lookup"><span data-stu-id="4fc75-103">Windows Forms <xref:System.Windows.Forms.ScrollBar> controls are used to provide easy navigation through a long list of items or a large amount of information by scrolling either horizontally or vertically within an application or control.</span></span> <span data-ttu-id="4fc75-104">スクロール バーは、Windows のインターフェイスの一般的な要素をそのため、<xref:System.Windows.Forms.ScrollBar>コントロールから派生していないを持つコントロールが使用される多くの場合、<xref:System.Windows.Forms.ScrollableControl>クラスです。</span><span class="sxs-lookup"><span data-stu-id="4fc75-104">Scroll bars are a common element of the Windows interface, so the <xref:System.Windows.Forms.ScrollBar> control is often used with controls that do not derive from the <xref:System.Windows.Forms.ScrollableControl> class.</span></span> <span data-ttu-id="4fc75-105">組み込むに多くの開発者が同様に、選択、<xref:System.Windows.Forms.ScrollBar>独自のユーザー コントロールを作成するときに制御します。</span><span class="sxs-lookup"><span data-stu-id="4fc75-105">Similarly, many developers choose to incorporate the <xref:System.Windows.Forms.ScrollBar> control when authoring their own user controls.</span></span>  
  
 <span data-ttu-id="4fc75-106"><xref:System.Windows.Forms.HScrollBar> (水平) と<xref:System.Windows.Forms.VScrollBar>(縦方向) の制御は、他のコントロールから独立して動作して、独自のイベント、プロパティ、およびメソッドのセット。</span><span class="sxs-lookup"><span data-stu-id="4fc75-106">The <xref:System.Windows.Forms.HScrollBar> (horizontal) and <xref:System.Windows.Forms.VScrollBar> (vertical) controls operate independently from other controls and have their own set of events, properties, and methods.</span></span> <span data-ttu-id="4fc75-107"><xref:System.Windows.Forms.ScrollBar>コントロールは、テキスト ボックス、リスト ボックス、コンボ ボックス、または MDI フォームにアタッチされている組み込みのスクロール バーと同じではありません (、<xref:System.Windows.Forms.TextBox>コントロールが、<xref:System.Windows.Forms.TextBox.ScrollBars%2A>プロパティ、コントロールに関連付けられているスクロール バーを非表示)。</span><span class="sxs-lookup"><span data-stu-id="4fc75-107"><xref:System.Windows.Forms.ScrollBar> controls are not the same as the built-in scroll bars that are attached to text boxes, list boxes, combo boxes, or MDI forms (the <xref:System.Windows.Forms.TextBox> control has a <xref:System.Windows.Forms.TextBox.ScrollBars%2A> property to show or hide scroll bars that are attached to the control).</span></span>  
  
 <span data-ttu-id="4fc75-108"><xref:System.Windows.Forms.ScrollBar>使用を制御、<xref:System.Windows.Forms.ScrollBar.Scroll>スクロール バーに沿ったスクロール ボックス (つまみとも呼ばれます) の動きを監視するイベントです。</span><span class="sxs-lookup"><span data-stu-id="4fc75-108">The <xref:System.Windows.Forms.ScrollBar> controls use the <xref:System.Windows.Forms.ScrollBar.Scroll> event to monitor the movement of the scroll box (sometimes referred to as the thumb) along the scroll bar.</span></span> <span data-ttu-id="4fc75-109">使用して、<xref:System.Windows.Forms.ScrollBar.Scroll>がドラッグされていると、イベントがスクロール バーの値へのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="4fc75-109">Using the <xref:System.Windows.Forms.ScrollBar.Scroll> event provides access to the scroll bar value as it is being dragged.</span></span>  
  
## <a name="value-property"></a><span data-ttu-id="4fc75-110">Value プロパティ</span><span class="sxs-lookup"><span data-stu-id="4fc75-110">Value Property</span></span>  
 <span data-ttu-id="4fc75-111"><xref:System.Windows.Forms.ScrollBar.Value%2A>プロパティ (つまり、既定では、0) は、`integer`スクロール バーのスクロール ボックスの位置に対応する値。</span><span class="sxs-lookup"><span data-stu-id="4fc75-111">The <xref:System.Windows.Forms.ScrollBar.Value%2A> property (which, by default, is 0) is an `integer` value corresponding to the position of the scroll box in the scroll bar.</span></span> <span data-ttu-id="4fc75-112">スクロール ボックスの位置は、最小値では、ときに、左端の位置 (水平スクロール バーまたは (垂直スクロール バーの上端の位置に移動します。</span><span class="sxs-lookup"><span data-stu-id="4fc75-112">When the scroll box position is at the minimum value, it moves to the left-most position (for horizontal scroll bars) or the top position (for vertical scroll bars).</span></span> <span data-ttu-id="4fc75-113">スクロール ボックスがの場合、最大値、一番右にスクロール ボックスの移動、または最下部の位置です。</span><span class="sxs-lookup"><span data-stu-id="4fc75-113">When the scroll box is at the maximum value, the scroll box moves to the right-most or bottom position.</span></span> <span data-ttu-id="4fc75-114">同様に、範囲の上部と下部の中間値は、スクロール バーの途中でスクロール ボックスの先端を配置します。</span><span class="sxs-lookup"><span data-stu-id="4fc75-114">Similarly, a value halfway between the bottom and top of the range places the leading edge of the scroll box in the middle of the scroll bar.</span></span>  
  
 <span data-ttu-id="4fc75-115">に加えて、マウスのクリックを使用して、スクロール バーの値を変更する、ユーザーが任意の時点、バーのスクロール ボックスをドラッグすることもできます。</span><span class="sxs-lookup"><span data-stu-id="4fc75-115">In addition to using mouse clicks to change the scroll bar value, a user can also drag the scroll box to any point along the bar.</span></span> <span data-ttu-id="4fc75-116">結果の値は、スクロール ボックスの位置によって異なりますが、範囲内では常に、<xref:System.Windows.Forms.ScrollBar.Minimum%2A>に<xref:System.Windows.Forms.ScrollBar.Maximum%2A>ユーザーによって設定されるプロパティです。</span><span class="sxs-lookup"><span data-stu-id="4fc75-116">The resulting value depends on the position of the scroll box, but it is always within the range of the <xref:System.Windows.Forms.ScrollBar.Minimum%2A> to <xref:System.Windows.Forms.ScrollBar.Maximum%2A> properties set by the user.</span></span>  
  
## <a name="largechange-and-smallchange-properties"></a><span data-ttu-id="4fc75-117">LargeChange と SmallChange プロパティ</span><span class="sxs-lookup"><span data-stu-id="4fc75-117">LargeChange and SmallChange Properties</span></span>  
 <span data-ttu-id="4fc75-118">ユーザーが PAGEUP または PAGEDOWN キーを押すかスクロール ボックスのどちら側にスクロール バーのトラックをクリックしたときに、<xref:System.Windows.Forms.ScrollBar.Value%2A>プロパティの変更に設定された値に従って、<xref:System.Windows.Forms.ScrollBar.LargeChange%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="4fc75-118">When the user presses the PAGE UP or PAGE DOWN key or clicks in the scroll bar track on either side of the scroll box, the <xref:System.Windows.Forms.ScrollBar.Value%2A> property changes according to the value set in the <xref:System.Windows.Forms.ScrollBar.LargeChange%2A> property.</span></span>  
  
 <span data-ttu-id="4fc75-119">押されたときの矢印のいずれかのキーか、スクロール バーのボタンのいずれかをクリックすると、<xref:System.Windows.Forms.ScrollBar.Value%2A>プロパティの変更に設定された値に従って、<xref:System.Windows.Forms.ScrollBar.SmallChange%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="4fc75-119">When the user presses one of the arrow keys or clicks one of the scroll bar buttons, the <xref:System.Windows.Forms.ScrollBar.Value%2A> property changes according to the value set in the <xref:System.Windows.Forms.ScrollBar.SmallChange%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fc75-120">参照</span><span class="sxs-lookup"><span data-stu-id="4fc75-120">See Also</span></span>  
 <xref:System.Windows.Forms.HScrollBar>  
 <xref:System.Windows.Forms.VScrollBar>  
 [<span data-ttu-id="4fc75-121">.NET Framework 2.0 の Windows フォームへの追加</span><span class="sxs-lookup"><span data-stu-id="4fc75-121">Additions to Windows Forms for the .NET Framework 2.0</span></span>](http://msdn.microsoft.com/en-us/c61a923d-3d6a-4c8c-820c-e94c83f3f9a8)  
 [<span data-ttu-id="4fc75-122">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="4fc75-122">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
