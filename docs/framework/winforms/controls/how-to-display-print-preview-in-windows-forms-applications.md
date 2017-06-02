---
title: "方法 : Windows フォーム アプリケーションに印刷プレビューを表示する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "例 [Windows フォーム], 印刷プレビュー"
  - "印刷プレビュー, 表示"
  - "印刷 [Windows フォーム], 印刷プレビュー"
ms.assetid: e394134c-0886-4517-bd8d-edc4a3749eb5
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 方法 : Windows フォーム アプリケーションに印刷プレビューを表示する
<xref:System.Windows.Forms.PrintPreviewDialog> コントロールを使用すると、ユーザーは印刷前などにドキュメントを表示できます。  
  
 そのためには、<xref:System.Drawing.Printing.PrintDocument> クラスのインスタンスを指定する必要があります。これが印刷されるドキュメントです。  <xref:System.Drawing.Printing.PrintDocument> コンポーネントでの印刷プレビューの使用の詳細については、「[方法 : Windows フォームで印刷プレビューを使用して印刷する](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md)」を参照してください。  
  
> [!NOTE]
>  実行時に <xref:System.Windows.Forms.PrintPreviewDialog> コントロールを使用するためには、ユーザーがコンピューター上にローカルで、またはネットワークを通じて、プリンターをインストールしている必要があります。<xref:System.Windows.Forms.PrintPreviewDialog> コンポーネントはこのプリンターに応じて、印刷時のドキュメントの外観を決定します。  
  
 <xref:System.Windows.Forms.PrintPreviewDialog> コントロールは <xref:System.Drawing.Printing.PrinterSettings> クラスを使用します。  また、<xref:System.Windows.Forms.PrintPreviewDialog> コントロールは <xref:System.Windows.Forms.PrintPreviewDialog> コンポーネントと同じように <xref:System.Drawing.Printing.PageSettings> クラスを使用します。  <xref:System.Windows.Forms.PrintPreviewDialog> コントロールの <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> プロパティに指定された印刷ドキュメントは、<xref:System.Drawing.Printing.PrinterSettings> クラスと <xref:System.Drawing.Printing.PageSettings> クラスの両方のインスタンスを参照します。その両方を使用してプレビュー ウィンドウにドキュメントが表示されます。  
  
### PrintPreviewDialog コントロールを使用してページを表示するには  
  
-   <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> メソッドを使用してダイアログ ボックスを表示します。このとき、使用する <xref:System.Drawing.Printing.PrintDocument> を指定します。  
  
     次のコード例では、<xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーを使用して <xref:System.Windows.Forms.PrintPreviewDialog> コントロールのインスタンスを開いています。  印刷ドキュメントは、<xref:System.Windows.Forms.PrintDialog.Document%2A> プロパティに指定されます。  次の例では印刷ドキュメントが指定されていません。  
  
     このコード例では、フォームに <xref:System.Windows.Forms.Button> コントロール、`myDocument` という名前の <xref:System.Drawing.Printing.PrintDocument> コンポーネント、および <xref:System.Windows.Forms.PrintPreviewDialog> コントロールが必要です。  
  
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
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) フォームのコンストラクターに次のコードを挿入してイベント ハンドラーを登録します。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## 参照  
 [PrintDocument コンポーネント](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)   
 [PrintPreviewDialog コントロール](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)   
 [Windows フォームにおける印刷のサポート](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)   
 [Windows フォーム](../../../../docs/framework/winforms/index.md)