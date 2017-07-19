---
title: "TextBox コントロールの概要 (Windows フォーム) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TextBox"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "テキスト ボックス, 追加"
  - "TextBox コントロール [Windows フォーム], TextBox コントロールの概要"
ms.assetid: d1a9c7f5-fa53-480a-a75c-158f8649ea2f
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# TextBox コントロールの概要 (Windows フォーム)
Windows フォーム テキスト ボックスを使用すると、入力データを取得したりテキストを表示したりできます。  <xref:System.Windows.Forms.TextBox> コントロールは、通常は編集可能なテキストに使用しますが、読み取り専用にすることもできます。  テキスト ボックスでは、複数の行を表示したり、コントロールのサイズに合わせてテキストを折り返したりできます。基本的な書式を追加することもできます。  <xref:System.Windows.Forms.TextBox> コントロールには、表示用のテキストまたはコントロールから入力されたテキストに適用するための、単一の書式スタイルが用意されています。  書式が複数設定されたテキストを表示するには、<xref:System.Windows.Forms.RichTextBox> コントロールを使用します。  詳細については、「[RichTextBox コントロールの概要](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md)」を参照してください。  
  
## TextBox コントロールの操作  
 コントロールによって表示されるテキストは、<xref:System.Windows.Forms.TextBox.Text%2A> プロパティに含まれています。  既定では、最大 2,048 文字をテキスト ボックスに入力できます。  <xref:System.Windows.Forms.TextBox.Multiline%2A> プロパティを `true` に設定した場合は、32 KB までのテキストを入力できます。  <xref:System.Windows.Forms.TextBox.Text%2A> プロパティは、デザイン時に \[プロパティ\] ウィンドウで設定するか、実行時にコードで設定するか、または実行時にユーザー入力によって設定します。  テキスト ボックスの現在の内容は、実行時に <xref:System.Windows.Forms.TextBox.Text%2A> プロパティを読み取ることによって取得できます。  
  
 実行時にテキストをコントロール内に設定するコード例を次に示します。  `InitializeMyControl` の手順では自動的に実装します ; これを呼び出す必要があります。  
  
```vb  
Private Sub InitializeMyControl()  
   ' Put some text into the control first.  
   TextBox1.Text = "This is a TextBox control."  
End Sub  
  
```  
  
```csharp  
private void InitializeMyControl() {  
   // Put some text into the control first.  
   textBox1.Text = "This is a TextBox control.";  
}  
  
```  
  
```cpp  
private:  
   void InitializeMyControl()  
   {  
      // Put some text into the control first.  
      textBox1->Text = "This is a TextBox control.";  
   }  
```  
  
## 参照  
 <xref:System.Windows.Forms.TextBox>   
 [方法 : Windows フォーム TextBox コントロールでのカーソル位置を制御する](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)   
 [方法 : Windows フォームの TextBox コントロールを使用してパスワード テキスト ボックスを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)   
 [方法 : 読み取り専用テキスト ボックスを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)   
 [方法 : 文字列に引用符を挿入する](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)   
 [方法 : Windows フォーム TextBox コントロールでテキストを選択する](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)   
 [方法 : Windows フォーム TextBox コントロールで複数行を表示する](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)   
 [TextBox コントロール](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)