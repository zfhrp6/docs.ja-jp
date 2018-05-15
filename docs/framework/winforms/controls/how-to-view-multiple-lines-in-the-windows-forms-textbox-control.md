---
title: '方法 : Windows フォーム TextBox コントロールで複数行を表示する'
ms.date: 03/30/2017
helpviewer_keywords:
- newline
- end of line
- ScrollBars property [Windows Forms], in TextBox control
- CRLF
- MultiLine property in TextBox control
- line-feed
- TextBox control [Windows Forms], viewing multiple lines
- carriage return
ms.assetid: 43173201-0b74-4067-a472-605029ca5f35
ms.openlocfilehash: c826a519d8be05430eb6e2434209424514347b5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a><span data-ttu-id="71cec-102">方法 : Windows フォーム TextBox コントロールで複数行を表示する</span><span class="sxs-lookup"><span data-stu-id="71cec-102">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="71cec-103">既定では、Windows フォーム<xref:System.Windows.Forms.TextBox>コントロールは、1 行のテキストを表示し、スクロール バーは表示されません。</span><span class="sxs-lookup"><span data-stu-id="71cec-103">By default, the Windows Forms <xref:System.Windows.Forms.TextBox> control displays a single line of text and does not display scroll bars.</span></span> <span data-ttu-id="71cec-104">テキストは、使用可能な領域よりも長くなりますが、テキストの一部のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="71cec-104">If the text is longer than the available space, only part of the text is visible.</span></span> <span data-ttu-id="71cec-105">この既定の動作を変更するには設定して、 <xref:System.Windows.Forms.TextBox.Multiline%2A>、<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>と<xref:System.Windows.Forms.TextBox.ScrollBars%2A>プロパティを適切な値にします。</span><span class="sxs-lookup"><span data-stu-id="71cec-105">You can change this default behavior by setting the <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, and <xref:System.Windows.Forms.TextBox.ScrollBars%2A> properties to appropriate values.</span></span>  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a><span data-ttu-id="71cec-106">TextBox コントロールでの改行を表示するには</span><span class="sxs-lookup"><span data-stu-id="71cec-106">To display a carriage return in the TextBox control</span></span>  
  
-   <span data-ttu-id="71cec-107">複数の行に改行を表示する<xref:System.Windows.Forms.TextBox>を使用して、<xref:System.Environment.NewLine%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="71cec-107">To display a carriage return in a multi-line <xref:System.Windows.Forms.TextBox>, use the <xref:System.Environment.NewLine%2A> property.</span></span>  
  
     <span data-ttu-id="71cec-108">注意してくださいをエスケープ文字の解釈 (\\) 言語に固有です。</span><span class="sxs-lookup"><span data-stu-id="71cec-108">Be aware that the interpretation of escape characters (\\) is language-specific.</span></span> <span data-ttu-id="71cec-109">Visual Basic で`Chr$(13) & Chr$(10)`のキャリッジ リターンとライン フィード文字の組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="71cec-109">Visual Basic uses `Chr$(13) & Chr$(10)` for the carriage return and linefeed character combination.</span></span>  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a><span data-ttu-id="71cec-110">テキスト ボックス コントロールで複数の行を表示するには</span><span class="sxs-lookup"><span data-stu-id="71cec-110">To view multiple lines in the TextBox control</span></span>  
  
1.  <span data-ttu-id="71cec-111"><xref:System.Windows.Forms.TextBox.Multiline%2A> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="71cec-111">Set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`.</span></span> <span data-ttu-id="71cec-112">場合<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>は`true`(既定)、コントロール内のテキストが、1 つまたは複数の段落を表示する、以外の場合はそれ以外の場合でサポートされる一覧は、一部の行はコントロールの端に隠れてしまうことがあります。</span><span class="sxs-lookup"><span data-stu-id="71cec-112">If <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> is `true` (the default), then the text in the control will appear as one or more paragraphs; otherwise it will appear as a list, in which some lines may be clipped at the edge of the control.</span></span>  
  
2.  <span data-ttu-id="71cec-113"><xref:System.Windows.Forms.TextBox.ScrollBars%2A> プロパティに適切な値を設定します。</span><span class="sxs-lookup"><span data-stu-id="71cec-113">Set the <xref:System.Windows.Forms.TextBox.ScrollBars%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="71cec-114">[値]</span><span class="sxs-lookup"><span data-stu-id="71cec-114">Value</span></span>|<span data-ttu-id="71cec-115">説明</span><span class="sxs-lookup"><span data-stu-id="71cec-115">Description</span></span>|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|<span data-ttu-id="71cec-116">段落テキストにする場合は、この値を使用するコントロールにほぼ常に適合します。</span><span class="sxs-lookup"><span data-stu-id="71cec-116">Use this value if the text will be a paragraph that almost always fits the control.</span></span> <span data-ttu-id="71cec-117">ユーザーは、一度にすべてを表示するには、テキストが長すぎる場合、コントロール内に移動する、マウス ポインターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="71cec-117">The user can use the mouse pointer to move around inside the control if the text is too long to display all at once.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|<span data-ttu-id="71cec-118">線、これらのいくつかの幅を超える可能性がありますの一覧を表示する場合、この値を使用して、<xref:System.Windows.Forms.TextBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="71cec-118">Use this value if you want to display a list of lines, some of which may be longer than the width of the <xref:System.Windows.Forms.TextBox> control.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|<span data-ttu-id="71cec-119">一覧は、コントロールの高さより長くすることがある場合は、この値を使用します。</span><span class="sxs-lookup"><span data-stu-id="71cec-119">Use this value if the list may be longer than the height of the control.</span></span>|  
  
3.  <span data-ttu-id="71cec-120"><xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> プロパティに適切な値を設定します。</span><span class="sxs-lookup"><span data-stu-id="71cec-120">Set the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="71cec-121">[値]</span><span class="sxs-lookup"><span data-stu-id="71cec-121">Value</span></span>|<span data-ttu-id="71cec-122">説明</span><span class="sxs-lookup"><span data-stu-id="71cec-122">Description</span></span>|  
    |-----------|-----------------|  
    |`false`|<span data-ttu-id="71cec-123">コントロール内のテキストが自動的に折り返される、ため、行の区切りに到達するまで右にスクロールされます。</span><span class="sxs-lookup"><span data-stu-id="71cec-123">Text in the control will not automatically be wrapped, so it will scroll to the right until a line break is reached.</span></span> <span data-ttu-id="71cec-124">選択した場合は、この値を使用して<xref:System.Windows.Forms.ScrollBars.Horizontal>スクロール バーまたは<xref:System.Windows.Forms.ScrollBars.Both>上、します。</span><span class="sxs-lookup"><span data-stu-id="71cec-124">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Horizontal> scroll bars or <xref:System.Windows.Forms.ScrollBars.Both>, above.</span></span>|  
    |<span data-ttu-id="71cec-125">`true` (既定値)</span><span class="sxs-lookup"><span data-stu-id="71cec-125">`true` (default)</span></span>|<span data-ttu-id="71cec-126">水平スクロール バーは表示されません。</span><span class="sxs-lookup"><span data-stu-id="71cec-126">The horizontal scrollbar will not appear.</span></span> <span data-ttu-id="71cec-127">選択した場合は、この値を使用して<xref:System.Windows.Forms.ScrollBars.Vertical>スクロール バーまたは<xref:System.Windows.Forms.ScrollBars.None>、上記の 1 つまたは複数の段落を表示します。</span><span class="sxs-lookup"><span data-stu-id="71cec-127">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Vertical> scroll bars or <xref:System.Windows.Forms.ScrollBars.None>, above, to display one or more paragraphs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="71cec-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="71cec-128">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="71cec-129">TextBox コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="71cec-129">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="71cec-130">方法: Windows フォーム TextBox コントロールでのカーソル位置を制御する</span><span class="sxs-lookup"><span data-stu-id="71cec-130">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="71cec-131">方法: Windows フォームの TextBox コントロールを使用してパスワード テキスト ボックスを作成する</span><span class="sxs-lookup"><span data-stu-id="71cec-131">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="71cec-132">方法: 読み取り専用テキスト ボックスを作成する</span><span class="sxs-lookup"><span data-stu-id="71cec-132">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="71cec-133">方法: 文字列に引用符を挿入する</span><span class="sxs-lookup"><span data-stu-id="71cec-133">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="71cec-134">方法: Windows フォーム TextBox コントロールでテキストを選択する</span><span class="sxs-lookup"><span data-stu-id="71cec-134">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="71cec-135">TextBox コントロール</span><span class="sxs-lookup"><span data-stu-id="71cec-135">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
