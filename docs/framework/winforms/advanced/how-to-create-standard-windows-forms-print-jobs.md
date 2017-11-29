---
title: "方法 : 標準の Windows フォーム印刷ジョブを作成する"
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
- printing [Windows Forms]
- printing [Windows Forms], creating print jobs
- printing [Visual Basic], in Windows applications
ms.assetid: 03342b90-9cfe-40b2-838b-b479a13c5dea
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c2b0ce30f76fe7f8cbdc156c4a8ff5abffafae10
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a><span data-ttu-id="61db0-102">方法 : 標準の Windows フォーム印刷ジョブを作成する</span><span class="sxs-lookup"><span data-stu-id="61db0-102">How to: Create Standard Windows Forms Print Jobs</span></span>
<span data-ttu-id="61db0-103">Windows フォームにおける印刷の基盤となるは、<xref:System.Drawing.Printing.PrintDocument>コンポーネント-具体的には、<xref:System.Drawing.Printing.PrintDocument.PrintPage>イベント。</span><span class="sxs-lookup"><span data-stu-id="61db0-103">The foundation of printing in Windows Forms is the <xref:System.Drawing.Printing.PrintDocument> component—more specifically, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span> <span data-ttu-id="61db0-104">処理するコードを記述して、<xref:System.Drawing.Printing.PrintDocument.PrintPage>イベント、印刷する対象とそれを印刷する方法を指定できます。</span><span class="sxs-lookup"><span data-stu-id="61db0-104">By writing code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event, you can specify what to print and how to print it.</span></span>  
  
### <a name="to-create-a-print-job"></a><span data-ttu-id="61db0-105">印刷ジョブを作成するには</span><span class="sxs-lookup"><span data-stu-id="61db0-105">To create a print job</span></span>  
  
1.  <span data-ttu-id="61db0-106">追加、<xref:System.Drawing.Printing.PrintDocument>コンポーネントをフォームにします。</span><span class="sxs-lookup"><span data-stu-id="61db0-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2.  <span data-ttu-id="61db0-107"><xref:System.Drawing.Printing.PrintDocument.PrintPage> イベントを処理するコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="61db0-107">Write code to handle the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     <span data-ttu-id="61db0-108">コード、独自のロジックを印刷する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61db0-108">You will have to code your own printing logic.</span></span> <span data-ttu-id="61db0-109">さらに、印刷する対象を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="61db0-109">Additionally, you will have to specify the material to be printed.</span></span>  
  
     <span data-ttu-id="61db0-110">次のコード例では赤い長方形の形状のサンプル画像を作成、<xref:System.Drawing.Printing.PrintDocument.PrintPage>イベント ハンドラーを印刷する対象として機能します。</span><span class="sxs-lookup"><span data-stu-id="61db0-110">In the following code example, a sample graphic in the shape of a red rectangle is created in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler to act as material to be printed.</span></span>  
  
    ```vb  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,   
         new Rectangle(500, 500, 500, 500));  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Red,  
             Rectangle(500, 500, 500, 500));  
       }  
    ```  
  
     <span data-ttu-id="61db0-111">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] および [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) フォームのコンストラクターに次のコードを追加して、イベント ハンドラーを登録します。</span><span class="sxs-lookup"><span data-stu-id="61db0-111">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    ```  
  
    ```cpp  
    printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    ```  
  
     <span data-ttu-id="61db0-112">コードを記述することも、<xref:System.Drawing.Printing.PrintDocument.BeginPrint>と<xref:System.Drawing.Printing.PrintDocument.EndPrint>などを表す整数のページの合計数を印刷するデクリメントされる各ページを印刷するイベントです。</span><span class="sxs-lookup"><span data-stu-id="61db0-112">You may also want to write code for the <xref:System.Drawing.Printing.PrintDocument.BeginPrint> and <xref:System.Drawing.Printing.PrintDocument.EndPrint> events, perhaps including an integer representing the total number of pages to print that is decremented as each page prints.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="61db0-113">追加することができます、<xref:System.Windows.Forms.PrintDialog>コンポーネントをフォームにユーザーに、クリーンで効率的なユーザー インターフェイス (UI) を提供します。</span><span class="sxs-lookup"><span data-stu-id="61db0-113">You can add a <xref:System.Windows.Forms.PrintDialog> component to your form to provide a clean and efficient user interface (UI) to your users.</span></span> <span data-ttu-id="61db0-114">設定、<xref:System.Windows.Forms.PrintDialog.Document%2A>のプロパティ、<xref:System.Windows.Forms.PrintDialog>フォームでを処理するドキュメントを印刷に関連するプロパティを設定するコンポーネントを有効します。</span><span class="sxs-lookup"><span data-stu-id="61db0-114">Setting the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> component enables you to set properties related to the print document you are working with on your form.</span></span> <span data-ttu-id="61db0-115">詳細については、<xref:System.Windows.Forms.PrintDialog>コンポーネントを参照してください[PrintDialog コンポーネント](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="61db0-115">For more information about the <xref:System.Windows.Forms.PrintDialog> component, see [PrintDialog Component](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md).</span></span>  
  
     <span data-ttu-id="61db0-116">Windows フォームの詳細については、プログラムで印刷ジョブを作成する方法を含む、印刷ジョブを参照してください<xref:System.Drawing.Printing.PrintPageEventArgs>です。</span><span class="sxs-lookup"><span data-stu-id="61db0-116">For more information about the specifics of Windows Forms print jobs, including how to create a print job programmatically, see <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61db0-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="61db0-117">See Also</span></span>  
 <xref:System.Drawing.Printing.PrintDocument>  
 [<span data-ttu-id="61db0-118">Windows フォームにおける印刷のサポート</span><span class="sxs-lookup"><span data-stu-id="61db0-118">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
