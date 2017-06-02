---
title: "方法 : Windows フォーム CheckBox のクリックに応答する | Microsoft Docs"
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
  - "チェック ボックス, 応答 (イベントへの)"
  - "CheckBox コントロール [Windows フォーム], Click イベント"
  - "Click イベント, CheckBox コントロール"
  - "ダブルクリック"
  - "イベント [Windows フォーム], Click イベント"
ms.assetid: c39f901e-8899-43b6-aa31-939cbf7089fb
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : Windows フォーム CheckBox のクリックに応答する
ユーザーが Windows フォームの <xref:System.Windows.Forms.CheckBox> コントロールをクリックすると、<xref:System.Windows.Forms.Control.Click> イベントが発生します。  チェック ボックスの状態に応じてアクションを実行するように、アプリケーションをプログラミングできます。  
  
### CheckBox のクリックに応答するには  
  
1.  <xref:System.Windows.Forms.Control.Click> イベント ハンドラー内で <xref:System.Windows.Forms.CheckBox.Checked%2A> プロパティを使用してコントロールの状態を判断し、必要なアクションを実行します。  
  
    ```vb  
    Private Sub CheckBox1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles CheckBox1.Click  
       ' The CheckBox control's Text property is changed each time the   
       ' control is clicked, indicating a checked or unchecked state.  
       If CheckBox1.Checked = True Then  
          CheckBox1.Text = "Checked"  
       Else  
          CheckBox1.Text = "Unchecked"  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    private void checkBox1_Click(object sender, System.EventArgs e)  
    {  
       // The CheckBox control's Text property is changed each time the   
       // control is clicked, indicating a checked or unchecked state.  
       if (checkBox1.Checked)  
       {  
          checkBox1.Text = "Checked";  
       }  
       else  
       {  
          checkBox1.Text = "Unchecked";  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if (checkBox1->Checked)  
          {  
             checkBox1->Text = "Checked";  
          }  
          else  
          {  
             checkBox1->Text = "Unchecked";  
          }  
       }  
    ```  
  
    > [!NOTE]
    >  ユーザーが <xref:System.Windows.Forms.CheckBox> コントロールをダブルクリックした場合、<xref:System.Windows.Forms.CheckBox> コントロールではダブルクリック イベントがサポートされていないため、それぞれのクリックが個別に処理されます。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> プロパティが `true` \(既定\) に設定されている場合、<xref:System.Windows.Forms.CheckBox> をクリックすると、自動的にオンまたはオフになります。  それ以外の場合は、<xref:System.Windows.Forms.Control.Click> イベントの発生時に手動で <xref:System.Windows.Forms.CheckBox.Checked%2A> プロパティを設定する必要があります。  
  
     また、<xref:System.Windows.Forms.CheckBox> コントロールを使用して、アクションの実行方法を決めることもできます。  
  
### チェック ボックスがクリックされた状態に応じて、アクションの実行方法を決定するには  
  
1.  case ステートメントを使用して <xref:System.Windows.Forms.CheckBox.CheckState%2A> プロパティの値を問い合わせ、アクションの実行方法を決定します。  <xref:System.Windows.Forms.CheckBox.ThreeState%2A> プロパティが `true` に設定されている場合、<xref:System.Windows.Forms.CheckBox.CheckState%2A> プロパティは、ボックスがオンの状態、ボックスがオフの状態、および中間状態を表す 3 つの値のいずれかを返します。中間状態では、ボックスが淡色表示されてオプションが無効であることが示されます。  
  
    ```vb  
    Private Sub CheckBox1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles CheckBox1.Click  
       Select Case CheckBox1.CheckState  
          Case CheckState.Checked  
             ' Code for checked state.  
          Case CheckState.Unchecked  
             ' Code for unchecked state.  
          Case CheckState.Indeterminate  
             ' Code for indeterminate state.  
       End Select   
    End Sub  
  
    ```  
  
    ```csharp  
    private void checkBox1_Click(object sender, System.EventArgs e)  
    {  
       switch(checkBox1.CheckState)  
       {  
          case CheckState.Checked:  
             // Code for checked state.  
             break;  
          case CheckState.Unchecked:  
             // Code for unchecked state.  
             break;  
          case CheckState.Indeterminate:  
             // Code for indeterminate state.  
             break;  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          switch(checkBox1->CheckState) {  
             case CheckState::Checked:  
                // Code for checked state.  
                break;  
             case CheckState::Unchecked:  
                // Code for unchecked state.  
                break;  
             case CheckState::Indeterminate:  
                // Code for indeterminate state.  
                break;  
          }  
       }  
    ```  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.CheckBox.ThreeState%2A> プロパティに `true` が設定されている場合、<xref:System.Windows.Forms.CheckBox.Checked%2A> プロパティは <xref:System.Windows.Forms.CheckState> と <xref:System.Windows.Forms.CheckState> の両方に対して `true` を返します。  
  
## 参照  
 <xref:System.Windows.Forms.CheckBox>   
 [CheckBox コントロールの概要](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)   
 [方法 : Windows フォームの CheckBox コントロールでオプションを設定する](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)   
 [CheckBox コントロール](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)