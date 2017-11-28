---
title: "方法 : Windows フォームの RichTextBox コントロールにスクロール バーを表示する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text boxes [Windows Forms], displaying scroll bars
- scroll bars [Windows Forms], displaying in controls
- RichTextBox control [Windows Forms], displaying scroll bars
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3b20c526b27eb185bf79eaf0ace47e5a9fded42a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control"></a><span data-ttu-id="89ce5-102">方法 : Windows フォームの RichTextBox コントロールにスクロール バーを表示する</span><span class="sxs-lookup"><span data-stu-id="89ce5-102">How to: Display Scroll Bars in the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="89ce5-103">既定では、Windows フォーム<xref:System.Windows.Forms.RichTextBox>コントロールは、必要に応じて、垂直および水平スクロール バーを表示します。</span><span class="sxs-lookup"><span data-stu-id="89ce5-103">By default, the Windows Forms <xref:System.Windows.Forms.RichTextBox> control displays horizontal and vertical scroll bars as necessary.</span></span> <span data-ttu-id="89ce5-104">7 つの可能な値がある、<xref:System.Windows.Forms.RichTextBox.ScrollBars%2A>のプロパティ、<xref:System.Windows.Forms.RichTextBox>コントロールで、次の表で説明します。</span><span class="sxs-lookup"><span data-stu-id="89ce5-104">There are seven possible values for the <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> property of the <xref:System.Windows.Forms.RichTextBox> control, which are described in the table below.</span></span>  
  
### <a name="to-display-scroll-bars-in-a-richtextbox-control"></a><span data-ttu-id="89ce5-105">RichTextBox コントロールにスクロール バーを表示するには</span><span class="sxs-lookup"><span data-stu-id="89ce5-105">To display scroll bars in a RichTextBox control</span></span>  
  
1.  <span data-ttu-id="89ce5-106"><xref:System.Windows.Forms.RichTextBox.Multiline%2A> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="89ce5-106">Set the <xref:System.Windows.Forms.RichTextBox.Multiline%2A> property to `true`.</span></span> <span data-ttu-id="89ce5-107">水平方向などのスクロール バーの種類が表示されない、<xref:System.Windows.Forms.RichTextBox.Multiline%2A>プロパティに設定されている`false`です。</span><span class="sxs-lookup"><span data-stu-id="89ce5-107">No type of scroll bar, including horizontal, will display if the <xref:System.Windows.Forms.RichTextBox.Multiline%2A> property is set to `false`.</span></span>  
  
2.  <span data-ttu-id="89ce5-108">設定、<xref:System.Windows.Forms.RichTextBox.ScrollBars%2A>プロパティの適切な値を<xref:System.Windows.Forms.RichTextBoxScrollBars>列挙します。</span><span class="sxs-lookup"><span data-stu-id="89ce5-108">Set the <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> property to an appropriate value of the <xref:System.Windows.Forms.RichTextBoxScrollBars> enumeration.</span></span>  
  
    |<span data-ttu-id="89ce5-109">値</span><span class="sxs-lookup"><span data-stu-id="89ce5-109">Value</span></span>|<span data-ttu-id="89ce5-110">説明</span><span class="sxs-lookup"><span data-stu-id="89ce5-110">Description</span></span>|  
    |-----------|-----------------|  
    |<span data-ttu-id="89ce5-111"><xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (既定値)</span><span class="sxs-lookup"><span data-stu-id="89ce5-111"><xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (default)</span></span>|<span data-ttu-id="89ce5-112">テキストがコントロールの高さや幅を超えた場合にのみ、水平または垂直スクロール バー、またはその両方を表示します。</span><span class="sxs-lookup"><span data-stu-id="89ce5-112">Displays horizontal or vertical scroll bars, or both, only when text exceeds the width or length of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.None>|<span data-ttu-id="89ce5-113">スクロール バーの任意の型がまったく表示されません。</span><span class="sxs-lookup"><span data-stu-id="89ce5-113">Never displays any type of scroll bar.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Horizontal>|<span data-ttu-id="89ce5-114">水平スクロール バーのテキストがコントロールの幅を超えた場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="89ce5-114">Displays a horizontal scroll bar only when the text exceeds the width of the control.</span></span> <span data-ttu-id="89ce5-115">(これには、<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>プロパティに設定する必要があります`false`)。</span><span class="sxs-lookup"><span data-stu-id="89ce5-115">(For this to occur, the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property must be set to `false`.)</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Vertical>|<span data-ttu-id="89ce5-116">垂直スクロール バーのテキストがコントロールの高さを超えた場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="89ce5-116">Displays a vertical scroll bar only when the text exceeds the height of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedHorizontal>|<span data-ttu-id="89ce5-117">水平スクロール バーの場合に表示、<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>プロパティに設定されている`false`です。</span><span class="sxs-lookup"><span data-stu-id="89ce5-117">Displays a horizontal scroll bar when the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property is set to `false`.</span></span> <span data-ttu-id="89ce5-118">テキストがコントロールの幅を超えていない場合、スクロール バーは淡色表示になります。</span><span class="sxs-lookup"><span data-stu-id="89ce5-118">The scroll bar appears dimmed when text does not exceed the width of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedVertical>|<span data-ttu-id="89ce5-119">常に垂直スクロール バーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="89ce5-119">Always displays a vertical scroll bar.</span></span> <span data-ttu-id="89ce5-120">テキストがコントロールの長さを超えていない場合、スクロール バーは淡色表示になります。</span><span class="sxs-lookup"><span data-stu-id="89ce5-120">The scroll bar appears dimmed when text does not exceed the length of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedBoth>|<span data-ttu-id="89ce5-121">常に垂直スクロール バーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="89ce5-121">Always displays a vertical scrollbar.</span></span> <span data-ttu-id="89ce5-122">水平スクロール バーの場合に表示、<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>プロパティに設定されている`false`です。</span><span class="sxs-lookup"><span data-stu-id="89ce5-122">Displays a horizontal scroll bar when the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property is set to `false`.</span></span> <span data-ttu-id="89ce5-123">テキストがコントロールの高さや幅を超えていない場合、スクロール バーは灰色表示されている表示されます。</span><span class="sxs-lookup"><span data-stu-id="89ce5-123">The scroll bars appear grayed when text does not exceed the width or length of the control.</span></span>|  
  
3.  <span data-ttu-id="89ce5-124"><xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> プロパティに適切な値を設定します。</span><span class="sxs-lookup"><span data-stu-id="89ce5-124">Set the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="89ce5-125">値</span><span class="sxs-lookup"><span data-stu-id="89ce5-125">Value</span></span>|<span data-ttu-id="89ce5-126">説明</span><span class="sxs-lookup"><span data-stu-id="89ce5-126">Description</span></span>|  
    |-----------|-----------------|  
    |`false`|<span data-ttu-id="89ce5-127">コントロール内のテキスト行の区切りに到達するまで右にスクロールされますので、コントロールの幅に合わせて自動的に調整されません。</span><span class="sxs-lookup"><span data-stu-id="89ce5-127">Text in the control is not automatically adjusted to fit the width of the control, so it will scroll to the right until a line break is reached.</span></span> <span data-ttu-id="89ce5-128">または、両方の水平スクロール バーを上に選択した場合は、この値を使用します。</span><span class="sxs-lookup"><span data-stu-id="89ce5-128">Use this value if you chose horizontal scroll bars or both, above.</span></span>|  
    |<span data-ttu-id="89ce5-129">`true` (既定値)</span><span class="sxs-lookup"><span data-stu-id="89ce5-129">`true` (default)</span></span>|<span data-ttu-id="89ce5-130">コントロール内のテキストは、コントロールの幅に合わせて自動的に調整します。</span><span class="sxs-lookup"><span data-stu-id="89ce5-130">Text in the control is automatically adjusted to fit the width of the control.</span></span> <span data-ttu-id="89ce5-131">水平スクロール バーは表示されません。</span><span class="sxs-lookup"><span data-stu-id="89ce5-131">The horizontal scrollbar will not appear.</span></span> <span data-ttu-id="89ce5-132">1 つまたは複数の段落を表示する、上記の垂直スクロール バーまたは none を選択した場合は、この値を使用します。</span><span class="sxs-lookup"><span data-stu-id="89ce5-132">Use this value if you chose vertical scroll bars or none, above, to display one or more paragraphs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="89ce5-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="89ce5-133">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBoxScrollBars>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="89ce5-134">RichTextBox コントロール</span><span class="sxs-lookup"><span data-stu-id="89ce5-134">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="89ce5-135">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="89ce5-135">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
