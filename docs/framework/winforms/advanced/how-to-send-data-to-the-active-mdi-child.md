---
title: "方法 : アクティブな MDI 子フォームにデータを送信する | Microsoft Docs"
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
  - "クリップボードのトピック, 取得 (データを)"
  - "クリップボードのトピック, 貼り付け"
  - "MDI, 送信 (フォームにデータを)"
ms.assetid: 1047d2fe-1235-46db-aad9-563aea1d743b
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : アクティブな MDI 子フォームにデータを送信する
ユーザーがデータをクリップボードから MDI アプリケーションに貼り付ける場合など、[マルチ ドキュメント インターフェイス \(MDI\) アプリケーション](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)のコンテキストの中で、アクティブな子ウィンドウにデータを送信することは少なくありません。  
  
> [!NOTE]
>  フォーカスがある子ウィンドウを調べてその内容をクリップボードに送信する方法については、「[方法 : アクティブな MDI 子フォームを特定する](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)」を参照してください。  
  
### クリップボードからアクティブな MDI 子ウィンドウへデータを送信するには  
  
1.  アクティブな子フォームにあるアクティブなコントロールにクリップボードからテキストをコピーするコードをメソッドに記述します。  
  
    > [!NOTE]
    >  この例では、MDI 親フォーム \(`Form1`\) は <xref:System.Windows.Forms.RichTextBox> コントロールのある MDI 子ウィンドウを少なくとも 1 つ持っていることを前提としています。  詳細については、「[方法 : MDI 親フォームを作成する](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)」を参照してください。  
  
    ```vb  
    Public Sub mniPaste_Click(ByVal sender As Object, _  
       ByVal e As System.EventArgs) Handles mniPaste.Click  
  
       ' Determine the active child form.  
       Dim activeChild As Form = Me.ParentForm.ActiveMDIChild  
  
       ' If there is an active child form, find the active control, which  
       ' in this example should be a RichTextBox.  
       If (Not activeChild Is Nothing) Then  
          Try  
             Dim theBox As RichTextBox = Ctype(activeChild.ActiveControl, RichTextBox)  
             If (Not theBox Is Nothing) Then  
                ' Create a new instance of the DataObject interface.  
                Dim data As IDataObject = Clipboard.GetDataObject()  
                ' If the data is text, then set the text of the   
                ' RichTextBox to the text in the clipboard.  
                If (data.GetDataPresent(DataFormats.Text)) Then  
                   theBox.SelectedText = data.GetData(DataFormats.Text).ToString()  
                End If  
             End If  
          Catch  
             MessageBox.Show("You need to select a RichTextBox.")  
          End Try  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    protected void mniPaste_Click (object sender, System.EventArgs e)  
    {  
      // Determine the active child form.  
       Form activeChild = this.ParentForm.ActiveMdiChild;  
  
       // If there is an active child form, find the active control, which  
       // in this example should be a RichTextBox.  
       if (activeChild != null)  
       {  
          try   
          {  
             RichTextBox theBox = (RichTextBox)activeChild.ActiveControl;  
             if (theBox != null)  
             {  
                // Create a new instance of the DataObject interface.  
                IDataObject data = Clipboard.GetDataObject();  
                // If the data is text, then set the text of the   
                // RichTextBox to the text in the clipboard.  
                if (data.GetDataPresent(DataFormats.Text))  
                {  
                   theBox.SelectedText = data.GetData(DataFormats.Text).ToString();                 
                }  
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
 [方法 : アクティブな MDI 子フォームを特定する](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)   
 [方法 : MDI 子フォームを配置する](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)