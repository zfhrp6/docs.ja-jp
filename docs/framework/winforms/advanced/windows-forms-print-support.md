---
title: "Windows フォームにおける印刷のサポート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 81f89ee41eb9f8b492ab12e30ae4580cdffbd8f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-print-support"></a><span data-ttu-id="1cf42-102">Windows フォームにおける印刷のサポート</span><span class="sxs-lookup"><span data-stu-id="1cf42-102">Windows Forms Print Support</span></span>
<span data-ttu-id="1cf42-103">Windows フォームにおける印刷は、主に使用して、 [PrintDocument コンポーネント](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)を印刷するユーザーを有効にするコンポーネントと[PrintPreviewDialog コントロール](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)コントロール、 [PrintDialogコンポーネント](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)と[PageSetupDialog コンポーネント](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)Windows オペレーティング システムに慣れているユーザーが使い慣れたグラフィカル インターフェイスを提供するコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="1cf42-103">Printing in Windows Forms consists primarily of using the [PrintDocument Component](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) component to enable the user to print, and the [PrintPreviewDialog Control](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md) control, [PrintDialog Component](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) and [PageSetupDialog Component](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) components to provide a familiar graphical interface to users accustomed to the Windows operating system.</span></span>  
  
 <span data-ttu-id="1cf42-104">通常の新しいインスタンスを作成、<xref:System.Drawing.Printing.PrintDocument>コンポーネント、設定を使用して印刷する対象を記述するプロパティ、<xref:System.Drawing.Printing.PrinterSettings>と<xref:System.Drawing.Printing.PageSettings>クラス、および呼び出し、<xref:System.Drawing.Printing.PrintDocument.Print%2A>を実際には、ドキュメントを印刷する方法です。</span><span class="sxs-lookup"><span data-stu-id="1cf42-104">Typically, you create a new instance of the <xref:System.Drawing.Printing.PrintDocument> component, set the properties that describe what to print using the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to actually print the document.</span></span>  
  
 <span data-ttu-id="1cf42-105">Windows ベースのアプリケーションからの印刷の実行中に、<xref:System.Drawing.Printing.PrintDocument>コンポーネントは中止印刷 ダイアログ ボックスをユーザーに表示アラート印刷が発生しているという事実にし、印刷ジョブをキャンセルできません。</span><span class="sxs-lookup"><span data-stu-id="1cf42-105">During the course of printing from a Windows-based application, the <xref:System.Drawing.Printing.PrintDocument> component will show an abort print dialog box to alert users to the fact that printing is occurring and to allow the print job to be canceled.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1cf42-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="1cf42-106">In This Section</span></span>  
 [<span data-ttu-id="1cf42-107">方法: 標準の Windows フォーム印刷ジョブを作成する</span><span class="sxs-lookup"><span data-stu-id="1cf42-107">How to: Create Standard Windows Forms Print Jobs</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 <span data-ttu-id="1cf42-108">使用する方法について説明します、<xref:System.Drawing.Printing.PrintDocument>から Windows フォームを印刷するコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="1cf42-108">Explains how to use the <xref:System.Drawing.Printing.PrintDocument> component to print from a Windows Form.</span></span>  
  
 [<span data-ttu-id="1cf42-109">方法: 実行時に PrintDialog のユーザー入力をキャプチャする</span><span class="sxs-lookup"><span data-stu-id="1cf42-109">How to: Capture User Input from a PrintDialog at Run Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 <span data-ttu-id="1cf42-110">選択した印刷オプションを使用してプログラムから変更する方法について説明します、<xref:System.Windows.Forms.PrintDialog>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="1cf42-110">Explains how to modify selected print options programmatically using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="1cf42-111">方法: Windows フォームでユーザーのコンピューターに接続されたプリンターを選択する</span><span class="sxs-lookup"><span data-stu-id="1cf42-111">How to: Choose the Printers Attached to a User's Computer in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 <span data-ttu-id="1cf42-112">印刷を使用するプリンターの変更について説明します、<xref:System.Windows.Forms.PrintDialog>実行時コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="1cf42-112">Describes changing the printer to print to using the <xref:System.Windows.Forms.PrintDialog> component at run time.</span></span>  
  
 [<span data-ttu-id="1cf42-113">方法: Windows フォームでグラフィックスを印刷する</span><span class="sxs-lookup"><span data-stu-id="1cf42-113">How to: Print Graphics in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)  
 <span data-ttu-id="1cf42-114">プリンターに送信側のグラフィックスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="1cf42-114">Describes sending graphics to the printer.</span></span>  
  
 [<span data-ttu-id="1cf42-115">方法: Windows フォームで複数ページのテキスト ファイルを印刷する</span><span class="sxs-lookup"><span data-stu-id="1cf42-115">How to: Print a Multi-Page Text File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 <span data-ttu-id="1cf42-116">プリンターに送信するテキストを説明します。</span><span class="sxs-lookup"><span data-stu-id="1cf42-116">Describes sending text to the printer.</span></span>  
  
 [<span data-ttu-id="1cf42-117">方法: Windows フォームの印刷ジョブを完了する</span><span class="sxs-lookup"><span data-stu-id="1cf42-117">How to: Complete Windows Forms Print Jobs</span></span>](../../../../docs/framework/winforms/advanced/how-to-complete-windows-forms-print-jobs.md)  
 <span data-ttu-id="1cf42-118">印刷ジョブの完了をユーザーに通知する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1cf42-118">Explains how to alert users to the completion of a print job.</span></span>  
  
 [<span data-ttu-id="1cf42-119">方法: Windows フォームを印刷する</span><span class="sxs-lookup"><span data-stu-id="1cf42-119">How to: Print a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-a-windows-form.md)  
 <span data-ttu-id="1cf42-120">現在のフォームのコピーを印刷する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1cf42-120">Shows how to print a copy of the current form.</span></span>  
  
 [<span data-ttu-id="1cf42-121">方法: Windows フォームで印刷プレビューを使用して印刷する</span><span class="sxs-lookup"><span data-stu-id="1cf42-121">How to: Print in Windows Forms Using Print Preview</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md)  
 <span data-ttu-id="1cf42-122">使用する方法を示します、<xref:System.Windows.Forms.PrintPreviewDialog>ドキュメントを印刷します。</span><span class="sxs-lookup"><span data-stu-id="1cf42-122">Shows how to use a <xref:System.Windows.Forms.PrintPreviewDialog> for printing a document.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1cf42-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="1cf42-123">Related Sections</span></span>  
 [<span data-ttu-id="1cf42-124">PrintDocument コンポーネント</span><span class="sxs-lookup"><span data-stu-id="1cf42-124">PrintDocument Component</span></span>](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)  
 <span data-ttu-id="1cf42-125">使用方法を説明、<xref:System.Drawing.Printing.PrintDocument>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="1cf42-125">Explains usage of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 [<span data-ttu-id="1cf42-126">PrintDialog コンポーネント</span><span class="sxs-lookup"><span data-stu-id="1cf42-126">PrintDialog Component</span></span>](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 <span data-ttu-id="1cf42-127">使用方法を説明、<xref:System.Windows.Forms.PrintDialog>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="1cf42-127">Explains usage of the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="1cf42-128">PrintPreviewDialog コントロール</span><span class="sxs-lookup"><span data-stu-id="1cf42-128">PrintPreviewDialog Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 <span data-ttu-id="1cf42-129">使用方法を説明、<xref:System.Windows.Forms.PrintPreviewDialog>コントロール。</span><span class="sxs-lookup"><span data-stu-id="1cf42-129">Explains usage of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
 [<span data-ttu-id="1cf42-130">PageSetupDialog コンポーネント</span><span class="sxs-lookup"><span data-stu-id="1cf42-130">PageSetupDialog Component</span></span>](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)  
 <span data-ttu-id="1cf42-131">使用方法を説明、<xref:System.Windows.Forms.PageSetupDialog>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="1cf42-131">Explains usage of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="1cf42-132">内のクラスをについて説明します、<xref:System.Drawing.Printing>名前空間。</span><span class="sxs-lookup"><span data-stu-id="1cf42-132">Describes the classes in the <xref:System.Drawing.Printing> namespace.</span></span>
