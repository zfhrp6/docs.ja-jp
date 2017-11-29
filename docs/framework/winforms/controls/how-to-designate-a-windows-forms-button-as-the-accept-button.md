---
title: "方法 : Windows フォームの Button コントロールを承認ボタンとして指定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: 22cc9da6-b913-4e04-9554-dee443ac5c3a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0bf5f8dbf8718cb6a30883395d54c5cbc6bafaff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a>方法 : Windows フォームの Button コントロールを承認ボタンとして指定する
すべての Windows フォームで指定することができます、<xref:System.Windows.Forms.Button>コントロールを承認ボタン、既定のボタンとも呼ばれます。 ユーザーが ENTER キーを押したときに既定のボタンがクリックされたフォーム上の他のコントロールにフォーカスがあります。  
  
> [!NOTE]
>  このコントロールにフォーカスが別のボタン機能には、例外:、フォーカスのあるボタンをクリックする場合は、— 複数行テキスト ボックス、または ENTER キーをトラップするカスタム コントロールです。  
  
### <a name="to-designate-the-accept-button"></a>承認ボタンを指定するには  
  
1.  フォームの設定<xref:System.Windows.Forms.Form.AcceptButton%2A>プロパティを適切な<xref:System.Windows.Forms.Button>コントロール。  
  
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
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Form.AcceptButton%2A>  
 [Button コントロールの概要](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Windows フォームの Button コントロールを選択する方法](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [方法: Windows フォームのボタンのクリックに応答する](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [方法: Windows フォームの Button コントロールをキャンセル ボタンとして指定する](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-cancel-button.md)  
 [Button コントロール](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
