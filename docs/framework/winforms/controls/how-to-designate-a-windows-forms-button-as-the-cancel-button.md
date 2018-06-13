---
title: '方法 : Windows フォームの Button コントロールをキャンセル ボタンとして指定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
ms.openlocfilehash: efe68ec8e5c34607bb8f865b5d0c7919a0377ab8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530872"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a>方法 : Windows フォームの Button コントロールをキャンセル ボタンとして指定する
すべての Windows フォームで指定することができます、<xref:System.Windows.Forms.Button>コントロールを [キャンセル] ボタンを配置します。 ユーザーがフォーム上の他のコントロールにフォーカスがあるか、ESC キーを押すたびに [キャンセル] ボタンをクリックします。 このようなボタンは通常、ユーザー操作をコミットすることがなくすばやく操作を終了するために設定します。  
  
### <a name="to-designate-the-cancel-button"></a>[キャンセル] ボタンを指定するには  
  
1.  フォームの設定<xref:System.Windows.Forms.Form.CancelButton%2A>プロパティを適切な<xref:System.Windows.Forms.Button>コントロール。  
  
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
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Form.CancelButton%2A>  
 [Button コントロールの概要](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Windows フォームの Button コントロールを選択する方法](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [方法: Windows フォームのボタンのクリックに応答する](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [方法: Windows フォームの Button コントロールを承認ボタンとして指定する](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-accept-button.md)  
 [Button コントロール](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
