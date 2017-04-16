---
title: "方法 : Windows フォームの Button コントロールをキャンセル ボタンとして指定する | Microsoft Docs"
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
  - "Button コントロール [Windows フォーム], 指定 (キャンセル ボタンとして)"
  - "ボタン, キャンセル ボタン"
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : Windows フォームの Button コントロールをキャンセル ボタンとして指定する
すべての Windows フォーム上で、<xref:System.Windows.Forms.Button> コントロールをキャンセル ボタンとして指定できます。  ユーザーが Esc キーを押すと、フォームの他のコントロールにフォーカスがある場合でも、このキャンセル ボタンがクリックされます。  このようなボタンは、通常、ユーザーがどのアクションにもコミットせずに、すばやく操作を終了できるようにするために設定されます。  
  
### キャンセル ボタンを指定するには  
  
1.  フォームの <xref:System.Windows.Forms.Form.CancelButton%2A> プロパティを適切な <xref:System.Windows.Forms.Button> コントロールに設定します。  
  
    ```vb  
    Private Sub SetCancelButton(ByVal myCancelBtn As Button)  
       Me.CancelButton = myCancelBtn  
    End Sub  
    ```  
  
    ```csharp  
    private void SetCancelButton(Button myCancelBtn)  
    {  
       this.CancelButton = myCancelBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetCancelButton(Button ^ myCancelBtn)  
       {  
          this->CancelButton = myCancelBtn;  
       }  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.Form.CancelButton%2A>   
 [Button コントロールの概要](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)   
 [Windows フォームの Button コントロールを選択する方法](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)   
 [方法 : Windows フォームのボタンのクリックに応答する](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)   
 [方法 : Windows フォームの Button コントロールを承認ボタンとして指定する](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-accept-button.md)   
 [Button コントロール](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)