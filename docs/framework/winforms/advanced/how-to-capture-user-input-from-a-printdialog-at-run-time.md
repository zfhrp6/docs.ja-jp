---
title: "方法 : 実行時に PrintDialog のユーザー入力をキャプチャする | Microsoft Docs"
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
  - "印刷オプション"
  - "印刷オプション, 変更 (実行時に)"
  - "印刷 [Windows フォーム], オプション"
  - "実行時に, 変更 (印刷オプションを)"
ms.assetid: 438501d8-9a70-4fb3-aae6-e46579aba0c6
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 方法 : 実行時に PrintDialog のユーザー入力をキャプチャする
印刷に関連するオプションはデザイン時に設定できますが、多くの場合ユーザーの選択によって、実行時にこれらのオプションの変更が必要となることがあります。  <xref:System.Windows.Forms.PrintDialog> コンポーネントと <xref:System.Drawing.Printing.PrintDocument> コンポーネントを使用して、文書を印刷するユーザー入力をキャプチャできます。  
  
### 印刷オプションをプログラムで変更するには  
  
1.  フォームに <xref:System.Windows.Forms.PrintDialog> コンポーネントと <xref:System.Drawing.Printing.PrintDocument> コンポーネントを追加します。  
  
2.  <xref:System.Windows.Forms.PrintDialog> の <xref:System.Windows.Forms.PrintDialog.Document%2A> プロパティをフォームに追加した <xref:System.Drawing.Printing.PrintDocument> に設定します。  
  
    ```vb  
    PrintDialog1.Document = PrintDocument1  
  
    ```  
  
    ```csharp  
    printDialog1.Document = PrintDocument1;  
  
    ```  
  
    ```cpp  
    printDialog1->Document = PrintDocument1;  
    ```  
  
3.  <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> メソッドを使用して <xref:System.Windows.Forms.PrintDialog> コンポーネントを表示します。  
  
    ```vb  
    PrintDialog1.ShowDialog()  
  
    ```  
  
    ```csharp  
    printDialog1.ShowDialog();  
  
    ```  
  
    ```cpp  
    printDialog1->ShowDialog();  
    ```  
  
4.  ダイアログ ボックスでユーザーが選択した内容は、<xref:System.Drawing.Printing.PrintDocument> コンポーネントの <xref:System.Drawing.Printing.PrinterSettings> プロパティにコピーされます。  
  
## 参照  
 [方法 : Windows フォームで複数ページのテキスト ファイルを印刷する](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)   
 [Windows フォームにおける印刷のサポート](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)