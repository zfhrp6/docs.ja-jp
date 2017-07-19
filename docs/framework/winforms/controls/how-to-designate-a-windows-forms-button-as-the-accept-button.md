---
title: "方法 : Windows フォームの Button コントロールを承認ボタンとして指定する | Microsoft Docs"
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
  - "承認ボタン (Windows フォームの)"
  - "Button コントロール [Windows フォーム], 指定 (既定として)"
  - "ボタン, 既定 (Windows フォームでの)"
  - "Windows フォーム コントロール, 既定のボタン (フォームの)"
ms.assetid: 22cc9da6-b913-4e04-9554-dee443ac5c3a
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : Windows フォームの Button コントロールを承認ボタンとして指定する
すべての Windows フォーム上で、<xref:System.Windows.Forms.Button> コントロールを承認ボタン \(既定のボタンとも呼ばれます\) として指定できます。  ユーザーが **Enter** キーを押すと、フォームの他のコントロールにフォーカスがある場合でも、既定のボタンがクリックされます。  
  
> [!NOTE]
>  ただし、複数行テキスト ボックス、または Enter キーをトラップするカスタム コントロールの場合は例外です。また、フォーカスのあるコントロールが承認ボタン以外のボタンである場合は、フォーカスのあるボタンがクリックされます。  
  
### 承認ボタンを指定するには  
  
1.  フォームの <xref:System.Windows.Forms.Form.AcceptButton%2A> プロパティを適切な <xref:System.Windows.Forms.Button> コントロールに設定します。  
  
    ```vb  
    Private Sub SetDefault(ByVal myDefaultBtn As Button)  
      Me.AcceptButton = myDefaultBtn   
    End Sub  
    ```  
  
    ```csharp  
    private void SetDefault(Button myDefaultBtn)  
    {  
       this.AcceptButton = myDefaultBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetDefault(Button ^ myDefaultBtn)  
       {  
          this->AcceptButton = myDefaultBtn;  
       }  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.Form.AcceptButton%2A>   
 [Button コントロールの概要](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)   
 [Windows フォームの Button コントロールを選択する方法](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)   
 [方法 : Windows フォームのボタンのクリックに応答する](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)   
 [方法 : Windows フォームの Button コントロールをキャンセル ボタンとして指定する](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-cancel-button.md)   
 [Button コントロール](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)