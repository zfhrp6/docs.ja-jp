---
title: "方法 : Windows フォームの TextBox コントロールを使用してパスワード テキスト ボックスを作成する | Microsoft Docs"
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
  - "パスワード ボックス, 作成"
  - "PasswordChar プロパティ (テキスト ボックスの)"
  - "パスワード, 入力マスク"
  - "パスワード, パスワード テキスト ボックス"
  - "TextBox コントロール [Windows フォーム], 入力 (パスワードを)"
ms.assetid: d105d6b9-3d50-44cd-80d8-2c0e2f486727
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : Windows フォームの TextBox コントロールを使用してパスワード テキスト ボックスを作成する
Windows フォーム テキスト ボックスの 1 つであるパスワード ボックスには、文字列を入力したときにプレースホルダー文字が表示されます。  
  
### パスワード テキスト ボックスを作成するには  
  
1.  <xref:System.Windows.Forms.TextBox> コントロールの <xref:System.Windows.Forms.TextBox.PasswordChar%2A> プロパティに特定の文字を設定します。  
  
     <xref:System.Windows.Forms.TextBox.PasswordChar%2A> プロパティでは、テキスト ボックスに表示する文字を指定します。  たとえば、パスワード ボックスにアスタリスク \(\*\) を表示する場合は、\[プロパティ\] ウィンドウで、<xref:System.Windows.Forms.TextBox.PasswordChar%2A> プロパティに \* を指定します。  テキスト ボックスに入力した文字に関係なく、アスタリスクが表示されます。  
  
2.  \(省略可能\) <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> プロパティを設定します。  このプロパティでは、テキスト ボックスに入力できる文字数を指定します。  最大長を超えるとビープ音がなり、テキスト ボックスにそれ以上文字を入力できなくなります。  パスワードに最大長を設定するとハッカーがパスワードを推測しやすくなるため、このプロパティは必ずしも設定する必要はありません。  
  
     次のコード例では、14 文字までの文字列を入力でき、文字列の代わりにアスタリスクが表示されるテキスト ボックスを初期化します。  `InitializeMyControl` の手順では自動的に実装します ; これを呼び出す必要があります。  
  
    > [!IMPORTANT]
    >  テキスト ボックスで <xref:System.Windows.Forms.TextBox.PasswordChar%2A> プロパティを使用すると、ユーザーがパスワードを入力するときに他の人に見られないようにできます。  このセキュリティ対策では、アプリケーションのロジックによって許可される可能性があるパスワードの保存や伝送を防止することはできません。  入力されたテキストはどのような方法でも暗号化されていないため、他の機密データと同様に扱う必要があります。  パスワードは、表示はされませんが、書式なしテキストの文字列として扱われています。ただし、他に追加のセキュリティ対策を講じている場合は除きます。  
  
    ```vb  
    Private Sub InitializeMyControl()  
       ' Set to no text.  
       TextBox1.Text = ""  
       ' The password character is an asterisk.  
       TextBox1.PasswordChar = "*"  
       ' The control will allow no more than 14 characters.  
       TextBox1.MaxLength = 14  
    End Sub  
  
    ```  
  
    ```csharp  
    private void InitializeMyControl()  
    {  
       // Set to no text.  
       textBox1.Text = "";  
       // The password character is an asterisk.  
       textBox1.PasswordChar = '*';  
       // The control will allow no more than 14 characters.  
       textBox1.MaxLength = 14;  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void InitializeMyControl()  
       {  
          // Set to no text.  
          textBox1->Text = "";  
          // The password character is an asterisk.  
          textBox1->PasswordChar = '*';  
          // The control will allow no more than 14 characters.  
          textBox1->MaxLength = 14;  
       }  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.TextBox>   
 [TextBox コントロールの概要](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)   
 [方法 : Windows フォーム TextBox コントロールでのカーソル位置を制御する](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)   
 [方法 : 読み取り専用テキスト ボックスを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)   
 [方法 : 文字列に引用符を挿入する](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)   
 [方法 : Windows フォーム TextBox コントロールでテキストを選択する](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)   
 [方法 : Windows フォーム TextBox コントロールで複数行を表示する](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)   
 [TextBox コントロール](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)