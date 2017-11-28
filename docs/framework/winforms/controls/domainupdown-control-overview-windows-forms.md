---
title: "DomainUpDown コントロールの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a0692677b8ef596bb31b1869480603573a9ec98d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="domainupdown-control-overview-windows-forms"></a><span data-ttu-id="7fa5f-102">DomainUpDown コントロールの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="7fa5f-102">DomainUpDown Control Overview (Windows Forms)</span></span>
<span data-ttu-id="7fa5f-103">Windows フォーム<xref:System.Windows.Forms.DomainUpDown>コントロールは基本的にテキスト ボックスの組み合わせや組の一覧を上または下に移動するためのボタンです。</span><span class="sxs-lookup"><span data-stu-id="7fa5f-103">The Windows Forms <xref:System.Windows.Forms.DomainUpDown> control is essentially a combination of a text box and a pair of buttons for moving up or down through a list.</span></span> <span data-ttu-id="7fa5f-104">コントロールは、表示し、選択肢の一覧から、テキスト文字列を設定します。</span><span class="sxs-lookup"><span data-stu-id="7fa5f-104">The control displays and sets a text string from a list of choices.</span></span> <span data-ttu-id="7fa5f-105">上下一覧内を移動するボタンをクリックして、上下の矢印キーを押すことによって、または、リスト内の項目に一致する文字列を入力して、ユーザーは、文字列を選択できます。</span><span class="sxs-lookup"><span data-stu-id="7fa5f-105">The user can select the string by clicking up and down buttons to move through a list, by pressing the UP and DOWN ARROW keys, or by typing a string that matches an item in the list.</span></span> <span data-ttu-id="7fa5f-106">このコントロールの用途の 1 つでは、名前のアルファベット順に並べ替えられたリストから項目を選択するためです。</span><span class="sxs-lookup"><span data-stu-id="7fa5f-106">One possible use for this control is for selecting items from an alphabetically sorted list of names.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7fa5f-107">一覧を並べ替えるには設定、<xref:System.Windows.Forms.DomainUpDown.Sorted%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="7fa5f-107">To sort the list, set the <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="7fa5f-108">このコントロールの機能は、リスト ボックスまたはコンボ ボックスによく似ていますが、非常に小さい領域を占有します。</span><span class="sxs-lookup"><span data-stu-id="7fa5f-108">The function of this control is very similar to the list box or combo box, but it takes up very little space.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="7fa5f-109">主要プロパティ</span><span class="sxs-lookup"><span data-stu-id="7fa5f-109">Key Properties</span></span>  
 <span data-ttu-id="7fa5f-110">コントロールのプロパティは<xref:System.Windows.Forms.DomainUpDown.Items%2A>、 <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>、および<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>です。</span><span class="sxs-lookup"><span data-stu-id="7fa5f-110">The key properties of the control are <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, and <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span></span> <span data-ttu-id="7fa5f-111"><xref:System.Windows.Forms.DomainUpDown.Items%2A>プロパティには、文字列値を持つが、コントロールに表示されるオブジェクトの一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7fa5f-111">The <xref:System.Windows.Forms.DomainUpDown.Items%2A> property contains the list of objects whose text values are displayed in the control.</span></span> <span data-ttu-id="7fa5f-112">場合<xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>に設定されている`false`コントロールは、ユーザーが型し、リスト内の値を内容と一致するテキストを自動的に完了します。</span><span class="sxs-lookup"><span data-stu-id="7fa5f-112">If <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> is set to `false`, the control automatically completes text that the user types and matches it to a value in the list.</span></span> <span data-ttu-id="7fa5f-113">場合<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>に設定されている`true`、スクロールの過去の最後の項目をクリックすると、一覧で、その逆の最初の項目。</span><span class="sxs-lookup"><span data-stu-id="7fa5f-113">If <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> is set to `true`, scrolling past the last item will take you to the first item in the list and vice versa.</span></span> <span data-ttu-id="7fa5f-114">コントロールの主要なメソッドは<xref:System.Windows.Forms.DomainUpDown.UpButton%2A>と<xref:System.Windows.Forms.DomainUpDown.DownButton%2A>です。</span><span class="sxs-lookup"><span data-stu-id="7fa5f-114">The key methods of the control are <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> and <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span></span>  
  
 <span data-ttu-id="7fa5f-115">このコントロールには、テキスト文字列のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7fa5f-115">This control displays only text strings.</span></span> <span data-ttu-id="7fa5f-116">数値を表示するコントロールを実行する場合に、使用、<xref:System.Windows.Forms.NumericUpDown>コントロール。</span><span class="sxs-lookup"><span data-stu-id="7fa5f-116">If you want a control that displays numeric values, use the <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="7fa5f-117">詳細については、次を参照してください。 [NumericUpDown コントロールの概要](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="7fa5f-117">For more information, see [NumericUpDown Control Overview](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fa5f-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="7fa5f-118">See Also</span></span>  
 <xref:System.Windows.Forms.DomainUpDown>  
 [<span data-ttu-id="7fa5f-119">DomainUpDown コントロール</span><span class="sxs-lookup"><span data-stu-id="7fa5f-119">DomainUpDown Control</span></span>](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)
