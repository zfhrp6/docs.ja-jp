---
title: '方法 : 標準の Windows フォーム印刷ジョブを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms]
- printing [Windows Forms], creating print jobs
- printing [Visual Basic], in Windows applications
ms.assetid: 03342b90-9cfe-40b2-838b-b479a13c5dea
ms.openlocfilehash: b580268a6af3f56f240a1c511c3d473a4a5ddc15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522334"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>方法 : 標準の Windows フォーム印刷ジョブを作成する
Windows フォームにおける印刷の基盤となるは、<xref:System.Drawing.Printing.PrintDocument>コンポーネント-具体的には、<xref:System.Drawing.Printing.PrintDocument.PrintPage>イベント。 処理するコードを記述して、<xref:System.Drawing.Printing.PrintDocument.PrintPage>イベント、印刷する対象とそれを印刷する方法を指定できます。  
  
### <a name="to-create-a-print-job"></a>印刷ジョブを作成するには  
  
1.  追加、<xref:System.Drawing.Printing.PrintDocument>コンポーネントをフォームにします。  
  
2.  <xref:System.Drawing.Printing.PrintDocument.PrintPage> イベントを処理するコードを記述します。  
  
     コード、独自のロジックを印刷する必要があります。 さらに、印刷する対象を指定する必要があります。  
  
     次のコード例では赤い長方形の形状のサンプル画像を作成、<xref:System.Drawing.Printing.PrintDocument.PrintPage>イベント ハンドラーを印刷する対象として機能します。  
  
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
  
     (Visual c# と[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)])、イベント ハンドラーを登録するフォームのコンス トラクターに次のコードを追加します。  
  
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
  
     コードを記述することも、<xref:System.Drawing.Printing.PrintDocument.BeginPrint>と<xref:System.Drawing.Printing.PrintDocument.EndPrint>などを表す整数のページの合計数を印刷するデクリメントされる各ページを印刷するイベントです。  
  
    > [!NOTE]
    >  追加することができます、<xref:System.Windows.Forms.PrintDialog>コンポーネントをフォームにユーザーに、クリーンで効率的なユーザー インターフェイス (UI) を提供します。 設定、<xref:System.Windows.Forms.PrintDialog.Document%2A>のプロパティ、<xref:System.Windows.Forms.PrintDialog>フォームでを処理するドキュメントを印刷に関連するプロパティを設定するコンポーネントを有効します。 詳細については、<xref:System.Windows.Forms.PrintDialog>コンポーネントを参照してください[PrintDialog コンポーネント](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)です。  
  
     Windows フォームの詳細については、プログラムで印刷ジョブを作成する方法を含む、印刷ジョブを参照してください<xref:System.Drawing.Printing.PrintPageEventArgs>です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.Printing.PrintDocument>  
 [Windows フォームにおける印刷のサポート](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
