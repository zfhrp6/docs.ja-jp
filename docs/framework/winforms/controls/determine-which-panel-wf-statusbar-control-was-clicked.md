---
title: "方法 : Windows フォームの StatusBar コントロールでクリックされたパネルを確認する | Microsoft Docs"
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
  - "Panel コントロール [Windows フォーム], 判断 (クリックを)"
  - "PanelClick イベント, 判断 (パネルのクリックを)"
  - "パネル, 判断 (クリックされた)"
  - "ステータス バー, 判断 (パネルのクリックを)"
  - "StatusBar コントロール [Windows フォーム], コーディング (パネル クリック イベントを)"
  - "StatusBar コントロール [Windows フォーム], 判断 (パネルのクリックを)"
ms.assetid: d14c6092-04b2-4a07-8ddf-0dd11277ff5f
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : Windows フォームの StatusBar コントロールでクリックされたパネルを確認する
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> コントロールと <xref:System.Windows.Forms.ToolStripStatusLabel> コントロールは、<xref:System.Windows.Forms.StatusBar> コントロールおよび <xref:System.Windows.Forms.StatusBarPanel> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.StatusBar> コントロールおよび <xref:System.Windows.Forms.StatusBarPanel> コントロールは、下位互換性を保つ目的および将来使用する目的で、必要に応じて保持できます。  
  
 ユーザーのクリックに応答するように [StatusBar コントロール](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) コントロールをプログラムするには、<xref:System.Windows.Forms.StatusBar.PanelClick> イベント内で case ステートメントを使用します。  このイベントには、クリックされた <xref:System.Windows.Forms.StatusBarPanel> オブジェクトへの参照を保持する引数 \(パネル引数\) が含まれます。  この参照を使用することにより、クリックされたパネルのインデックスを判別し、それに基づいてプログラミングできます。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.StatusBar> コントロールの <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> プロパティが `true` に設定されていることを確認します。  
  
### クリックされたパネルを判別するには  
  
1.  <xref:System.Windows.Forms.StatusBar.PanelClick> イベント ハンドラーで、`Select Case` ステートメント \([!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] の場合\) または `switch case` \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] または [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)] の場合\) ステートメントを使用し、イベント引数でクリックされたパネルのインデックスを調べて、どのパネルがクリックされたかを確認します。  
  
     次のコード例はフォームに表示を <xref:System.Windows.Forms.StatusBar>コントロールの `StatusBar1`および <xref:System.Windows.Forms.StatusBarPanel> の 2 オブジェクトおよび `StatusBarPanel1``StatusBarPanel2` 必要です。  
  
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
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) フォームのコンストラクターに次のコードを挿入してイベント ハンドラーを登録します。  
  
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
  
## 参照  
 <xref:System.Windows.Forms.StatusBar>   
 <xref:System.Windows.Forms.ToolStripStatusLabel>   
 [方法 : ステータス バー パネルのサイズを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-size-of-status-bar-panels.md)   
 [チュートリアル : ステータス バー情報の実行時更新](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)   
 [StatusBar コントロールの概要](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)