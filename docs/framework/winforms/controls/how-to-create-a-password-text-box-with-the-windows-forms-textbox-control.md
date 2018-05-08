---
title: '方法 : Windows フォームの TextBox コントロールを使用してパスワード テキスト ボックスを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], entering passwords
- password boxes [Windows Forms], creating
- PasswordChar property in text boxes
- passwords [Windows Forms], input mask
- passwords [Windows Forms], password text box
ms.assetid: d105d6b9-3d50-44cd-80d8-2c0e2f486727
ms.openlocfilehash: 41bfb2bc1a1ead5bb289264c44145b88721efe49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a>方法 : Windows フォームの TextBox コントロールを使用してパスワード テキスト ボックスを作成する
パスワード ボックスは、ユーザーが入力文字列中に、プレース ホルダー文字を表示する Windows フォームのテキスト ボックスです。  
  
### <a name="to-create-a-password-text-box"></a>パスワード テキスト ボックスを作成するには  
  
1.  設定、<xref:System.Windows.Forms.TextBox.PasswordChar%2A>のプロパティ、<xref:System.Windows.Forms.TextBox>特定の文字をコントロールします。  
  
     <xref:System.Windows.Forms.TextBox.PasswordChar%2A>プロパティは、テキスト ボックスに表示される文字を指定します。 たとえば、[パスワード] ボックスに表示されるアスタリスクを実行する場合に、指定 * の<xref:System.Windows.Forms.TextBox.PasswordChar%2A>プロパティ ウィンドウでプロパティです。 次に、どのような文字をテキスト ボックスにユーザーを入力するに関係なく、アスタリスクが表示されます。  
  
2.  (省略可能)設定、<xref:System.Windows.Forms.TextBoxBase.MaxLength%2A>プロパティです。 プロパティは、テキスト ボックスに入力できる文字数を決定します。 最大長を超えた場合、システムのビープ音が鳴るし、テキスト ボックスで、複数の文字は使用できません。 これを行うように使用すると、パスワードを推測しようとしているハッカーのパスワードの最大の長さがありますの希望しない場合がありますに注意してください。  
  
     次のコード例では、14 文字以内の文字列をそのまま使用し、文字列の代わりにアスタリスクが表示するテキスト ボックスを初期化する方法を示します。 `InitializeMyControl`プロシージャが自動的に実行されません。 呼び出す必要があります。  
  
    > [!IMPORTANT]
    >  使用して、<xref:System.Windows.Forms.TextBox.PasswordChar%2A>プロパティ テキスト ボックスに確保できますを他のユーザーはデータを入力するユーザーを確認する場合は、ユーザーのパスワードを確認できません。 このセキュリティ対策には、あらゆる種類の記憶域または、アプリケーション ロジックによって発生するパスワードの送信は説明しません。 任意の方法で入力したテキストは暗号化されないために、他の機密データと同様に扱う必要があります。 このよう表示されない場合でもパスワード中として扱われますプレーン テキスト文字列 (いくつか追加のセキュリティ対策を実装している) 場合。  
  
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
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.TextBox>  
 [TextBox コントロールの概要](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [方法: Windows フォーム TextBox コントロールでのカーソル位置を制御する](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [方法: 読み取り専用テキスト ボックスを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [方法: 文字列に引用符を挿入する](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [方法: Windows フォーム TextBox コントロールでテキストを選択する](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [方法: Windows フォーム TextBox コントロールで複数行を表示する](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [TextBox コントロール](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
