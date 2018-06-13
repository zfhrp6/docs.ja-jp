---
title: '方法 : Windows フォームのボタンのクリックに応答する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], responding to Click events
- events [Windows Forms], Click events
- Click event [Windows Forms], Button control
- MouseDown event
- Button control [Windows Forms], click response
- double-clicks
- examples [Windows Forms], controls
- Click event [Windows Forms], responding to
ms.assetid: 7a4951bd-369c-4662-b246-28ad83eda484
ms.openlocfilehash: 14a880c34f163dc6fece44c24d377822a741b0f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534252"
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a>方法 : Windows フォームのボタンのクリックに応答する
Windows フォームの最も基本的な使用<xref:System.Windows.Forms.Button>コントロールは、ボタンがクリックされたときに、いくつかのコードを実行します。  
  
 クリックすると、<xref:System.Windows.Forms.Button>コントロールも生成されます他のイベントの数など、 <xref:System.Windows.Forms.Control.MouseEnter>、 <xref:System.Windows.Forms.Control.MouseDown>、および<xref:System.Windows.Forms.Control.MouseUp>イベント。 これらの関連するイベントのイベント ハンドラーをアタッチする場合は、その操作が競合しないことを確認します。 たとえば場合は、ユーザーがテキスト ボックスに入力した情報をクリア ボタンをクリックすると、ボタンの上にマウス ポインターを置きます必要がありますいないツール ヒントが表示現在存在しない情報を使用します。  
  
 ユーザーをダブルクリックする場合、<xref:System.Windows.Forms.Button>コントロール、1 回のクリックを個別に処理されます。 つまり、コントロールでは、ダブルクリック イベントをサポートしません。  
  
### <a name="to-respond-to-a-button-click"></a>ボタンのクリックに応答するには  
  
-   ボタンの`Click`<xref:System.EventHandler>を実行するコードを記述します。 `Button1_Click` コントロールにバインドする必要があります。 詳細については、次を参照してください。[する方法: Windows フォームの時間の実行時のイベント ハンドラーの作成](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md)です。  
  
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
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          MessageBox::Show("button1 was clicked");  
       }  
    ```  
  
## <a name="see-also"></a>関連項目  
 [Button コントロールの概要](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Windows フォームの Button コントロールを選択する方法](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Button コントロール](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
