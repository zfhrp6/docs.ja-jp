---
title: "方法 : 実行時に PrintDialog のユーザー入力をキャプチャする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print options [Windows Forms], changing at run time
- printing [Windows Forms], options
- print options
- run time [Windows Forms], changing print options
ms.assetid: 438501d8-9a70-4fb3-aae6-e46579aba0c6
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5fcc2ccc240752c8c54c28fe2358d3ef49cbf3b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-capture-user-input-from-a-printdialog-at-run-time"></a><span data-ttu-id="b393c-102">方法 : 実行時に PrintDialog のユーザー入力をキャプチャする</span><span class="sxs-lookup"><span data-stu-id="b393c-102">How to: Capture User Input from a PrintDialog at Run Time</span></span>
<span data-ttu-id="b393c-103">デザイン時の印刷に関連するオプションを設定できますが、最も可能性の高いユーザーが行う選択により、実行時にこれらのオプションを変更する必要が場合があります。</span><span class="sxs-lookup"><span data-stu-id="b393c-103">While you can set options related to printing at design time, you will sometimes want to change these options at run time, most likely because of choices made by the user.</span></span> <span data-ttu-id="b393c-104">使用してドキュメントを印刷するためのユーザー入力をキャプチャすることができます、<xref:System.Windows.Forms.PrintDialog>と<xref:System.Drawing.Printing.PrintDocument>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="b393c-104">You can capture user input for printing a document using the <xref:System.Windows.Forms.PrintDialog> and the <xref:System.Drawing.Printing.PrintDocument> components.</span></span>  
  
### <a name="to-change-print-options-programmatically"></a><span data-ttu-id="b393c-105">印刷オプションをプログラムで変更するには</span><span class="sxs-lookup"><span data-stu-id="b393c-105">To change print options programmatically</span></span>  
  
1.  <span data-ttu-id="b393c-106">追加、<xref:System.Windows.Forms.PrintDialog>と<xref:System.Drawing.Printing.PrintDocument>コンポーネントをフォームにします。</span><span class="sxs-lookup"><span data-stu-id="b393c-106">Add a <xref:System.Windows.Forms.PrintDialog> and a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2.  <span data-ttu-id="b393c-107">設定、<xref:System.Windows.Forms.PrintDialog.Document%2A>のプロパティ、<xref:System.Windows.Forms.PrintDialog>を<xref:System.Drawing.Printing.PrintDocument>フォームに追加します。</span><span class="sxs-lookup"><span data-stu-id="b393c-107">Set the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> to the <xref:System.Drawing.Printing.PrintDocument> added to the form.</span></span>  
  
    ```vb  
    PrintDialog1.Document = PrintDocument1  
    ```  
  
    ```csharp  
    printDialog1.Document = PrintDocument1;  
    ```  
  
    ```cpp  
    printDialog1->Document = PrintDocument1;  
    ```  
  
3.  <span data-ttu-id="b393c-108">表示、<xref:System.Windows.Forms.PrintDialog>コンポーネントを使用して、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="b393c-108">Display the <xref:System.Windows.Forms.PrintDialog> component by using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
    ```vb  
    PrintDialog1.ShowDialog()  
    ```  
  
    ```csharp  
    printDialog1.ShowDialog();  
    ```  
  
    ```cpp  
    printDialog1->ShowDialog();  
    ```  
  
4.  <span data-ttu-id="b393c-109">ダイアログ ボックスから、ユーザーの印刷オプションをコピーする、<xref:System.Drawing.Printing.PrinterSettings>のプロパティ、<xref:System.Drawing.Printing.PrintDocument>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="b393c-109">The user's printing choices from the dialog will be copied to the <xref:System.Drawing.Printing.PrinterSettings> property of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b393c-110">参照</span><span class="sxs-lookup"><span data-stu-id="b393c-110">See Also</span></span>  
 [<span data-ttu-id="b393c-111">方法: Windows フォームで複数ページのテキスト ファイルを印刷する</span><span class="sxs-lookup"><span data-stu-id="b393c-111">How to: Print a Multi-Page Text File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 [<span data-ttu-id="b393c-112">Windows フォームにおける印刷のサポート</span><span class="sxs-lookup"><span data-stu-id="b393c-112">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
