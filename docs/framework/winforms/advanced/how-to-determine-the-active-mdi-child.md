---
title: "方法 : アクティブな MDI 子フォームを特定する | Microsoft Docs"
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
  - "子フォーム"
  - "クリップボードのトピック, コピー (データを)"
  - "MDI, アクティブ化 (フォームを)"
  - "MDI, 子ウィンドウ"
  - "MDI, 指定 (フォーカスを)"
ms.assetid: 33880ec3-0207-4c2b-a616-ff140443cc0f
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : アクティブな MDI 子フォームを特定する
現在アクティブな子フォーム上でフォーカスされているコントロールを操作するためのコマンドを必要とする場合が考えられます。  たとえば、子フォームのテキスト ボックスから、選択したテキストをクリップボードにコピーするとします。  この場合、標準の \[編集\] メニューの \[コピー\] の <xref:System.Windows.Forms.Control.Click> イベントを使用して、選択したテキストをクリップボードにコピーするプロシージャを作成します。  
  
 MDI アプリケーションでは、同じ子フォームのインスタンスを多数持つことができるため、プロシージャでは使用するフォームを特定する必要があります。  正しいフォームを特定するには、フォーカスがある子フォーム、または最後にアクティブになった子フォームを返す <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> プロパティを使用します。  
  
 1 つのフォームに複数のコントロールがある場合は、アクティブなコントロールを特定する必要もあります。  <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> プロパティと同様に、<xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> プロパティは、アクティブな子フォーム上でフォーカスされているコントロールを返します。  子フォームのメニュー、MDI フォームのメニュー、またはツール バー ボタンで呼び出すことができるコピー プロシージャを次に示します。  
  
### アクティブな MDI 子フォームを判断してテキストをクリップボードにコピーするには  
  
1.  アクティブな子フォームにあるアクティブなコントロールからテキストをクリップボードにコピーするコードをメソッドに記述します。  
  
    > [!NOTE]
    >  この例では、MDI 親フォーム \(`Form1`\) は <xref:System.Windows.Forms.RichTextBox> コントロールのある MDI 子ウィンドウを少なくとも 1 つ持っていることを前提としています。  詳細については、「[方法 : MDI 親フォームを作成する](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)」を参照してください。  
  
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
  
## 参照  
 [マルチ ドキュメント インターフェイス \(MDI\) アプリケーション](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)   
 [方法 : MDI 親フォームを作成する](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)   
 [方法 : MDI 子フォームを作成する](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)   
 [方法 : アクティブな MDI 子フォームにデータを送信する](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)   
 [方法 : MDI 子フォームを配置する](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)