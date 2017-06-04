---
title: "方法 : 標準の Windows フォーム印刷ジョブを作成する | Microsoft Docs"
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
  - "出力 [Visual Basic], Windows アプリケーションで"
  - "印刷 [Windows フォーム]"
  - "印刷 [Windows フォーム], 作成 (印刷ジョブを)"
ms.assetid: 03342b90-9cfe-40b2-838b-b479a13c5dea
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 方法 : 標準の Windows フォーム印刷ジョブを作成する
Windows フォームでの印刷の基盤となるのは、<xref:System.Drawing.Printing.PrintDocument> コンポーネントです。より具体的に言えば、<xref:System.Drawing.Printing.PrintDocument.PrintPage> イベントです。  <xref:System.Drawing.Printing.PrintDocument.PrintPage> イベントを処理するコードを記述することにより、印刷対象と印刷方法を指定できます。  
  
### 印刷ジョブを作成するには  
  
1.  フォームに <xref:System.Drawing.Printing.PrintDocument> コンポーネントを追加します。  
  
2.  <xref:System.Drawing.Printing.PrintDocument.PrintPage> イベントを処理するコードを記述します。  
  
     独自の印刷ロジックをコーディングする必要があります。  また、印刷する対象も指定する必要があります。  
  
     次のコード例では、印刷対象として <xref:System.Drawing.Printing.PrintDocument.PrintPage> イベント ハンドラー内で赤い四角形のサンプル グラフィックを作成しています。  
  
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
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] および [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) フォームのコンストラクターに次のコードを挿入してイベント ハンドラーを登録します。  
  
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
  
     また、<xref:System.Drawing.Printing.PrintDocument.BeginPrint> イベントおよび <xref:System.Drawing.Printing.PrintDocument.EndPrint> イベントに対するコードを記述することが必要な場合もあります。その場合、各ページが印刷されるたびに、印刷する合計ページ数を表す整数がデクリメントされるようにもできます。  
  
    > [!NOTE]
    >  フォームに <xref:System.Windows.Forms.PrintDialog> コンポーネントを追加すると、明快で効率的なユーザー インターフェイス \(UI\) をユーザーに提供できます。  <xref:System.Windows.Forms.PrintDialog> コンポーネントの <xref:System.Windows.Forms.PrintDialog.Document%2A> プロパティを設定することにより、フォーム上で作業中の印刷ドキュメントに関連するプロパティを設定できます。  <xref:System.Windows.Forms.PrintDialog> コンポーネントの詳細については、「[PrintDialog コンポーネント](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)」を参照してください。  
  
     印刷ジョブをプログラムで作成する方法など、Windows フォームの印刷ジョブの詳細については、「<xref:System.Drawing.Printing.PrintPageEventArgs>」のトピックを参照してください。  
  
## 参照  
 <xref:System.Drawing.Printing.PrintDocument>   
 [Windows フォームにおける印刷のサポート](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)