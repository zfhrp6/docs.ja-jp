---
title: '方法 : 文字列に引用符を挿入する (Windows フォーム)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- quotation marks
- TextBox control [Windows Forms], displaying quotation marks
- quotation marks [Windows Forms], adding to strings in text boxes
ms.assetid: 68bdc3f3-4177-4eab-99cd-cac17a82b515
ms.openlocfilehash: 7fcc2e8692880f1e5c2b8df807cf7943a5575c56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534834"
---
# <a name="how-to-put-quotation-marks-in-a-string-windows-forms"></a>方法 : 文字列に引用符を挿入する (Windows フォーム)
テキストの文字列に引用符 (" ") を挿入することが必要な場合があります。 例えば:  
  
 言いました、「treat、優れた」!  
  
 代わりに、使用することも、<xref:Microsoft.VisualBasic.ControlChars.Quote>フィールドは定数として。  
  
### <a name="to-place-quotation-marks-in-a-string-in-your-code"></a>コードの文字列に引用符を挿入するには  
  
1.  Visual basic では、埋め込みの引用符として行の 2 つの引用符を挿入します。 Visual C# の場合と[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]、エスケープ シーケンスを挿入\\"として埋め込まれた引用符。 たとえば、上記の文字列を作成するには、次のコードを使用します。  
  
    ```vb  
    Private Sub InsertQuote()  
       TextBox1.Text = "She said, ""You deserve a treat!"" "  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertQuote(){  
       textBox1.Text = "She said, \"You deserve a treat!\" ";  
    }  
    ```  
  
    ```cpp  
    private:  
       void InsertQuote()  
       {  
          textBox1->Text = "She said, \"You deserve a treat!\" ";  
       }  
    ```  
  
     - または -  
  
2.  引用符を表す ASCII 文字または Unicode 文字を挿入します。 Visual basic では、ASCII 文字 (34) を使用します。 Visual c# では、Unicode 文字 (\u0022) を使用します。  
  
    ```vb  
    Private Sub InsertAscii()  
       TextBox1.Text = "She said, " & Chr(34) & "You deserve a treat!" & Chr(34)  
    End Sub  
    ```  
  
    ```csharp  
    private void InsertAscii(){  
       textBox1.Text = "She said, " + '\u0022' + "You deserve a treat!" + '\u0022';  
    }  
    ```  
  
    > [!NOTE]
    >  この例では、基本文字セットの文字を指定するユニバーサル文字名を使用できないため、\u0022 を使用することはできません。 使用した場合、C3851 が発生します。 詳細については、「[コンパイラ エラー C3851](/cpp/error-messages/compiler-errors-2/compiler-error-c3851)」を参照してください。  
  
     - または -  
  
3.  文字の定数を定義し、必要に応じてその定数を使用することもできます。  
  
    ```vb  
    Const quote As String = """"  
    TextBox1.Text = "She said, " & quote & "You deserve a treat!" & quote  
    ```  
  
    ```csharp  
    const string quote = "\"";  
    textBox1.Text = "She said, " + quote +  "You deserve a treat!"+ quote ;  
    ```  
  
    ```cpp  
    const String^ quote = "\"";  
    textBox1->Text = String::Concat("She said, ",  
       const_cast<String^>(quote), "You deserve a treat!",  
       const_cast<String^>(quote));  
    ```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.TextBox>  
 <xref:Microsoft.VisualBasic.ControlChars.Quote>  
 [TextBox コントロールの概要](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [方法: Windows フォーム TextBox コントロールでのカーソル位置を制御する](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [方法: Windows フォームの TextBox コントロールを使用してパスワード テキスト ボックスを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [方法: 読み取り専用テキスト ボックスを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [方法: Windows フォーム TextBox コントロールでテキストを選択する](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [方法: Windows フォーム TextBox コントロールで複数行を表示する](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [TextBox コントロール](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
