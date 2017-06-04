---
title: "方法 : Windows フォームの印刷ジョブを完了する | Microsoft Docs"
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
  - "印刷ジョブ, 完了 (Windows フォームで)"
  - "印刷 [Windows フォーム], 印刷ジョブ"
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# 方法 : Windows フォームの印刷ジョブを完了する
印刷ジョブを伴うワード プロセッサやその他のアプリケーションでは、多くの場合、印刷ジョブが完了したというメッセージをユーザーに表示するオプションが用意されています。  <xref:System.Drawing.Printing.PrintDocument> コンポーネントの <xref:System.Drawing.Printing.PrintDocument.EndPrint> イベントを処理することによって、Windows フォームにこの機能を用意できます。  
  
 次の手順では、<xref:System.Drawing.Printing.PrintDocument> コンポーネントのある Windows ベースのアプリケーションを作成している必要があります。これは Windows ベースのアプリケーションからの印刷を有効にする標準的な方法です。  <xref:System.Drawing.Printing.PrintDocument> コンポーネントを使用した Windows フォームからの印刷の詳細については、「[方法 : 標準の Windows フォーム印刷ジョブを作成する](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)」を参照してください。  
  
### 印刷ジョブを完了するには  
  
1.  <xref:System.Drawing.Printing.PrintDocument> コンポーネントの <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> プロパティを設定します。  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2.  <xref:System.Drawing.Printing.PrintDocument.EndPrint> イベントを処理するコードを記述します。  
  
     次のコード例では、ドキュメントの印刷が完了したことを示すメッセージ ボックスが表示されます。  
  
    ```vb  
    Private Sub PrintDocument1_EndPrint(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintEventArgs) Handles PrintDocument1.EndPrint  
       MessageBox.Show(PrintDocument1.DocumentName + " has finished printing.")  
    End Sub  
  
    ```  
  
    ```csharp  
    private void printDocument1_EndPrint(object sender,   
    System.Drawing.Printing.PrintEventArgs e)  
    {  
       MessageBox.Show(printDocument1.DocumentName +   
          " has finished printing.");  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_EndPrint(System::Object ^ sender,  
          System::Drawing::Printing::PrintEventArgs ^ e)  
       {  
          MessageBox::Show(String::Concat(printDocument1->DocumentName,  
             " has finished printing."));  
       }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] および [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) フォームのコンストラクターに次のコードを挿入してイベント ハンドラーを登録します。  
  
    ```csharp  
    this.printDocument1.EndPrint += new  
       System.Drawing.Printing.PrintEventHandler  
       (this.printDocument1_EndPrint);  
  
    ```  
  
    ```cpp  
    this->printDocument1->EndPrint += gcnew  
       System::Drawing::Printing::PrintEventHandler  
       (this, &Form1::printDocument1_EndPrint);  
    ```  
  
## 参照  
 <xref:System.Drawing.Printing.PrintDocument>   
 [Windows フォームにおける印刷のサポート](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)