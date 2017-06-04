---
title: "方法 : Windows フォームでユーザーのコンピューターに接続されたプリンターを選択する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "印刷 [Windows フォーム], プリンターの選択"
  - "プリンター, 選択"
ms.assetid: 63c1172b-2931-4ac0-953f-37f629494bbf
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 方法 : Windows フォームでユーザーのコンピューターに接続されたプリンターを選択する
既定のプリンター以外のプリンターに印刷することがよくあります。<xref:System.Windows.Forms.PrintDialog> コンポーネントを使用すると、現在インストールされているプリンターからユーザーに選択させることができます。<xref:System.Windows.Forms.PrintDialog> コンポーネントでは、<xref:System.Windows.Forms.PrintDialog> コンポーネントの <xref:System.Windows.Forms.DialogResult> がキャプチャされ、プリンターの選択に使用されます。  
  
 次の手順では、既定のプリンターに印刷するテキスト ファイルを選択します。<xref:System.Windows.Forms.PrintDialog> クラスがインスタンス化されます。  
  
### プリンターを選択してファイルを印刷するには  
  
1.  <xref:System.Windows.Forms.PrintDialog> コンポーネントを使用して、使用するプリンターを選択します。  
  
     次のコード例では、2 つのイベントを処理しています。 最初の <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Click> イベントでは、<xref:System.Windows.Forms.PrintDialog>クラスがインスタンス化され、ユーザーが選択したプリンターが <xref:System.Windows.Forms.DialogResult> プロパティでキャプチャされます。  
  
     2 番目の <xref:System.Drawing.Printing.PrintDocument> コンポーネントの <xref:System.Drawing.Printing.PrintDocument.PrintPage> イベントでは、サンプル ドキュメントが指定されたプリンターに印刷されます。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim PrintDialog1 As New PrintDialog()  
       PrintDialog1.Document = PrintDocument1  
       Dim result As DialogResult = PrintDialog1.ShowDialog()  
  
       If (result = DialogResult.OK) Then  
         PrintDocument1.Print()  
       End If   
  
    End Sub  
  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))          
    End Sub  
  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       PrintDialog printDialog1 = new PrintDialog();  
       printDialog1.Document = printDocument1;  
       DialogResult result = printDialog1.ShowDialog();  
       if (result == DialogResult.OK)  
       {  
          printDocument1.Print();  
       }  
    }  
  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,   
         new Rectangle(500, 500, 500, 500));  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          PrintDialog ^ printDialog1 = gcnew PrintDialog();  
          printDialog1->Document = printDocument1;  
          System::Windows::Forms::DialogResult result =   
             printDialog1->ShowDialog();  
          if (result == DialogResult::OK)  
          {  
             printDocument1->Print();  
          }  
       }  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Red,  
             Rectangle(500, 500, 500, 500));  
       }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] および [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) フォームのコンストラクターに次のコードを追加して、イベント ハンドラーを登録します。  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
  
    ```  
  
    ```cpp  
    this->printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## 参照  
 [Windows フォームにおける印刷のサポート](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)