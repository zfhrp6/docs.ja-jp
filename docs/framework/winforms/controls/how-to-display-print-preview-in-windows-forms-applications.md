---
title: '方法 : Windows フォーム アプリケーションに印刷プレビューを表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print preview [Windows Forms], displaying
- printing [Windows Forms], print preview
- examples [Windows Forms], print preview
ms.assetid: e394134c-0886-4517-bd8d-edc4a3749eb5
ms.openlocfilehash: 1c1291ea675d823fab3052b0fa365cb2d4c31088
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532809"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a>方法 : Windows フォーム アプリケーションに印刷プレビューを表示する
使用することができます、<xref:System.Windows.Forms.PrintPreviewDialog>を印刷する前に多くの場合、ドキュメントを表示するユーザーを有効にするコントロール。  
  
 これを行うには、インスタンスを指定する必要があります、<xref:System.Drawing.Printing.PrintDocument>クラスです。 これは、印刷するドキュメントです。 印刷プレビューでの使用の詳細については、<xref:System.Drawing.Printing.PrintDocument>コンポーネントを参照してください[する方法: Windows フォームを使用して印刷プレビューで印刷](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md)です。  
  
> [!NOTE]
>  使用する、<xref:System.Windows.Forms.PrintPreviewDialog>制御、実行時にユーザーが必要ローカルまたはネットワークを介して、自分のコンピューターにインストールされているプリンターは部分的方法、<xref:System.Windows.Forms.PrintPreviewDialog>コンポーネントは、印刷されたときに、ドキュメントがどのように表示されるかを決定します。  
  
 <xref:System.Windows.Forms.PrintPreviewDialog>コントロール、<xref:System.Drawing.Printing.PrinterSettings>クラスです。 さらに、<xref:System.Windows.Forms.PrintPreviewDialog>コントロール、<xref:System.Drawing.Printing.PageSettings>クラスと同様に、<xref:System.Windows.Forms.PrintPreviewDialog>はコンポーネントです。 指定した印刷ドキュメント、<xref:System.Windows.Forms.PrintPreviewDialog>コントロールの<xref:System.Windows.Forms.PrintPreviewControl.Document%2A>プロパティが両方のインスタンスを指す、<xref:System.Drawing.Printing.PrinterSettings>と<xref:System.Drawing.Printing.PageSettings>クラス、およびこれらは、プレビュー ウィンドウ内のドキュメントを表示するために使用します。  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a>PrintPreviewDialog コントロールを使用してページを表示するには  
  
-   <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> メソッドを使用してダイアログ ボックスを表示し、使用する <xref:System.Drawing.Printing.PrintDocument> を指定します。  
  
     次のコード例では、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Click>イベント ハンドラーのインスタンスを開き、<xref:System.Windows.Forms.PrintPreviewDialog>コントロール。 印刷ドキュメントがで指定された、<xref:System.Windows.Forms.PrintDialog.Document%2A>プロパティです。 次の例では、印刷ドキュメントが指定されていません。  
  
     この例では、フォームがある必要があります、<xref:System.Windows.Forms.Button>コントロール、<xref:System.Drawing.Printing.PrintDocument>という名前のコンポーネント`myDocument`、および<xref:System.Windows.Forms.PrintPreviewDialog>コントロール。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       ' The print document 'myDocument' used below  
       ' is merely for an example.  
       ' You will have to specify your own print document.  
       PrintPreviewDialog1.Document = myDocument  
       PrintPreviewDialog1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // The print document 'myDocument' used below  
       // is merely for an example.  
       // You will have to specify your own print document.  
       printPreviewDialog1.Document = myDocument;  
       printPreviewDialog1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // The print document 'myDocument' used below  
          // is merely for an example.  
          // You will have to specify your own print document.  
          printPreviewDialog1->Document = myDocument;  
          printPreviewDialog1->ShowDialog();  
       }  
    ```  
  
     (Visual C# の場合、 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)])、イベント ハンドラーを登録するフォームのコンス トラクターに次のコードを追加します。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>関連項目  
 [PrintDocument コンポーネント](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)  
 [PrintPreviewDialog コントロール](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [Windows フォームにおける印刷のサポート](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [Windows フォーム](../../../../docs/framework/winforms/index.md)
