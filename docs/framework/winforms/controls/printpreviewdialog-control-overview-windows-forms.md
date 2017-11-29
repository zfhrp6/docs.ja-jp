---
title: "PrintPreviewDialog コントロールの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PrintPreviewDialog
helpviewer_keywords: PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3c898dc24c9a4418e3af45fce507e6befcf905a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a><span data-ttu-id="0fae4-102">PrintPreviewDialog コントロールの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="0fae4-102">PrintPreviewDialog Control Overview (Windows Forms)</span></span>
<span data-ttu-id="0fae4-103">Windows フォーム<xref:System.Windows.Forms.PrintPreviewDialog>コントロールは、構成済みのダイアログ ボックスを表示するために使用する方法、 [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)印刷したときに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0fae4-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> control is a pre-configured dialog box used to display how a [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) will appear when printed.</span></span> <span data-ttu-id="0fae4-104">独自のダイアログ ボックスではなく簡易ソリューションとして、Windows ベースのアプリケーションの中で使用します。</span><span class="sxs-lookup"><span data-stu-id="0fae4-104">Use it within your Windows-based application as a simple solution instead of configuring your own dialog box.</span></span> <span data-ttu-id="0fae4-105">このコントロールには、印刷を開始するボタン、ズーム イン用のボタン、1 ページまたは複数ページを表示するボタン、およびダイアログ ボックスを閉じるためのボタンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0fae4-105">The control contains buttons for printing, zooming in, displaying one or multiple pages, and closing the dialog box.</span></span>  
  
## <a name="key-properties-and-methods"></a><span data-ttu-id="0fae4-106">キー プロパティとメソッド</span><span class="sxs-lookup"><span data-stu-id="0fae4-106">Key Properties and Methods</span></span>  
 <span data-ttu-id="0fae4-107">コントロールのキー プロパティは<xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>、プレビューするドキュメントを設定します。</span><span class="sxs-lookup"><span data-stu-id="0fae4-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="0fae4-108">ドキュメントがある必要があります、<xref:System.Drawing.Printing.PrintDocument>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0fae4-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="0fae4-109">ダイアログ ボックスを表示するために呼び出す必要があります、<xref:System.Windows.Forms.Form.ShowDialog%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="0fae4-109">In order to display the dialog box, you must call its <xref:System.Windows.Forms.Form.ShowDialog%2A> method.</span></span> <span data-ttu-id="0fae4-110">アンチ エイリアスが滑らかにテキストを行うことができます。 が、低速です。 表示することもできます。これを使用する設定、<xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="0fae4-110">Anti-aliasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="0fae4-111">特定のプロパティは、<xref:System.Windows.Forms.PrintPreviewControl>を<xref:System.Windows.Forms.PrintPreviewDialog>が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0fae4-111">Certain properties are available through the <xref:System.Windows.Forms.PrintPreviewControl> that the <xref:System.Windows.Forms.PrintPreviewDialog> contains.</span></span> <span data-ttu-id="0fae4-112">(これを追加する必要はありません<xref:System.Windows.Forms.PrintPreviewControl>フォームに含まれている自動的に、<xref:System.Windows.Forms.PrintPreviewDialog>をフォームにダイアログ ボックスを追加するとします)。を通じて使用可能なプロパティの例については、<xref:System.Windows.Forms.PrintPreviewControl>は、<xref:System.Windows.Forms.PrintPreviewControl.Columns%2A>と<xref:System.Windows.Forms.PrintPreviewControl.Rows%2A>プロパティで、コントロールの水平方向および垂直方向に表示されているページの数を決定します。</span><span class="sxs-lookup"><span data-stu-id="0fae4-112">(You do not have to add this <xref:System.Windows.Forms.PrintPreviewControl> to the form; it is automatically contained within the <xref:System.Windows.Forms.PrintPreviewDialog> when you add the dialog to your form.) Examples of properties available through the <xref:System.Windows.Forms.PrintPreviewControl> are the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties, which determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="0fae4-113">アクセスすることができます、<xref:System.Windows.Forms.PrintPreviewControl.Columns%2A>プロパティとして`PrintPreviewDialog1.PrintPreviewControl.Columns`で[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]、`printPreviewDialog1.PrintPreviewControl.Columns`で[!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、または`printPreviewDialog1->PrintPreviewControl->Columns`で[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="0fae4-113">You can access the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> property as `PrintPreviewDialog1.PrintPreviewControl.Columns` in [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], `printPreviewDialog1.PrintPreviewControl.Columns` in [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], or `printPreviewDialog1->PrintPreviewControl->Columns` in [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fae4-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="0fae4-114">See Also</span></span>  
 <xref:System.Windows.Forms.PrintPreviewDialog>  
 [<span data-ttu-id="0fae4-115">PrintPreviewControl コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="0fae4-115">PrintPreviewControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="0fae4-116">PrintPreviewDialog コントロール</span><span class="sxs-lookup"><span data-stu-id="0fae4-116">PrintPreviewDialog Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [<span data-ttu-id="0fae4-117">ダイアログ ボックス コントロールおよびコンポーネント</span><span class="sxs-lookup"><span data-stu-id="0fae4-117">Dialog-Box Controls and Components</span></span>](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
