---
title: '方法 : Windows フォーム LinkLabel コントロールでオブジェクトまたは Web ページにリンクする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], LinkLabel control
- Windows Forms, linking to objects
- Web page link control
- linking [Windows Forms], to other forms
- Windows Forms, linking to Web pages
- links [Windows Forms], to other forms
- LinkLabel control [Windows Forms], linking to object or Web page
- LinkLabel control [Windows Forms], examples
ms.assetid: 6c91c975-3cb7-4504-82f0-fc6255f8fb85
ms.openlocfilehash: 9957eae7e15c99ec259574b435402420c6bcf5f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539634"
---
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a>方法 : Windows フォーム LinkLabel コントロールでオブジェクトまたは Web ページにリンクする
Windows フォーム<xref:System.Windows.Forms.LinkLabel>コントロールでは、フォーム上で Web スタイルのリンクを作成することができます。 リンクがクリックされたときに、リンクが参照されたを示すためにその色を変更できます。 色の変更の詳細については、次を参照してください。[する方法: Windows フォーム LinkLabel コントロールの外観を変更](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)です。  
  
## <a name="linking-to-another-form"></a>別のフォームへのリンク  
  
#### <a name="to-link-to-another-form-with-a-linklabel-control"></a>LinkLabel コントロールで他のフォームにリンクするには  
  
1.  設定、<xref:System.Windows.Forms.LinkLabel.Text%2A>プロパティに適切なキャプション。  
  
2.  設定、<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>プロパティのキャプションのどの部分がリンクとして示されます。 示されている方法は、リンクのラベルの外観に関連するプロパティによって異なります。 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>によって表される値、 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> 2 つの数値、文字の開始位置と文字数を含むオブジェクト。 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>または次のような方法でコードをプロパティ ウィンドウでプロパティを設定することができます。  
  
    ```vb  
    ' In this code example, the link area has been set to begin  
    ' at the first character and extend for eight characters.  
    ' You may need to modify this based on the text entered in Step 1.  
    LinkLabel1.LinkArea = New LinkArea(0, 8)  
    ```  
  
    ```csharp  
    // In this code example, the link area has been set to begin  
    // at the first character and extend for eight characters.  
    // You may need to modify this based on the text entered in Step 1.  
    linkLabel1.LinkArea = new LinkArea(0,8);  
    ```  
  
    ```cpp  
    // In this code example, the link area has been set to begin  
    // at the first character and extend for eight characters.  
    // You may need to modify this based on the text entered in Step 1.  
    linkLabel1->LinkArea = LinkArea(0,8);  
    ```  
  
3.  <xref:System.Windows.Forms.LinkLabel.LinkClicked> 、イベント ハンドラーを呼び出す、<xref:System.Windows.Forms.Form.Show%2A>プロジェクトで、別のフォームを開き、設定する方法、<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>プロパティを`true`です。  
  
    > [!NOTE]
    >  インスタンス、<xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs>クラスへの参照を実行する、<xref:System.Windows.Forms.LinkLabel>キャストする必要はありません、クリックされたコントロール、`sender`オブジェクト。  
  
    ```vb  
    Protected Sub LinkLabel1_LinkClicked(ByVal Sender As System.Object, _  
       ByVal e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) _  
       Handles LinkLabel1.LinkClicked  
       ' Show another form.  
       Dim f2 As New Form()  
       f2.Show  
       LinkLabel1.LinkVisited = True  
    End Sub  
    ```  
  
    ```csharp  
    protected void linkLabel1_LinkClicked(object sender, System. Windows.Forms.LinkLabelLinkClickedEventArgs e)  
    {  
       // Show another form.  
       Form f2 = new Form();  
       f2.Show();  
       linkLabel1.LinkVisited = true;  
    }  
    ```  
  
    ```cpp  
    private:  
       void linkLabel1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)  
       {  
          // Show another form.  
          Form ^ f2 = new Form();  
          f2->Show();  
          linkLabel1->LinkVisited = true;  
       }  
    ```  
  
## <a name="linking-to-a-web-page"></a>Web ページへのリンク  
 <xref:System.Windows.Forms.LinkLabel>コントロールを使用して、既定のブラウザーで Web ページを表示することもできます。  
  
#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a>LinkLabel コントロールで Internet Explorer と Web ページへのリンクを開始するには  
  
1.  設定、<xref:System.Windows.Forms.LinkLabel.Text%2A>プロパティに適切なキャプション。  
  
2.  設定、<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>プロパティのキャプションのどの部分がリンクとして示されます。  
  
3.  <xref:System.Windows.Forms.LinkLabel.LinkClicked> 、例外処理ブロック中のイベント ハンドラー呼び出しを設定する 2 番目の手順、<xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>プロパティを`true`を使用して、 <xref:System.Diagnostics.Process.Start%2A> URL を使用して、既定のブラウザーを開始するメソッド。 使用する、<xref:System.Diagnostics.Process.Start%2A>メソッドへの参照を追加する必要があります、<xref:System.Diagnostics?displayProperty=nameWithType>名前空間。  
  
    > [!IMPORTANT]
    >  部分的に信頼された環境で次のコードを実行するかどうか (など、共有ドライブ上)、JIT コンパイラが失敗したときに、`VisitLink`メソッドが呼び出されます。 `System.Diagnostics.Process.Start`ステートメントにより、リンク確認要求が失敗します。 例外をキャッチする場合に、`VisitLink`メソッドが呼び出されると、次のコードにより、JIT コンパイラが失敗すると、エラーが処理される適切にします。  
  
    ```vb  
    Private Sub LinkLabel1_LinkClicked(ByVal sender As System.Object, _  
       ByVal e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) _  
       Handles LinkLabel1.LinkClicked  
       Try  
          VisitLink()  
       Catch ex As Exception  
          ' The error message  
          MessageBox.Show("Unable to open link that was clicked.")  
       End Try  
    End Sub  
  
    Sub VisitLink()  
       ' Change the color of the link text by setting LinkVisited   
       ' to True.  
       LinkLabel1.LinkVisited = True  
       ' Call the Process.Start method to open the default browser   
       ' with a URL:  
       System.Diagnostics.Process.Start("http://www.microsoft.com")  
    End Sub  
    ```  
  
    ```csharp  
    private void linkLabel1_LinkClicked(object sender, System.Windows.Forms.LinkLabelLinkClickedEventArgs e)  
    {  
       try  
       {  
          VisitLink();  
       }  
       catch (Exception ex )  
       {  
          MessageBox.Show("Unable to open link that was clicked.");  
       }  
    }  
  
    private void VisitLink()  
    {  
       // Change the color of the link text by setting LinkVisited   
       // to true.  
       linkLabel1.LinkVisited = true;  
       //Call the Process.Start method to open the default browser   
       //with a URL:  
       System.Diagnostics.Process.Start("http://www.microsoft.com");  
    }  
    ```  
  
    ```cpp  
    private:  
       void linkLabel1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)  
       {  
          try  
          {  
             VisitLink();  
          }  
          catch (Exception ^ ex)  
          {  
             MessageBox::Show("Unable to open link that was clicked.");  
          }  
       }  
    private:  
       void VisitLink()  
       {  
          // Change the color of the link text by setting LinkVisited   
          // to true.  
          linkLabel1->LinkVisited = true;  
          // Call the Process.Start method to open the default browser   
          // with a URL:  
          System::Diagnostics::Process::Start("http://www.microsoft.com");  
       }  
    ```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>  
 [LinkLabel コントロールの概要](../../../../docs/framework/winforms/controls/linklabel-control-overview-windows-forms.md)  
 [方法: Windows フォーム LinkLabel コントロールの表示形式を変更する](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)  
 [LinkLabel コントロール](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)
