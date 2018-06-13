---
title: RichTextBox コントロール (Windows フォーム)
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes
- RichTextBox control [Windows Forms]
- rich edit controls
ms.assetid: 3225f2ef-c6d9-4bd4-9d3e-2219e58edbf2
ms.openlocfilehash: 00f28abeb616006e63a45dd7922f4d5b247e8dd9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540883"
---
# <a name="richtextbox-control-windows-forms"></a><span data-ttu-id="c95f5-102">RichTextBox コントロール (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="c95f5-102">RichTextBox Control (Windows Forms)</span></span>
<span data-ttu-id="c95f5-103">Windows フォーム`RichTextBox`コントロールを表示、入力すると、および書式設定を含むテキストを操作するために使用します。</span><span class="sxs-lookup"><span data-stu-id="c95f5-103">The Windows Forms `RichTextBox` control is used for displaying, entering, and manipulating text with formatting.</span></span> <span data-ttu-id="c95f5-104">`RichTextBox`コントロールはすべて、<xref:System.Windows.Forms.TextBox>コントロールできますが、ことができますフォント、色、およびリンクの表示以外の場合はファイル以外の場合は元に戻すおよびやり直し操作の編集からテキストと埋め込み画像の読み込み、指定した文字を検索します。</span><span class="sxs-lookup"><span data-stu-id="c95f5-104">The `RichTextBox` control does everything the <xref:System.Windows.Forms.TextBox> control does, but it can also display fonts, colors, and links; load text and embedded images from a file; undo and redo editing operations; and find specified characters.</span></span> <span data-ttu-id="c95f5-105">`RichTextBox`通常、コントロールはテキストの操作を提供し、Microsoft Word などのワード プロセッシング アプリケーションと同様の機能の表示に使用します。</span><span class="sxs-lookup"><span data-stu-id="c95f5-105">The `RichTextBox` control is typically used to provide text manipulation and display features similar to word processing applications such as Microsoft Word.</span></span> <span data-ttu-id="c95f5-106">同様に、<xref:System.Windows.Forms.TextBox>コントロール、`RichTextBox`コントロールがスクロール バーを表示できるとは異なり、<xref:System.Windows.Forms.TextBox>コントロール、既定では両方水平および垂直方向のスクロール バーを表示し、追加のスクロール バーの設定。</span><span class="sxs-lookup"><span data-stu-id="c95f5-106">Like the <xref:System.Windows.Forms.TextBox> control, the `RichTextBox` control can display scroll bars; but unlike the <xref:System.Windows.Forms.TextBox> control, it displays both horizontal and vertical scrollbars by default and has additional scrollbar settings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c95f5-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c95f5-107">In This Section</span></span>  
 [<span data-ttu-id="c95f5-108">RichTextBox コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="c95f5-108">RichTextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md)  
 <span data-ttu-id="c95f5-109">一般的な概念が導入されています、`RichTextBox`コントロールで、ユーザー入力を許可するには、表示、および書式設定オプションでテキストを操作します。</span><span class="sxs-lookup"><span data-stu-id="c95f5-109">Introduces the general concepts of the `RichTextBox` control, which allows users to enter, display, and manipulate text with formatting options.</span></span>  
  
 [<span data-ttu-id="c95f5-110">方法: Windows フォームの RichTextBox コントロールにおける書式属性の変更を確認する</span><span class="sxs-lookup"><span data-stu-id="c95f5-110">How to: Determine When Formatting Attributes Change in the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/determine-when-formatting-attributes-change-wf-richtextbox-control.md)  
 <span data-ttu-id="c95f5-111">フォントおよび段落書式の設定の変更を追跡する方法について説明します、`RichTextBox`コントロール。</span><span class="sxs-lookup"><span data-stu-id="c95f5-111">Explains how to keep track of changes in font and paragraph formatting in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="c95f5-112">方法: Windows フォームの RichTextBox コントロールにスクロール バーを表示する</span><span class="sxs-lookup"><span data-stu-id="c95f5-112">How to: Display Scroll Bars in the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="c95f5-113">内のスクロール バーの使用可能な多くの選択肢について説明します、`RichTextBox`コントロール。</span><span class="sxs-lookup"><span data-stu-id="c95f5-113">Describes the many choices available for scroll bars in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="c95f5-114">方法: Windows フォームの RichTextBox コントロールを使用して Web スタイルのリンクを表示する</span><span class="sxs-lookup"><span data-stu-id="c95f5-114">How to: Display Web-Style Links with the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="c95f5-115">Web サイトにリンクする方法について説明します、`RichTextBox`コントロール。</span><span class="sxs-lookup"><span data-stu-id="c95f5-115">Explains how to link to Web sites from the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="c95f5-116">方法: Windows フォームの RichTextBox コントロールにおけるドラッグ アンド ドロップ操作を有効にする</span><span class="sxs-lookup"><span data-stu-id="c95f5-116">How to: Enable Drag-and-Drop Operations with the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/enable-drag-and-drop-operations-with-wf-richtextbox-control.md)  
 <span data-ttu-id="c95f5-117">データをドラッグする方法について説明、`RichTextBox`コントロール。</span><span class="sxs-lookup"><span data-stu-id="c95f5-117">Provides instructions for dragging data into the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="c95f5-118">方法: Windows フォームの RichTextBox コントロールにファイルを読み込む</span><span class="sxs-lookup"><span data-stu-id="c95f5-118">How to: Load Files into the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-load-files-into-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="c95f5-119">既存のファイルを読み込むための説明、`RichTextBox`コントロール。</span><span class="sxs-lookup"><span data-stu-id="c95f5-119">Provides instructions for loading an existing file into the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="c95f5-120">方法: Windows フォームの RichTextBox コントロールを使用してファイルを保存する</span><span class="sxs-lookup"><span data-stu-id="c95f5-120">How to: Save Files with the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-save-files-with-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="c95f5-121">内容を保存する方法について説明、`RichTextBox`ファイルを制御します。</span><span class="sxs-lookup"><span data-stu-id="c95f5-121">Provides instructions for saving the contents of the `RichTextBox` control to a file.</span></span>  
  
 [<span data-ttu-id="c95f5-122">方法: Windows フォームの RichTextBox コントロールのフォント属性を設定する</span><span class="sxs-lookup"><span data-stu-id="c95f5-122">How to: Set Font Attributes for the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md)  
 <span data-ttu-id="c95f5-123">フォント ファミリ、サイズ、スタイル、およびテキストの色を設定する方法について説明します、`RichTextBox`コントロール。</span><span class="sxs-lookup"><span data-stu-id="c95f5-123">Describes how to set the font family, size, style, and color of text in the `RichTextBox` control.</span></span>  
  
 [<span data-ttu-id="c95f5-124">方法: Windows フォームの RichTextBox コントロールを使用してインデント、ぶら下げインデント、および箇条書き段落を設定する</span><span class="sxs-lookup"><span data-stu-id="c95f5-124">How to: Set Indents, Hanging Indents, and Bulleted Paragraphs with the Windows Forms RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md)  
 <span data-ttu-id="c95f5-125">内の段落の書式を設定する方法について説明、`RichTextBox`コントロール。</span><span class="sxs-lookup"><span data-stu-id="c95f5-125">Describes how to format paragraphs in the `RichTextBox` control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c95f5-126">参照</span><span class="sxs-lookup"><span data-stu-id="c95f5-126">Reference</span></span>  
 <span data-ttu-id="c95f5-127"><xref:System.Windows.Forms.RichTextBox> クラス</span><span class="sxs-lookup"><span data-stu-id="c95f5-127"><xref:System.Windows.Forms.RichTextBox> class</span></span>  
 <span data-ttu-id="c95f5-128">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="c95f5-128">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c95f5-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="c95f5-129">Related Sections</span></span>  
 [<span data-ttu-id="c95f5-130">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="c95f5-130">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="c95f5-131">Windows フォーム コントロールの完全な一覧を、使用に関する情報リンクと共に提供します。</span><span class="sxs-lookup"><span data-stu-id="c95f5-131">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 [<span data-ttu-id="c95f5-132">TextBox コントロール</span><span class="sxs-lookup"><span data-stu-id="c95f5-132">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)  
 <span data-ttu-id="c95f5-133">一般的な概念が導入されています、<xref:System.Windows.Forms.TextBox>コントロールで、ユーザーの編集可能な複数行の入力を許可します。</span><span class="sxs-lookup"><span data-stu-id="c95f5-133">Introduces the general concepts of the <xref:System.Windows.Forms.TextBox> control, which allows editable, multiline input from the user.</span></span>
