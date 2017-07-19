---
title: "方法 : Windows フォームの CheckBox コントロールでオプションを設定する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "checked"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "チェック ボックス, 使用 (オプションを設定するために)"
  - "CheckBox コントロール [Windows フォーム], オンの状態"
  - "CheckBox コントロール [Windows フォーム], 使用 (オプションを設定するために)"
ms.assetid: 2ac70498-7e3e-4e07-8901-ccabaeb5fd3e
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : Windows フォームの CheckBox コントロールでオプションを設定する
Windows フォームの <xref:System.Windows.Forms.CheckBox> コントロールは、ユーザーが "True\/False" または "Yes\/No" のオプションを選択できるようにするために使用します。  選択したオプションにはチェック マークが付きます。  
  
### CheckBox コントロールでオプションを設定するには  
  
1.  <xref:System.Windows.Forms.CheckBox.Checked%2A> プロパティの値を確認して状態を判断し、その値を使用してオプションを設定します。  
  
     次のコード例では、<xref:System.Windows.Forms.CheckBox> コントロールの <xref:System.Windows.Forms.CheckBox.CheckedChanged> イベントが発生したときにチェック ボックスがオンであれば、フォームの <xref:System.Windows.Forms.Control.AllowDrop%2A> プロパティが `false` に設定されます。  この機能は、ユーザーの操作を制限する必要がある場合に便利です。  
  
    ```vb  
    Private Sub CheckBox1_CheckedChanged(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles CheckBox1.CheckedChanged  
       ' Determine the CheckState of the check box.  
       If CheckBox1.CheckState = CheckState.Checked Then  
          ' If checked, do not allow items to be dragged onto the form.  
          Me.AllowDrop = False  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    private void checkBox1_CheckedChanged(object sender, System.EventArgs e)  
    {  
       // Determine the CheckState of the check box.  
       if (checkBox1.CheckState == CheckState.Checked)   
       {  
          // If checked, do not allow items to be dragged onto the form.  
          this.AllowDrop = false;  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Determine the CheckState of the check box.  
          if (checkBox1->CheckState == CheckState::Checked)   
          {  
             // If checked, do not allow items to be dragged onto the form.  
             this->AllowDrop = false;  
          }  
       }  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.CheckBox>   
 [CheckBox コントロールの概要](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)   
 [方法 : Windows フォーム CheckBox のクリックに応答する](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)   
 [CheckBox コントロール](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)