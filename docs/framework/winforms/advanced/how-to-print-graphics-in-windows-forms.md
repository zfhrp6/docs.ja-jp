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
# <a name="how-to-print-graphics-in-windows-forms"></a>方法 : Windows フォームでグラフィックスを印刷する
多くの場合、Windows ベースのアプリケーションでグラフィックスを印刷するされます。 <xref:System.Drawing.Graphics>クラス オブジェクトを画面やプリンターなどのデバイスに描画するためのメソッドを提供します。  
  
### <a name="to-print-graphics"></a>グラフィックスを印刷するには  
  
1.  追加、<xref:System.Drawing.Printing.PrintDocument>コンポーネントをフォームにします。  
  
2.  <xref:System.Drawing.Printing.PrintDocument.PrintPage>イベント ハンドラーを使用して、<xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A>のプロパティ、<xref:System.Drawing.Printing.PrintPageEventArgs>にどのようなグラフィックスを印刷するプリンターを指示するクラス。  
  
     次のコード例は、外接する四角形内に青い楕円の作成に使用されるイベント ハンドラーを示しています。 四角形は、次の場所とサイズ: 100 から始まる 250 の幅と高さは 250 150。  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] および [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) フォームのコンストラクターに次のコードを追加して、イベント ハンドラーを登録します。  
  
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
  
## <a name="see-also"></a>参照  
 <xref:System.Drawing.Graphics>  
 <xref:System.Drawing.Brush>  
 [Windows フォームにおける印刷のサポート](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
