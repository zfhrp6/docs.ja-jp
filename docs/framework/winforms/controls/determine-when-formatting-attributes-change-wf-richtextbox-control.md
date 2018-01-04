---
title: "方法 : Windows フォームの RichTextBox コントロールにおける書式属性の変更を確認する"
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
- examples [Windows Forms], text boxes
- RichTextBox control [Windows Forms], determining font changes
- text boxes [Windows Forms], determining font changes
- SelChange event
ms.assetid: bdfed015-f77a-41e5-b38f-f8629b2fa166
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1764b55232d1883516c2cc8684e3ee1b0cb5c05b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a>方法 : Windows フォームの RichTextBox コントロールにおける書式属性の変更を確認する
Windows フォームの一般的な用途<xref:System.Windows.Forms.RichTextBox>コントロールのフォント オプションなどの段落のスタイル属性を含むテキストは、書式設定します。 アプリケーションは、テキストの多くのワード プロセッシング アプリケーションと同様に、ツールバーを表示するために書式設定の変更を追跡する必要があります。  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a>属性の書式設定の変更に応答するには  
  
1.  コードを記述、<xref:System.Windows.Forms.RichTextBox.SelectionChanged>イベント ハンドラー属性の値に応じて適切なアクションを実行します。 次の例の値に応じてツール バー ボタンの外観を変更する、<xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A>プロパティです。 ツール バー ボタンは、コントロール内にカーソルが移動したときにのみ更新されます。  
  
     次の例にフォームを前提としています、<xref:System.Windows.Forms.RichTextBox>コントロールと<xref:System.Windows.Forms.ToolBar>ツール バー ボタンが含まれるコントロール。 ツールバーとツール バー ボタンの詳細については、次を参照してください。[する方法: ツール バー コントロールの追加ボタン](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)です。  
  
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
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.RichTextBox.SelectionChanged>  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox コントロール](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
