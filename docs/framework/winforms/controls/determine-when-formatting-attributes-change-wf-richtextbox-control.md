---
title: "方法 : Windows フォームの RichTextBox コントロールにおける書式属性の変更を確認する | Microsoft Docs"
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
  - "例 [Windows フォーム], テキスト ボックス"
  - "RichTextBox コントロール [Windows フォーム], 判断 (フォントの変更を)"
  - "SelBold プロパティ"
  - "SelChange イベント"
  - "テキスト ボックス, 判断 (フォントの変更を)"
ms.assetid: bdfed015-f77a-41e5-b38f-f8629b2fa166
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : Windows フォームの RichTextBox コントロールにおける書式属性の変更を確認する
一般的に、Windows フォームの <xref:System.Windows.Forms.RichTextBox> コントロールは、テキストにフォント オプションや段落スタイルなどの属性を設定するために使用されます。  多くのワード プロセッシング アプリケーションのように、テキストの書式の変更を追跡するために、アプリケーションでツール バーを表示することが必要な場合があります。  
  
### 書式属性の変更に応答するには  
  
1.  <xref:System.Windows.Forms.RichTextBox.SelectionChanged> イベント ハンドラーに、属性の値に応じて適切な処理を実行するコードを記述します。  <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> プロパティの値に応じてツール バーのボタンの外観を変更する例を次に示します。  ツール バーのボタンは、コントロール内でカーソルが移動したときにだけ更新されます。  
  
     次の例では、フォームに <xref:System.Windows.Forms.RichTextBox> コントロールと、1 つのツール バー ボタンを含む <xref:System.Windows.Forms.ToolBar> コントロールがあると仮定しています。  ツール バーおよびツール バー ボタンの詳細については、「[方法 : ツール バー コントロールにボタンを追加する](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)」を参照してください。  
  
    ```vb  
    ' The following code assumes the existence of a toolbar control  
    ' with at least one toolbar button.  
    Private Sub RichTextBox1_SelectionChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles RichTextBox1.SelectionChanged  
       If RichTextBox1.SelectionBullet = True Then  
          ' Bullet button on toolbar should appear pressed  
          ToolBarButton1.Pushed = True  
       Else  
           ' Bullet button on toolbar should appear unpressed  
           ToolBarButton1.Pushed = False  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    // The following code assumes the existence of a toolbar control  
    // with at least one toolbar button.  
    private void richTextBox1_SelectionChanged(object sender,  
    System.EventArgs e)  
    {  
       if (richTextBox1.SelectionBullet == true)   
       {  
          // Bullet button on toolbar should appear pressed  
          toolBarButton1.Pushed = true;  
       }  
       else   
       {  
          // Bullet button on toolbar should appear unpressed  
          toolBarButton1.Pushed = false;  
       }  
    }  
  
    ```  
  
    ```cpp  
    // The following code assumes the existence of a toolbar control  
    // with at least one toolbar button.  
    private:  
       System::Void richTextBox1_SelectionChanged(  
          System::Object ^  sender, System::EventArgs ^  e)  
       {  
          if (richTextBox1->SelectionBullet == true)  
          {  
             // Bullet button on toolbar should appear pressed  
             toolBarButton1->Pushed = true;  
          }  
          else  
          {  
             // Bullet button on toolbar should appear unpressed  
             toolBarButton1->Pushed = false;  
          }  
       }  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.RichTextBox.SelectionChanged>   
 <xref:System.Windows.Forms.RichTextBox>   
 [RichTextBox コントロール](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)   
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)