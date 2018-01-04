---
title: "方法 : PrintDialog コンポーネントを表示する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d955febe528add4b774766a3b204f96eef5a119d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-the-printdialog-component"></a><span data-ttu-id="7e723-102">方法 : PrintDialog コンポーネントを表示する</span><span class="sxs-lookup"><span data-stu-id="7e723-102">How to: Display the PrintDialog Component</span></span>
<span data-ttu-id="7e723-103"><xref:System.Windows.Forms.PrintDialog>コンポーネントは、多くのユーザーに習熟する標準の Windows 印刷 ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="7e723-103">The <xref:System.Windows.Forms.PrintDialog> component is the standard Windows print dialog box that many of your users will be familiar with.</span></span> <span data-ttu-id="7e723-104">あるため、ユーザーはすぐに慣れる、使用すると役に立つなります、<xref:System.Windows.Forms.PrintDialog>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="7e723-104">Because your users will be immediately comfortable with it, it would be beneficial for you to use the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
### <a name="to-display-the-printdialog-component"></a><span data-ttu-id="7e723-105">PrintDialog コンポーネントを表示するには</span><span class="sxs-lookup"><span data-stu-id="7e723-105">To display the PrintDialog component</span></span>  
  
-   <span data-ttu-id="7e723-106">呼び出す、<xref:System.Windows.Forms.Form.ShowDialog%2A>メソッド アプリケーションのコード内からです。</span><span class="sxs-lookup"><span data-stu-id="7e723-106">Call the <xref:System.Windows.Forms.Form.ShowDialog%2A> method from within the code of your application.</span></span>  
  
     <span data-ttu-id="7e723-107">コンポーネントが表示されると、ユーザーはそれを使用して印刷ジョブのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="7e723-107">Once the component is shown, users will interact with it, setting the properties of the print job.</span></span> <span data-ttu-id="7e723-108">これらに保存、 <!--zz <xref:System.Drawing.Printing.PrinterSetting>--> `PrinterSetting`クラス (および<xref:System.Drawing.Printing.PageSettings>クラス、ユーザーがアクセスする場合、 [PageSetupDialog コンポーネント](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)を通じて、<xref:System.Windows.Forms.PrintDialog>コンポーネント) その印刷ジョブに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="7e723-108">These are saved in the <!--zz <xref:System.Drawing.Printing.PrinterSetting>--> `PrinterSetting` class (and the <xref:System.Drawing.Printing.PageSettings> class, if the user accesses the [PageSetupDialog Component](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) through the <xref:System.Windows.Forms.PrintDialog> component) associated with that print job.</span></span> <span data-ttu-id="7e723-109">その後で、設定されたプロパティを呼び出して印刷ジョブの詳細を確認できます。</span><span class="sxs-lookup"><span data-stu-id="7e723-109">You can then make calls to the properties they set to determine the specifics of the print job.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e723-110">参照</span><span class="sxs-lookup"><span data-stu-id="7e723-110">See Also</span></span>  
 [<span data-ttu-id="7e723-111">方法: 標準の Windows フォーム印刷ジョブを作成する</span><span class="sxs-lookup"><span data-stu-id="7e723-111">How to: Create Standard Windows Forms Print Jobs</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 [<span data-ttu-id="7e723-112">方法: 実行時に PrintDialog のユーザー入力をキャプチャする</span><span class="sxs-lookup"><span data-stu-id="7e723-112">How to: Capture User Input from a PrintDialog at Run Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 [<span data-ttu-id="7e723-113">PrintPreviewDialog コントロール</span><span class="sxs-lookup"><span data-stu-id="7e723-113">PrintPreviewDialog Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [<span data-ttu-id="7e723-114">PrintDialog コンポーネント</span><span class="sxs-lookup"><span data-stu-id="7e723-114">PrintDialog Component</span></span>](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 [<span data-ttu-id="7e723-115">Windows フォームにおける印刷のサポート</span><span class="sxs-lookup"><span data-stu-id="7e723-115">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [<span data-ttu-id="7e723-116">Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="7e723-116">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)
