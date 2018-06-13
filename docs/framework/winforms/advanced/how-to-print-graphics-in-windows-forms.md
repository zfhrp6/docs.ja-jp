---
title: '方法 : Windows フォームでグラフィックスを印刷する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], printing
- printing [Windows Forms], graphics
ms.assetid: 32b891e6-52ff-4fea-a9ff-2ce5db20a4c6
ms.openlocfilehash: 8281e1e0a3d350c3b81e26bbe59c098536ef064e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521499"
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
  
     (Visual c# と[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)])、イベント ハンドラーを登録するフォームのコンス トラクターに次のコードを追加します。  
  
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
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.Graphics>  
 <xref:System.Drawing.Brush>  
 [Windows フォームにおける印刷のサポート](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
