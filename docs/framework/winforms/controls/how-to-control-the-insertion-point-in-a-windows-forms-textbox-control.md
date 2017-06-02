---
title: "方法 : Windows フォーム TextBox コントロールでのカーソル位置を制御する | Microsoft Docs"
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
  - "カーソル位置, TextBox コントロール"
  - "テキスト ボックス, 制御 (挿入ポイントを)"
  - "TextBox コントロール [Windows フォーム], カーソル位置"
ms.assetid: 5bee7d34-5121-429e-ab1f-d8ff67bc74c1
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 方法 : Windows フォーム TextBox コントロールでのカーソル位置を制御する
Windows フォーム <xref:System.Windows.Forms.TextBox> コントロールに最初にフォーカスが設定されたとき、テキスト ボックスの既定のカーソル位置は、既存テキストの左端になります。  キーボードまたはマウスを使用して、カーソル位置を移動できます。  テキスト ボックスからフォーカスが他に移され、再びフォーカスを受け取った場合は、最後にカーソルが置かれていた場所がカーソル位置となります。  
  
 場合によっては、この動作により混乱することがあります。  ワード プロセッシング アプリケーションでは、新しい文字が既存テキストの後に表示されるという前提で作業します。  データ入力アプリケーションでは、新しい文字を入力すると既存の入力が置き換えられるという前提で作業します。  <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> プロパティおよび <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> プロパティを使用すると、用途に合わせて動作を変更できます。  
  
### TextBox コントロールのカーソル位置を制御するには  
  
1.  <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> プロパティに適切な値を設定します。  0 に設定すると、最初の文字のすぐ左側がカーソル位置となります。  
  
2.  \(省略可能\) <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> プロパティに、選択するテキストの長さを設定します。  
  
     次のコードでは、常にカーソル位置が 0 に戻されます。  `TextBox1_Enter` イベント ハンドラーは、コントロールにバインドする必要があります。詳細については、「[Windows フォーム内でのイベント ハンドラーの作成](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)」を参照してください。  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       TextBox1.SelectionStart = 0  
       TextBox1.SelectionLength = 0  
    End Sub  
  
    ```  
  
    ```csharp  
    private void textBox1_Enter(Object sender, System.EventArgs e) {  
       textBox1.SelectionStart = 0;  
       textBox1.SelectionLength = 0;  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = 0;  
       }  
    ```  
  
## 既定でのカーソル位置の表示  
 <xref:System.Windows.Forms.TextBox> のカーソル位置は、<xref:System.Windows.Forms.TextBox> コントロールがタブ オーダーの最初にある場合にだけ、新しいフォーム上に既定で表示されます。  それ以外の場合、カーソル位置は、キーボードまたはマウスを使って <xref:System.Windows.Forms.TextBox> にフォーカスを移動した場合にだけ表示されます。  
  
#### 新しいフォーム上でテキスト ボックスのカーソル位置を既定で表示するには  
  
-   <xref:System.Windows.Forms.TextBox> コントロールの <xref:System.Windows.Forms.Control.TabIndex%2A> プロパティを `0` に設定します。  
  
## 参照  
 <xref:System.Windows.Forms.TextBox>   
 [TextBox コントロールの概要](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)   
 [方法 : Windows フォームの TextBox コントロールを使用してパスワード テキスト ボックスを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)   
 [方法 : 読み取り専用テキスト ボックスを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)   
 [方法 : 文字列に引用符を挿入する](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)   
 [方法 : Windows フォーム TextBox コントロールでテキストを選択する](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)   
 [方法 : Windows フォーム TextBox コントロールで複数行を表示する](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)   
 [TextBox コントロール](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)