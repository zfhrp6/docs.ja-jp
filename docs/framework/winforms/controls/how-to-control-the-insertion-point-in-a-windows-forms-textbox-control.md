---
title: '方法 : Windows フォーム TextBox コントロールでのカーソル位置を制御する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], insertion point
- insertion points [Windows Forms], TextBox controls
- text boxes [Windows Forms], controlling insertion point
ms.assetid: 5bee7d34-5121-429e-ab1f-d8ff67bc74c1
ms.openlocfilehash: ced563eb063bbcc429cdf1447a0158459e5d5c97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530739"
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a>方法 : Windows フォーム TextBox コントロールでのカーソル位置を制御する
Windows フォーム<xref:System.Windows.Forms.TextBox>コントロールが最初にフォーカスを受け取る、既存のテキストの左側には、テキスト ボックス内の既定のカーソル。 ユーザーは、キーボードまたはマウスのカーソルを移動できます。 テキスト ボックスを失い、フォーカスを得た場合、挿入ポイントされます任意の場所、ユーザー最後置かれます。  
  
 場合によっては、この動作は、ユーザーに混乱を招くことがあります。 ユーザーのワード プロセッシング アプリケーションで、既存のテキストの後に表示する新しい文字と思ったかもしれません。 データ エントリのアプリケーションでは、ユーザーは、既存のエントリを置き換える新しい文字と思ったかもしれません。 <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A>と<xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>を目的に合わせて動作を変更するプロパティが有効にします。  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a>TextBox コントロールのカーソル位置を制御するには  
  
1.  <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> プロパティに適切な値を設定します。 0 は、最初の文字の左側にすぐにカーソルを配置します。  
  
2.  (省略可能)設定、<xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>プロパティを選択するテキストの長さをします。  
  
     次のコードは、常に 0 に挿入ポイントを返します。 `TextBox1_Enter`イベント ハンドラーが; 詳細については、コントロールにバインドする必要がありますを参照してください[Windows フォームでのイベント ハンドラーの作成](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)です。  
  
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
  
## <a name="making-the-insertion-point-visible-by-default"></a>カーソルを既定で表示します。  
 <xref:System.Windows.Forms.TextBox>挿入ポイントが既定では、新しいフォーム場合にのみに表示される、<xref:System.Windows.Forms.TextBox>コントロールがタブ オーダーの先頭にします。 挿入ポイントが提供する場合にのみを表示するそれ以外の場合、<xref:System.Windows.Forms.TextBox>キーボードまたはマウスでフォーカスがあります。  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a>新しいフォームに既定では、テキスト ボックスの挿入ポイントを表示する  
  
-   設定、<xref:System.Windows.Forms.TextBox>コントロールの<xref:System.Windows.Forms.Control.TabIndex%2A>プロパティを`0`です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.TextBox>  
 [TextBox コントロールの概要](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [方法: Windows フォームの TextBox コントロールを使用してパスワード テキスト ボックスを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [方法: 読み取り専用テキスト ボックスを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [方法: 文字列に引用符を挿入する](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [方法: Windows フォーム TextBox コントロールでテキストを選択する](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [方法: Windows フォーム TextBox コントロールで複数行を表示する](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [TextBox コントロール](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
