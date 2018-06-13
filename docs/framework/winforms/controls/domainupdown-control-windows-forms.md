---
title: DomainUpDown コントロール (Windows フォーム)
ms.date: 03/30/2017
helpviewer_keywords:
- DomainUpDown control [Windows Forms]
- spin button control [Windows Forms], up-down controls
- up-down controls
- spin button control
- up-down controls [Windows Forms], spin button controls
ms.assetid: fb7cf017-e931-4a95-9d21-8caee4ee122a
ms.openlocfilehash: c23f374f1ec9cab6e43b12d32b97c40533ac36cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527327"
---
# <a name="domainupdown-control-windows-forms"></a><span data-ttu-id="bcc9b-102">DomainUpDown コントロール (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="bcc9b-102">DomainUpDown Control (Windows Forms)</span></span>
<span data-ttu-id="bcc9b-103">Windows フォーム<xref:System.Windows.Forms.DomainUpDown>コントロールよう組のボタンとテキスト ボックスの組み合わせの一覧を上または下に移動します。</span><span class="sxs-lookup"><span data-stu-id="bcc9b-103">The Windows Forms <xref:System.Windows.Forms.DomainUpDown> control looks like a combination of a text box and a pair of buttons for moving up or down through a list.</span></span> <span data-ttu-id="bcc9b-104">コントロールは、表示し、選択肢の一覧から、テキスト文字列を設定します。</span><span class="sxs-lookup"><span data-stu-id="bcc9b-104">The control displays and sets a text string from a list of choices.</span></span> <span data-ttu-id="bcc9b-105">上下一覧内を移動するボタンをクリックして、上下の矢印キーを押すことによって、または、リスト内の項目に一致する文字列を入力して、ユーザーは、文字列を選択できます。</span><span class="sxs-lookup"><span data-stu-id="bcc9b-105">The user can select the string by clicking up and down buttons to move through a list, by pressing the UP and DOWN ARROW keys, or by typing a string that matches an item in the list.</span></span> <span data-ttu-id="bcc9b-106">このコントロールの用途の 1 つでは、名前のアルファベット順に並べ替えられたリストから項目を選択するためです。</span><span class="sxs-lookup"><span data-stu-id="bcc9b-106">One possible use for this control is for selecting items from an alphabetically sorted list of names.</span></span> <span data-ttu-id="bcc9b-107">(一覧を並べ替えるには設定、<xref:System.Windows.Forms.DomainUpDown.Sorted%2A>プロパティを`true`)。このコントロールの機能は、リスト ボックスまたはコンボ ボックスによく似ていますが、非常に小さい領域を占有します。</span><span class="sxs-lookup"><span data-stu-id="bcc9b-107">(To sort the list, set the <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> property to `true`.) The function of this control is very similar to the list box or combo box, but it takes up very little space.</span></span>  
  
 <span data-ttu-id="bcc9b-108">コントロールのプロパティは<xref:System.Windows.Forms.DomainUpDown.Items%2A>、 <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>、および<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>です。</span><span class="sxs-lookup"><span data-stu-id="bcc9b-108">The key properties of the control are <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, and <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span></span> <span data-ttu-id="bcc9b-109"><xref:System.Windows.Forms.DomainUpDown.Items%2A>プロパティには、文字列値を持つが、コントロールに表示されるオブジェクトの一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="bcc9b-109">The <xref:System.Windows.Forms.DomainUpDown.Items%2A> property contains the list of objects whose text values are displayed in the control.</span></span> <span data-ttu-id="bcc9b-110">場合<xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>に設定されている`false`コントロールは、ユーザーが型し、リスト内の値を内容と一致するテキストを自動的に完了します。</span><span class="sxs-lookup"><span data-stu-id="bcc9b-110">If <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> is set to `false`, the control automatically completes text that the user types and matches it to a value in the list.</span></span> <span data-ttu-id="bcc9b-111">場合<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>に設定されている`true`、スクロールの過去の最後の項目をクリックすると、一覧で、その逆の最初の項目。</span><span class="sxs-lookup"><span data-stu-id="bcc9b-111">If <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> is set to `true`, scrolling past the last item will take you to the first item in the list and vice versa.</span></span> <span data-ttu-id="bcc9b-112">コントロールの主要なメソッドは<xref:System.Windows.Forms.DomainUpDown.UpButton%2A>と<xref:System.Windows.Forms.DomainUpDown.DownButton%2A>です。</span><span class="sxs-lookup"><span data-stu-id="bcc9b-112">The key methods of the control are <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> and <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span></span>  
  
 <span data-ttu-id="bcc9b-113">このコントロールには、テキスト文字列のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bcc9b-113">This control displays only text strings.</span></span> <span data-ttu-id="bcc9b-114">数値を表示するコントロールを実行する場合に、使用、<xref:System.Windows.Forms.NumericUpDown>コントロール。</span><span class="sxs-lookup"><span data-stu-id="bcc9b-114">If you want a control that displays numeric values, use the <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="bcc9b-115">詳細については、次を参照してください。 [NumericUpDown コントロール](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="bcc9b-115">For more information, see [NumericUpDown Control](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md) .</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bcc9b-116">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="bcc9b-116">In This Section</span></span>  
 [<span data-ttu-id="bcc9b-117">DomainUpDown コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="bcc9b-117">DomainUpDown Control Overview</span></span>](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)  
 <span data-ttu-id="bcc9b-118">一般的な概念が導入されています、<xref:System.Windows.Forms.DomainUpDown>コントロールを参照し、テキスト文字列の一覧から選択することができます。</span><span class="sxs-lookup"><span data-stu-id="bcc9b-118">Introduces the general concepts of the <xref:System.Windows.Forms.DomainUpDown> control, which allows users to browse through and select from a list of text strings.</span></span>  
  
 [<span data-ttu-id="bcc9b-119">方法: Windows フォーム DomainUpDown コントロールにプログラムで項目を追加する</span><span class="sxs-lookup"><span data-stu-id="bcc9b-119">How to: Add Items to Windows Forms DomainUpDown Controls Programmatically</span></span>](../../../../docs/framework/winforms/controls/how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md)  
 <span data-ttu-id="bcc9b-120">テキスト文字列を指定する方法について説明します、<xref:System.Windows.Forms.DomainUpDown>コントロールを表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcc9b-120">Describes how to specify the text strings the <xref:System.Windows.Forms.DomainUpDown> control should display.</span></span>  
  
 [<span data-ttu-id="bcc9b-121">方法: Windows フォームの DomainUpDown コントロールから項目を削除する</span><span class="sxs-lookup"><span data-stu-id="bcc9b-121">How to: Remove Items from Windows Forms DomainUpDown Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 <span data-ttu-id="bcc9b-122">項目を削除する方法について説明します、<xref:System.Windows.Forms.DomainUpDown>コード内でコントロール。</span><span class="sxs-lookup"><span data-stu-id="bcc9b-122">Describes how to delete items from the <xref:System.Windows.Forms.DomainUpDown> control in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="bcc9b-123">参照</span><span class="sxs-lookup"><span data-stu-id="bcc9b-123">Reference</span></span>  
 <xref:System.Windows.Forms.DomainUpDown>  
 <span data-ttu-id="bcc9b-124">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="bcc9b-124">Describes this class and has links to all its members.</span></span>  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 <span data-ttu-id="bcc9b-125">このクラスについて説明し、すべてのメンバーへのリンクがあります.</span><span class="sxs-lookup"><span data-stu-id="bcc9b-125">Describes this class and has links to all its members..</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bcc9b-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="bcc9b-126">Related Sections</span></span>  
 [<span data-ttu-id="bcc9b-127">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="bcc9b-127">Controls You Can Use On Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="bcc9b-128">Windows フォーム コントロールの完全な一覧を、使用に関する情報リンクと共に提供します。</span><span class="sxs-lookup"><span data-stu-id="bcc9b-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
