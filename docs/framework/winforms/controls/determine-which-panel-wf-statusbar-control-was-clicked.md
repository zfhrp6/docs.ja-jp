---
title: '方法 : Windows フォームの StatusBar コントロールでクリックされたパネルを確認する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- status bars [Windows Forms], determining panel clicked
- panels [Windows Forms], determining clicked
- StatusBar control [Windows Forms], coding panel click events
- StatusBar control [Windows Forms], determining panel clicked
- PanelClick event [Windows Forms], determining panel clicked
- Panel control [Windows Forms], determining click
ms.assetid: d14c6092-04b2-4a07-8ddf-0dd11277ff5f
ms.openlocfilehash: b83dc7273c612e914840307bc749abef780284ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527975"
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a>方法 : Windows フォームの StatusBar コントロールでクリックされたパネルを確認する
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip>と<xref:System.Windows.Forms.ToolStripStatusLabel>コントロールの置換し、する機能を追加、<xref:System.Windows.Forms.StatusBar>と<xref:System.Windows.Forms.StatusBarPanel>コントロールですただし、、<xref:System.Windows.Forms.StatusBar>と<xref:System.Windows.Forms.StatusBarPanel>場合、旧バージョンとの互換性と将来の使用の両方のコントロールが保持されますします。選択します。  
  
 プログラムを[StatusBar コントロール](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md)コントロールにユーザーのクリックに応答を内の case ステートメントを使用して、<xref:System.Windows.Forms.StatusBar.PanelClick>イベント。 イベントには、クリックされたへの参照を含む引数 (パネルの引数) が含まれる<xref:System.Windows.Forms.StatusBarPanel>です。 この参照を使用して、クリックされたパネルのインデックスを確認し、それに応じたプログラミングできます。  
  
> [!NOTE]
>  いることを確認、<xref:System.Windows.Forms.StatusBar>コントロールの<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>プロパティに設定されている`true`です。  
  
### <a name="to-determine-which-panel-was-clicked"></a>クリックしてされたパネルを決定するには  
  
1.  <xref:System.Windows.Forms.StatusBar.PanelClick>イベント ハンドラーを使用して、 `Select Case` (Visual Basic で) または`switch case`(Visual c# または[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) イベントの引数でクリックされたパネルのインデックスを確認するにはクリックしてされたパネルを決定するステートメント。  
  
     次のコード例のフォームに存在することが必要です、<xref:System.Windows.Forms.StatusBar>コントロール、 `StatusBar1`、および 2 つ<xref:System.Windows.Forms.StatusBarPanel>オブジェクト、`StatusBarPanel1`と`StatusBarPanel2`です。  
  
    ```vb  
    Private Sub StatusBar1_PanelClick(ByVal sender As System.Object, ByVal e As System.Windows.Forms.StatusBarPanelClickEventArgs) Handles StatusBar1.PanelClick  
       Select Case StatusBar1.Panels.IndexOf(e.StatusBarPanel)  
         Case 0  
           MessageBox.Show("You have clicked Panel One.")  
         Case 1  
           MessageBox.Show("You have clicked Panel Two.")  
       End Select  
    End Sub  
    ```  
  
    ```csharp  
    private void statusBar1_PanelClick(object sender,   
    System.Windows.Forms.StatusBarPanelClickEventArgs e)  
    {  
       switch (statusBar1.Panels.IndexOf(e.StatusBarPanel))  
       {  
          case 0 :  
             MessageBox.Show("You have clicked Panel One.");  
             break;  
          case 1 :  
             MessageBox.Show("You have clicked Panel Two.");  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void statusBar1_PanelClick(System::Object ^  sender,  
          System::Windows::Forms::StatusBarPanelClickEventArgs ^  e)  
       {  
          switch (statusBar1->Panels->IndexOf(e->StatusBarPanel))  
          {  
             case 0 :  
                MessageBox::Show("You have clicked Panel One.");  
                break;  
             case 1 :  
                MessageBox::Show("You have clicked Panel Two.");  
                break;  
          }  
       }  
    ```  
  
     (Visual C# の場合、 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)])、イベント ハンドラーを登録するフォームのコンス トラクターに次のコードを追加します。  
  
    ```csharp  
    this.statusBar1.PanelClick += new   
       System.Windows.Forms.StatusBarPanelClickEventHandler   
       (this.statusBar1_PanelClick);  
    ```  
  
    ```cpp  
    this->statusBar1->PanelClick += gcnew  
       System::Windows::Forms::StatusBarPanelClickEventHandler  
       (this, &Form1::statusBar1_PanelClick);  
    ```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [方法: ステータス バー パネルのサイズを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-size-of-status-bar-panels.md)  
 [チュートリアル: ステータス バー情報の実行時更新](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)  
 [StatusBar コントロールの概要](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)
