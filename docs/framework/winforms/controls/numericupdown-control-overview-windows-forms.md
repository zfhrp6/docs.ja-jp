---
title: "NumericUpDown コントロールの概要 (Windows フォーム)"
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
- NumericUpDown
helpviewer_keywords:
- numeric spin button control [Windows Forms], Windows Forms
- NumericUpDown control [Windows Forms], about NumericUpDown control
- spin button control [Windows Forms], Windows Forms
ms.assetid: cff3cf30-4d46-4381-87df-37bfe83c71c5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 067a8862ee991213e584819e1cf99eddde06e2bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="numericupdown-control-overview-windows-forms"></a><span data-ttu-id="d8588-102">NumericUpDown コントロールの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="d8588-102">NumericUpDown Control Overview (Windows Forms)</span></span>
<span data-ttu-id="d8588-103"><xref:System.Windows.Forms.NumericUpDown>コントロールはテキスト ボックスの組み合わせと、値を調整するユーザーがクリックする矢印のペアのようになります。</span><span class="sxs-lookup"><span data-stu-id="d8588-103">The <xref:System.Windows.Forms.NumericUpDown> control looks like a combination of a text box and a pair of arrows that the user can click to adjust a value.</span></span> <span data-ttu-id="d8588-104">コントロールは、表示し、固定の数値の選択肢の一覧から 1 つの数値を設定します。</span><span class="sxs-lookup"><span data-stu-id="d8588-104">The control displays and sets a single numeric value from a list of fixed numeric-value choices.</span></span> <span data-ttu-id="d8588-105">ユーザーは大きくなり、上下の矢印キーを押すか、テキスト ボックス コントロールの一部に数値を入力と下向きの矢印をクリックして、番号が低下します。</span><span class="sxs-lookup"><span data-stu-id="d8588-105">The user can increase and decrease the number by clicking the up and down arrows, by pressing the UP and DOWN ARROW keys, or by typing a number in the text box part of the control.</span></span> <span data-ttu-id="d8588-106">上矢印キーをクリックすると、数値が最大値です。 方向を移動します。数値、最小値の方向に移動、下方向キーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d8588-106">Clicking the UP ARROW key moves the number toward the maximum; clicking the DOWN ARROW key moves the number toward the minimum.</span></span>  
  
 <span data-ttu-id="d8588-107">多用途の機能のためこのコントロールは、明らかな選択肢では、たとえば、ミュージック プレーヤー アプリケーションのボリューム コントロールを作成する場合です。</span><span class="sxs-lookup"><span data-stu-id="d8588-107">Because of its versatile functionality, this control is an obvious choice, for example, if you want to create a volume control for a music player application.</span></span> <span data-ttu-id="d8588-108"><xref:System.Windows.Forms.NumericUpDown>多くの Windows コントロール パネル アプリケーションでコントロールを使用します。</span><span class="sxs-lookup"><span data-stu-id="d8588-108">The <xref:System.Windows.Forms.NumericUpDown> control is used in many Windows Control Panel applications.</span></span>  
  
## <a name="key-properties-and-methods"></a><span data-ttu-id="d8588-109">キー プロパティとメソッド</span><span class="sxs-lookup"><span data-stu-id="d8588-109">Key Properties and Methods</span></span>  
 <span data-ttu-id="d8588-110">コントロールのテキスト ボックスに表示する数値は 16 進数、さまざまな形式で指定できます。</span><span class="sxs-lookup"><span data-stu-id="d8588-110">The numbers displayed in the control's text box can be in a variety of formats, including hexadecimal.</span></span> <span data-ttu-id="d8588-111">詳細については、次を参照してください。[する方法: Windows フォームの NumericUpDown コントロールの書式を設定](../../../../docs/framework/winforms/controls/how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="d8588-111">For more information, see [How to: Set the Format for the Windows Forms NumericUpDown Control](../../../../docs/framework/winforms/controls/how-to-set-the-format-for-the-windows-forms-numericupdown-control.md).</span></span> <span data-ttu-id="d8588-112">コントロールのプロパティは<xref:System.Windows.Forms.NumericUpDown.Value%2A>、 <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> (既定値は 100)、 <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> (既定値は 0)、および<xref:System.Windows.Forms.NumericUpDown.Increment%2A>(既定値は 1)。</span><span class="sxs-lookup"><span data-stu-id="d8588-112">The key properties of the control are <xref:System.Windows.Forms.NumericUpDown.Value%2A>, <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> (default value 100), <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> (default value 0), and <xref:System.Windows.Forms.NumericUpDown.Increment%2A> (default value 1).</span></span> <span data-ttu-id="d8588-113"><xref:System.Windows.Forms.NumericUpDown.Value%2A>プロパティは、コントロールで選択されている現在の数を設定します。</span><span class="sxs-lookup"><span data-stu-id="d8588-113">The <xref:System.Windows.Forms.NumericUpDown.Value%2A> property sets the current number selected in the control.</span></span> <span data-ttu-id="d8588-114"><xref:System.Windows.Forms.NumericUpDown.Increment%2A>プロパティを設定しますをクリックすると、矢印または下向き矢印数が調整されます。</span><span class="sxs-lookup"><span data-stu-id="d8588-114">The <xref:System.Windows.Forms.NumericUpDown.Increment%2A> property sets the amount that the number is adjusted by when the user clicks an up or down arrow.</span></span> <span data-ttu-id="d8588-115">コントロールからフォーカスが移動、ときに、最小値と最大の数値に対して任意の型指定された入力が検証されます。</span><span class="sxs-lookup"><span data-stu-id="d8588-115">When focus moves off the control, any typed input will be validated against the minimum and maximum numeric values.</span></span> <span data-ttu-id="d8588-116">上矢印を継続的に押す矢印または下向き矢印、数字、を通じてコントロールを移動する速度を上げることで、<xref:System.Windows.Forms.NumericUpDown.Accelerations%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d8588-116">You can increase the speed that the control moves through numbers, when the user continuously presses the up or down arrow, with the <xref:System.Windows.Forms.NumericUpDown.Accelerations%2A> property.</span></span> <span data-ttu-id="d8588-117">コントロールの主要なメソッドは<xref:System.Windows.Forms.NumericUpDown.UpButton%2A>と<xref:System.Windows.Forms.NumericUpDown.DownButton%2A>です。</span><span class="sxs-lookup"><span data-stu-id="d8588-117">The key methods of the control are <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> and <xref:System.Windows.Forms.NumericUpDown.DownButton%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8588-118">参照</span><span class="sxs-lookup"><span data-stu-id="d8588-118">See Also</span></span>  
 <xref:System.Windows.Forms.NumericUpDown>  
 [<span data-ttu-id="d8588-119">NumericUpDown コントロール</span><span class="sxs-lookup"><span data-stu-id="d8588-119">NumericUpDown Control</span></span>](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)  
 [<span data-ttu-id="d8588-120">方法: Windows フォームの NumericUpDown コントロールの書式を設定する</span><span class="sxs-lookup"><span data-stu-id="d8588-120">How to: Set the Format for the Windows Forms NumericUpDown Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)  
 [<span data-ttu-id="d8588-121">TextBox コントロール</span><span class="sxs-lookup"><span data-stu-id="d8588-121">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
