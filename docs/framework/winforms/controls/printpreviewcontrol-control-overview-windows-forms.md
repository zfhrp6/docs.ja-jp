---
title: "PrintPreviewControl コントロールの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 47bef441b01d8bdcf9a365c341005cff28c64f27
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a><span data-ttu-id="864e1-102">PrintPreviewControl コントロールの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="864e1-102">PrintPreviewControl Control Overview (Windows Forms)</span></span>
<span data-ttu-id="864e1-103">Windows フォーム<xref:System.Windows.Forms.PrintPreviewControl>表示に使用される、 [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)印刷されたときに表示されます。</span><span class="sxs-lookup"><span data-stu-id="864e1-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> is used to display a [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) as it will appear when printed.</span></span> <span data-ttu-id="864e1-104">このコントロールには、ボタンやその他のユーザー インターフェイスの要素がないため、通常は、独自の印刷プレビューのユーザー インターフェイスを作成する場合にのみ <xref:System.Windows.Forms.PrintPreviewControl> を使用します。</span><span class="sxs-lookup"><span data-stu-id="864e1-104">This control has no buttons or other user interface elements, so typically you use the <xref:System.Windows.Forms.PrintPreviewControl> only if you wish to write your own print-preview user interface.</span></span> <span data-ttu-id="864e1-105">標準のユーザー インターフェイスを実行する場合に、使用、<xref:System.Windows.Forms.PrintPreviewDialog>制御; を参照してください[PrintPreviewDialog コントロールの概要](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md)の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="864e1-105">If you want the standard user interface, use a <xref:System.Windows.Forms.PrintPreviewDialog> control; see [PrintPreviewDialog Control Overview](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md) for an overview.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="864e1-106">キー プロパティ</span><span class="sxs-lookup"><span data-stu-id="864e1-106">Key Properties</span></span>  
 <span data-ttu-id="864e1-107">コントロールのキー プロパティは<xref:System.Windows.Forms.PrintPreviewControl.Document%2A>、プレビューするドキュメントを設定します。</span><span class="sxs-lookup"><span data-stu-id="864e1-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="864e1-108">ドキュメントがある必要があります、<xref:System.Drawing.Printing.PrintDocument>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="864e1-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="864e1-109">印刷するドキュメントの作成の概要については、次を参照してください。 [PrintDocument コンポーネントの概要](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md)と[Windows フォームにおける印刷のサポート](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)です。</span><span class="sxs-lookup"><span data-stu-id="864e1-109">For an overview of creating documents for printing, see [PrintDocument Component Overview](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md) and [Windows Forms Print Support](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md).</span></span> <span data-ttu-id="864e1-110"><xref:System.Windows.Forms.PrintPreviewControl.Columns%2A>と<xref:System.Windows.Forms.PrintPreviewControl.Rows%2A>プロパティがコントロールの水平方向および垂直方向に表示されているページの数を決定します。</span><span class="sxs-lookup"><span data-stu-id="864e1-110">The <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="864e1-111">アンチ エイリアスが滑らかにテキストを行うことができます。 が、低速です。 表示することもできます。これを使用する設定、<xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="864e1-111">Antialiasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> property to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="864e1-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="864e1-112">See Also</span></span>  
 <xref:System.Windows.Forms.PrintPreviewControl>  
 [<span data-ttu-id="864e1-113">PrintPreviewDialog コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="864e1-113">PrintPreviewDialog Control Overview</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md)  
 [<span data-ttu-id="864e1-114">PrintPreviewControl コントロール</span><span class="sxs-lookup"><span data-stu-id="864e1-114">PrintPreviewControl Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-windows-forms.md)  
 [<span data-ttu-id="864e1-115">ダイアログ ボックス コントロールおよびコンポーネント</span><span class="sxs-lookup"><span data-stu-id="864e1-115">Dialog-Box Controls and Components</span></span>](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
