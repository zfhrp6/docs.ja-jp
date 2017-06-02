---
title: "方法 : Windows フォーム TextBox コントロールでテキストを選択する | Microsoft Docs"
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
  - "テキスト ボックス, 選択 (プログラムを使用してテキストを)"
  - "テキスト, 選択 (テキスト ボックスでプログラムを使用して)"
  - "TextBox コントロール [Windows フォーム], 選択 (プログラムを使用してテキストを)"
ms.assetid: 8c591546-6a01-45c7-8e03-f78431f903b1
caps.latest.revision: 24
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# 方法 : Windows フォーム TextBox コントロールでテキストを選択する
Windows フォーム <xref:System.Windows.Forms.TextBox> コントロールを使用すると、プログラムによってテキストを選択できます。  たとえば、テキストの特定の文字列を検索する関数を作成した場合は、テキストを選択し、検索した文字列の位置を視覚的に示すことができます。  
  
### プログラムによってテキストを選択するには  
  
1.  <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> プロパティに、選択するテキストの開始位置を設定します。  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> プロパティは、テキスト文字列内のカーソル位置を示す数値であり、0 は左端の位置を表します。  <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> プロパティにテキスト ボックスの文字数以上の値を設定した場合、カーソル位置は最後の文字の後に配置されます。  
  
2.  <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> プロパティに、選択するテキストの長さを設定します。  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> プロパティは、カーソル位置からの選択範囲の長さを設定する数値です。  <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> に 0 より大きい値を設定すると、現在のカーソル位置を基点とした文字数が選択されます。  
  
3.  \(省略可能\) <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> プロパティを使用して、選択したテキストにアクセスします。  
  
     次のコードを使用すると、コントロールの <xref:System.Windows.Forms.Control.Enter> イベントが発生したときに、テキスト ボックスの内容が選択されます。  この例では、テキスト ボックスの <xref:System.Windows.Forms.TextBox.Text%2A> プロパティの値が `null` または空の文字列でないかどうかを確認しています。  テキスト ボックスにフォーカスが移ると、テキスト ボックスの現在のテキストが選択されます。  `TextBox1_Enter` イベント ハンドラーは、コントロールにバインドする必要があります。詳細については、「[方法 : Windows フォームで実行時にイベント ハンドラーを作成する](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md)」を参照してください。  
  
     この例をテストするには、テキスト ボックスにフォーカスが移るまで Tab キーを押します。  テキスト ボックス内をクリックすると、テキストの選択が解除されます。  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       If (Not String.IsNullOrEmpty(TextBox1.Text)) Then  
          TextBox1.SelectionStart = 0  
          TextBox1.SelectionLength = TextBox1.Text.Length  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    private void textBox1_Enter(object sender, System.EventArgs e){  
       if (!String.IsNullOrEmpty(textBox1.Text))  
       {  
          textBox1.SelectionStart = 0;  
          textBox1.SelectionLength = textBox1.Text.Length;  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^ sender,  
          System::EventArgs ^ e) {  
       if (!System::String::IsNullOrEmpty(textBox1->Text))  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = textBox1->Text->Length;  
       }  
    }  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.TextBox>   
 [TextBox コントロールの概要](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)   
 [方法 : Windows フォーム TextBox コントロールでのカーソル位置を制御する](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)   
 [方法 : Windows フォームの TextBox コントロールを使用してパスワード テキスト ボックスを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)   
 [方法 : 読み取り専用テキスト ボックスを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)   
 [方法 : 文字列に引用符を挿入する](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)   
 [方法 : Windows フォーム TextBox コントロールで複数行を表示する](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)   
 [TextBox コントロール](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)