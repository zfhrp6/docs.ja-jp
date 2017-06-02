---
title: "方法 : Windows フォームのボタンのクリックに応答する | Microsoft Docs"
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
  - "Button コントロール [Windows フォーム], クリックに対する応答"
  - "ボタン, 応答 (Click イベントに)"
  - "Click イベント, Button コントロール"
  - "Click イベント, 応答"
  - "ダブルクリック"
  - "イベント [Windows フォーム], Click イベント"
  - "例 [Windows フォーム], コントロール"
  - "MouseDown イベント"
ms.assetid: 7a4951bd-369c-4662-b246-28ad83eda484
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : Windows フォームのボタンのクリックに応答する
Windows フォームの <xref:System.Windows.Forms.Button> コントロールの最も基本的な使用法は、ボタンがクリックされたときにコードを実行することです。  
  
 <xref:System.Windows.Forms.Button> コントロールをクリックすると、<xref:System.Windows.Forms.Control.MouseEnter>、<xref:System.Windows.Forms.Control.MouseDown>、<xref:System.Windows.Forms.Control.MouseUp> などのさまざまなイベントも生成されます。  これらの関連するイベントにイベント ハンドラーを割り当てる場合は、イベント ハンドラー間で処理内容が矛盾しないように注意してください。  たとえば、ボタンをクリックするとユーザーがテキスト ボックスに入力した情報がクリアされる場合は、ボタン上にマウス ポインターを重ねたときに、削除された情報のツール ヒントが表示されないようにします。  
  
 ユーザーが <xref:System.Windows.Forms.Button> コントロールをダブルクリックした場合、このコントロールではダブルクリック イベントがサポートされていないため、それぞれのクリックが個別に処理されます。  
  
### ボタン クリックに応答するには  
  
-   ボタンの `Click` <xref:System.EventHandler> に、実行するコードを記述します。  `Button1_Click` はコントロールにバインドする必要があります。  詳細については、「[方法 : Windows フォームで実行時にイベント ハンドラーを作成する](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md)」を参照してください。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       MessageBox.Show("Button1 was clicked")  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       MessageBox.Show("button1 was clicked");  
    }  
    ```  
  
    ```cpp#  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          MessageBox::Show("button1 was clicked");  
       }  
    ```  
  
## 参照  
 [Button コントロールの概要](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)   
 [Windows フォームの Button コントロールを選択する方法](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)   
 [Button コントロール](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)