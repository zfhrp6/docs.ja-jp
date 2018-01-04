---
title: "方法 : Windows フォームでグラフィックスを印刷する"
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
- graphics [Windows Forms], printing
- printing [Windows Forms], graphics
ms.assetid: 32b891e6-52ff-4fea-a9ff-2ce5db20a4c6
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 634689b0b39510cbcc9dc49b1f4717e7e07f88d9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-print-graphics-in-windows-forms"></a><span data-ttu-id="b69fa-102">方法 : Windows フォームでグラフィックスを印刷する</span><span class="sxs-lookup"><span data-stu-id="b69fa-102">How to: Print Graphics in Windows Forms</span></span>
<span data-ttu-id="b69fa-103">多くの場合、Windows ベースのアプリケーションでグラフィックスを印刷するされます。</span><span class="sxs-lookup"><span data-stu-id="b69fa-103">Frequently, you will want to print graphics in your Windows-based application.</span></span> <span data-ttu-id="b69fa-104"><xref:System.Drawing.Graphics>クラス オブジェクトを画面やプリンターなどのデバイスに描画するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="b69fa-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects to a device, such as a screen or printer.</span></span>  
  
### <a name="to-print-graphics"></a><span data-ttu-id="b69fa-105">グラフィックスを印刷するには</span><span class="sxs-lookup"><span data-stu-id="b69fa-105">To print graphics</span></span>  
  
1.  <span data-ttu-id="b69fa-106">追加、<xref:System.Drawing.Printing.PrintDocument>コンポーネントをフォームにします。</span><span class="sxs-lookup"><span data-stu-id="b69fa-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2.  <span data-ttu-id="b69fa-107"><xref:System.Drawing.Printing.PrintDocument.PrintPage>イベント ハンドラーを使用して、<xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A>のプロパティ、<xref:System.Drawing.Printing.PrintPageEventArgs>にどのようなグラフィックスを印刷するプリンターを指示するクラス。</span><span class="sxs-lookup"><span data-stu-id="b69fa-107">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class to instruct the printer on what kind of graphics to print.</span></span>  
  
     <span data-ttu-id="b69fa-108">次のコード例は、外接する四角形内に青い楕円の作成に使用されるイベント ハンドラーを示しています。</span><span class="sxs-lookup"><span data-stu-id="b69fa-108">The following code example shows an event handler used to create a blue ellipse within a bounding rectangle.</span></span> <span data-ttu-id="b69fa-109">四角形は、次の場所とサイズ: 100 から始まる 250 の幅と高さは 250 150。</span><span class="sxs-lookup"><span data-stu-id="b69fa-109">The rectangle has the following location and dimensions: beginning at 100, 150 with a width of 250 and a height of 250.</span></span>  
  
    ```vb  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillEllipse(Brushes.Blue, New Rectangle(100, 150, 250, 250))  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Blue,   
         new Rectangle(100, 150, 250, 250));  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Blue,  
             Rectangle(100, 150, 250, 250));  
       }  
    ```  
  
     <span data-ttu-id="b69fa-110">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] および [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) フォームのコンストラクターに次のコードを追加して、イベント ハンドラーを登録します。</span><span class="sxs-lookup"><span data-stu-id="b69fa-110">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    ```  
  
    ```cpp  
    this->printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b69fa-111">参照</span><span class="sxs-lookup"><span data-stu-id="b69fa-111">See Also</span></span>  
 <xref:System.Drawing.Graphics>  
 <xref:System.Drawing.Brush>  
 [<span data-ttu-id="b69fa-112">Windows フォームにおける印刷のサポート</span><span class="sxs-lookup"><span data-stu-id="b69fa-112">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
