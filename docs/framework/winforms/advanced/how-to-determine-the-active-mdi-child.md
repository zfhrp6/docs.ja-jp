---
title: '方法 : アクティブな MDI 子フォームを特定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- MDI [Windows Forms], child windows
- child forms
- MDI [Windows Forms], activating forms
- MDI [Windows Forms], locating focus
ms.assetid: 33880ec3-0207-4c2b-a616-ff140443cc0f
ms.openlocfilehash: 0b084d204361764af1b36b154acfc5b360fc977e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521719"
---
# <a name="how-to-determine-the-active-mdi-child"></a>方法 : アクティブな MDI 子フォームを特定する
場合によっては、現在アクティブな子フォームにフォーカスを持つコントロールが操作するコマンドを提供するされます。 たとえば、子フォームのテキスト ボックスから選択したテキストをクリップボードにコピーするとします。 クリップボードを使用して、選択したテキストをコピーするプロシージャを作成すると、<xref:System.Windows.Forms.Control.Click>コピー メニュー項目の編集 メニューの標準的なイベントです。  
  
 MDI アプリケーションでは、同じ子フォームの多くのインスタンスを持つことができますため、プロシージャを使用するフォームを知っている必要があります。 正しい形式を指定するには、使用、<xref:System.Windows.Forms.Form.ActiveMdiChild%2A>プロパティで、フォーカスを持っているか、最後にアクティブになった子フォームを返します。  
  
 フォーム上のいくつかのコントロールがある場合は、どのコントロールがアクティブなを指定する必要があります。 同様に、 <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> 、プロパティ、<xref:System.Windows.Forms.ContainerControl.ActiveControl%2A>プロパティは、アクティブな子フォームにフォーカスがあるコントロールを返します。 次の手順は、子フォームのメニューを MDI フォームまたはツール バー ボタンのメニューから呼び出すことができるコピー手順を示しています。  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a>アクティブな MDI 子ウィンドウ (テキストをクリップボードにコピーします) を決定するには  
  
1.  メソッド内には、アクティブな子フォームのアクティブ コントロールのテキストをクリップボードにコピーします。  
  
    > [!NOTE]
    >  この例では、MDI 親フォームがある (`Form1`) を含む 1 つまたは複数の MDI 子ウィンドウを持つ、<xref:System.Windows.Forms.RichTextBox>コントロール。 詳細については、次を参照してください。 [MDI 親フォームを作成する](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)です。  
  
    ```vb  
    Public Sub mniCopy_Click(ByVal sender As Object, _  
       ByVal e As System.EventArgs) Handles mniCopy.Click  
  
       ' Determine the active child form.  
       Dim activeChild As Form = Me.ActiveMDIChild  
  
       ' If there is an active child form, find the active control, which  
       ' in this example should be a RichTextBox.  
       If (Not activeChild Is Nothing) Then  
          Dim theBox As RichTextBox = _  
            TryCast(activeChild.ActiveControl, RichTextBox)  
  
          If (Not theBox Is Nothing) Then  
             'Put selected text on Clipboard.  
             Clipboard.SetDataObject(theBox.SelectedText)  
          Else  
             MessageBox.Show("You need to select a RichTextBox.")  
          End If  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void mniCopy_Click (object sender, System.EventArgs e)  
    {  
       // Determine the active child form.  
       Form activeChild = this.ActiveMdiChild;  
  
       // If there is an active child form, find the active control, which  
       // in this example should be a RichTextBox.  
       if (activeChild != null)  
       {    
          try  
          {  
             RichTextBox theBox = (RichTextBox)activeChild.ActiveControl;  
             if (theBox != null)  
             {  
                // Put the selected text on the Clipboard.  
                Clipboard.SetDataObject(theBox.SelectedText);  
  
             }  
          }  
          catch  
          {  
             MessageBox.Show("You need to select a RichTextBox.");  
          }  
       }  
    }  
    ```  
  
## <a name="see-also"></a>関連項目  
 [マルチ ドキュメント インターフェイス (MDI) アプリケーション](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [方法: MDI 親フォームを作成する](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [方法: MDI 子フォームを作成する](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [方法: アクティブな MDI 子フォームにデータを送信する](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [方法: MDI 子フォームを配置する](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
