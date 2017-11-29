---
title: "方法 : Windows フォームの印刷ジョブを完了する"
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
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9decba052589bfcc3ecd7b2861dad51e9c51378a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-complete-windows-forms-print-jobs"></a>方法 : Windows フォームの印刷ジョブを完了する
多くの場合、ワード プロセッサや印刷を関連するその他のアプリケーションは、印刷ジョブが完了したユーザーにメッセージを表示するオプションを提供します。 処理することにより、Windows フォーム内でこの機能を提供できる、<xref:System.Drawing.Printing.PrintDocument.EndPrint>のイベント、<xref:System.Drawing.Printing.PrintDocument>コンポーネントです。  
  
 次の手順で Windows ベースのアプリケーションを作成したことが必要です、<xref:System.Drawing.Printing.PrintDocument>コンポーネント、Windows ベースのアプリケーションからの印刷を有効化の標準的な方法は、これをします。 使用して Windows フォームからの印刷の詳細については、<xref:System.Drawing.Printing.PrintDocument>コンポーネントを参照してください[する方法: 標準の Windows フォームの印刷ジョブを作成する](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)です。  
  
### <a name="to-complete-a-print-job"></a>印刷ジョブを完了するには  
  
1.  設定、<xref:System.Drawing.Printing.PrintDocument.DocumentName%2A>のプロパティ、<xref:System.Drawing.Printing.PrintDocument>コンポーネントです。  
  
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
  
     次のコード例では、メッセージ ボックスが表示されます、ドキュメントの印刷が完了したことを示すです。  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] および [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) フォームのコンストラクターに次のコードを追加して、イベント ハンドラーを登録します。  
  
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
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.Printing.PrintDocument>  
 [Windows フォームにおける印刷のサポート](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
