---
title: "方法 : ツール バー ボタンのメニュー イベントをトリガーする | Microsoft Docs"
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
  - "例 [Windows フォーム], ツール バー"
  - "ToolBar コントロール [Windows フォーム], クリック イベント ハンドラー"
  - "ToolBar コントロール [Windows フォーム], コーディング (ボタン クリック イベントを)"
  - "ツール バー [Windows フォーム], クリック イベント ハンドラー"
ms.assetid: 98374f70-993d-4ca4-89fb-48fea6ce5b45
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : ツール バー ボタンのメニュー イベントをトリガーする
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> コントロールは、<xref:System.Windows.Forms.ToolBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.ToolBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  
  
 Windows フォームにツール バー ボタン付きの <xref:System.Windows.Forms.ToolBar> コントロールを実装する場合は、ユーザーによってクリックされたボタンを判別することが必要な場合があります。  
  
 <xref:System.Windows.Forms.ToolBar> コントロールの <xref:System.Windows.Forms.ToolBar.ButtonClick> イベントが発生した時点で、<xref:System.Windows.Forms.ToolBarButtonClickEventArgs> クラスの <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> プロパティを評価できます。  次の例では、クリックされたボタンを示すメッセージ ボックスが表示されます。  詳細については、「[MessageBox クラス](frlrfSystemWindowsFormsMessageBoxClassTopic)」を参照してください。  
  
 次の例では、Windows フォームに <xref:System.Windows.Forms.ToolBar> コントロールが追加されていると仮定しています。  
  
### ツール バーの Click イベントを処理するには  
  
1.  プロシージャで、<xref:System.Windows.Forms.ToolBar> コントロールにツール バー ボタンを追加します。  
  
    ```vb  
    Public Sub ToolBarConfig()  
    ' Instantiate the toolbar buttons, set their Text properties  
    ' and add them to the ToolBar control.  
       ToolBar1.Buttons.Add(New ToolBarButton("One"))  
       ToolBar1.Buttons.Add(New ToolBarButton("Two"))  
       ToolBar1.Buttons.Add(New ToolBarButton("Three"))  
    ' Add the event handler delegate.  
       AddHandler ToolBar1.ButtonClick, AddressOf Me.ToolBar1_ButtonClick  
    End Sub  
  
    ```  
  
    ```csharp  
    public void ToolBarConfig()   
    {  
       toolBar1.Buttons.Add(new ToolBarButton("One"));  
       toolBar1.Buttons.Add(new ToolBarButton("Two"));  
       toolBar1.Buttons.Add(new ToolBarButton("Three"));  
  
       toolBar1.ButtonClick +=   
          new ToolBarButtonClickEventHandler(this.toolBar1_ButtonClick);  
    }  
  
    ```  
  
    ```cpp  
    public:  
       void ToolBarConfig()  
       {  
          toolBar1->Buttons->Add(gcnew ToolBarButton("One"));  
          toolBar1->Buttons->Add(gcnew ToolBarButton("Two"));  
          toolBar1->Buttons->Add(gcnew ToolBarButton("Three"));  
  
          toolBar1->ButtonClick +=   
             gcnew ToolBarButtonClickEventHandler(this,  
             &Form1::toolBar1_ButtonClick);  
       }  
    ```  
  
2.  <xref:System.Windows.Forms.ToolBar> コントロールの <xref:System.Windows.Forms.ToolBar.ButtonClick> イベントにイベント ハンドラーを追加します。  ケース切り替えステートメントと <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> クラスを使用して、クリックされたツール バー ボタンを判別します。  判別された結果に基づいて、適切なメッセージ ボックスが表示されます。  
  
    > [!NOTE]
    >  この例では、プレースホルダーとしてメッセージ ボックスを使用しています。  ツール バー ボタンがクリックされたときに実行するコードは、適宜追加できます。  
  
    ```vb  
    Protected Sub ToolBar1_ButtonClick(ByVal sender As Object, _  
    ByVal e As ToolBarButtonClickEventArgs)  
    ' Evaluate the Button property of the ToolBarButtonClickEventArgs  
    ' to determine which button was clicked.  
       Select Case ToolBar1.Buttons.IndexOf(e.Button)  
         Case 0  
           MessageBox.Show("First toolbar button clicked")  
         Case 1  
           MessageBox.Show("Second toolbar button clicked")  
         Case 2  
           MessageBox.Show("Third toolbar button clicked")  
       End Select  
    End Sub  
  
    ```  
  
    ```csharp  
    protected void toolBar1_ButtonClick(object sender,  
    ToolBarButtonClickEventArgs e)  
    {  
       // Evaluate the Button property of the ToolBarButtonClickEventArgs  
       // to determine which button was clicked.  
       switch (toolBar1.Buttons.IndexOf(e.Button))  
       {  
          case 0 :  
             MessageBox.Show("First toolbar button clicked");  
             break;  
          case 1 :  
             MessageBox.Show("Second toolbar button clicked");  
             break;  
          case 2 :  
             MessageBox.Show("Third toolbar button clicked");  
             break;  
       }  
    }  
  
    ```  
  
    ```cpp  
    protected:  
       void toolBar1_ButtonClick(System::Object ^ sender,  
          ToolBarButtonClickEventArgs ^ e)  
       {  
         // Evaluate the Button property of the ToolBarButtonClickEventArgs  
         // to determine which button was clicked.  
          switch (toolBar1->Buttons->IndexOf(e->Button))  
          {  
             case 0 :  
                MessageBox::Show("First toolbar button clicked");  
                break;  
             case 1 :  
                MessageBox::Show("Second toolbar button clicked");  
                break;  
             case 2 :  
                MessageBox::Show("Third toolbar button clicked");  
                break;  
          }  
       }  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.ToolBar>   
 [方法 : ツール バー コントロールにボタンを追加する](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)   
 [方法 : ツール バー ボタンのアイコンを定義する](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)   
 [ToolBar コントロール](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)