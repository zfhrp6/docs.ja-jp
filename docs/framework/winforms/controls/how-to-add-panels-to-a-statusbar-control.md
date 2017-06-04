---
title: "方法 : StatusBar コントロールにパネルを追加する | Microsoft Docs"
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
  - "パネル, ステータス バー"
  - "ステータス バー, 追加 (パネルを)"
  - "StatusBar コントロール [Windows フォーム], 追加 (パネルを)"
ms.assetid: 835e3902-288c-4c38-9d69-0696d8695009
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : StatusBar コントロールにパネルを追加する
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> コントロールと <xref:System.Windows.Forms.ToolStripStatusLabel> コントロールは、<xref:System.Windows.Forms.StatusBar> コントロールおよび <xref:System.Windows.Forms.StatusBarPanel> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.StatusBar> コントロールおよび <xref:System.Windows.Forms.StatusBarPanel> コントロールは、下位互換性を保つ目的および将来使用する目的で、必要に応じて保持できます。  
  
 [StatusBar コントロール](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) コントロール内のプログラミング可能な領域は、<xref:System.Windows.Forms.StatusBarPanel> クラスのインスタンスで構成されています。  これらのインスタンスの追加は、<xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> クラスへの追加により行われます。  
  
### ステータス バーにパネルを追加するには  
  
1.  プロシージャでは、ステータス バー パネルを <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> に追加することによって作成します。  <xref:System.Windows.Forms.StatusBar.Panels%2A> プロパティから取得したインデックスを使用して、パネルごとにプロパティの設定値を指定します。  
  
     次のコード例では、アイコンの場所に対するパスとして **\[マイ ドキュメント\]** フォルダーが設定されています。  この場所を使用するのは、Windows オペレーティング システムを実行するコンピューターには、通常このディレクトリが存在すると考えられるためです。  また、この場所を選択すると、ユーザーは最小限のシステム アクセス レベルでアプリケーションを安全に実行できます。  次の例では、既に <xref:System.Windows.Forms.StatusBar> コントロールが追加されたフォームを必要とします。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> は、インデックス番号が 0 から始まるコレクションです。コードはそれに合わせて処理する必要があります。  
  
    ```vb  
    Public Sub CreateStatusBarPanels()  
    ' Create panels and set text property.  
       StatusBar1.Panels.Add("One")  
       StatusBar1.Panels.Add("Two")  
       StatusBar1.Panels.Add("Three")  
    ' Set properties of StatusBar panels.  
    ' Set AutoSize property of panels.  
       StatusBar1.Panels(0).AutoSize = StatusBarPanelAutoSize.Spring  
       StatusBar1.Panels(1).AutoSize = StatusBarPanelAutoSize.Contents  
       StatusBar1.Panels(2).AutoSize = StatusBarPanelAutoSize.Contents  
    ' Set BorderStyle property of panels.  
       StatusBar1.Panels(0).BorderStyle = StatusBarPanelBorderStyle.Raised  
       StatusBar1.Panels(1).BorderStyle = StatusBarPanelBorderStyle.Sunken  
       StatusBar1.Panels(2).BorderStyle = StatusBarPanelBorderStyle.Raised  
    ' Set Icon property of third panel. You should replace the bolded  
    ' icon in the sample below with an icon of your own choosing.  
       StatusBar1.Panels(2).Icon = New _   
       System.Drawing.Icon(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Icon.ico")  
       StatusBar1.ShowPanels = True  
    End Sub  
  
    ```  
  
    ```csharp  
    public void CreateStatusBarPanels()  
    {  
       // Create panels and set text property.  
       statusBar1.Panels.Add("One");  
       statusBar1.Panels.Add("Two");  
       statusBar1.Panels.Add("Three");  
       // Set properties of StatusBar panels.  
       // Set AutoSize property of panels.  
       statusBar1.Panels[0].AutoSize = StatusBarPanelAutoSize.Spring;  
       statusBar1.Panels[1].AutoSize = StatusBarPanelAutoSize.Contents;  
       statusBar1.Panels[2].AutoSize = StatusBarPanelAutoSize.Contents;  
       // Set BorderStyle property of panels.  
       statusBar1.Panels[0].BorderStyle =  
          StatusBarPanelBorderStyle.Raised;  
       statusBar1.Panels[1].BorderStyle = StatusBarPanelBorderStyle.Sunken;  
       statusBar1.Panels[2].BorderStyle = StatusBarPanelBorderStyle.Raised;  
       // Set Icon property of third panel. You should replace the bolded  
       // icon in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       statusBar1.Panels[2].Icon =   
          new System.Drawing.Icon (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\Icon.ico");  
       statusBar1.ShowPanels = true;  
    }  
  
    ```  
  
    ```cpp  
    public:  
       void CreateStatusBarPanels()  
       {  
          // Create panels and set text property.  
          statusBar1->Panels->Add("One");  
          statusBar1->Panels->Add("Two");  
          statusBar1->Panels->Add("Three");  
          // Set properties of StatusBar panels.  
          // Set AutoSize property of panels.  
          statusBar1->Panels[0]->AutoSize =  
             StatusBarPanelAutoSize::Spring;  
          statusBar1->Panels[1]->AutoSize =  
             StatusBarPanelAutoSize::Contents;  
          statusBar1->Panels[2]->AutoSize =  
             StatusBarPanelAutoSize::Contents;  
          // Set BorderStyle property of panels.  
          statusBar1->Panels[0]->BorderStyle =  
             StatusBarPanelBorderStyle::Raised;  
          statusBar1->Panels[1]->BorderStyle =  
             StatusBarPanelBorderStyle::Sunken;  
          statusBar1->Panels[2]->BorderStyle =  
             StatusBarPanelBorderStyle::Raised;  
          // Set Icon property of third panel.  
          // You should replace the bolded image   
          // in the sample below with an icon of your own choosing.  
          statusBar1->Panels[2]->Icon =  
             gcnew System::Drawing::Icon(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Icon.ico"));  
          statusBar1->ShowPanels = true;  
       }  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.StatusBar>   
 <xref:System.Windows.Forms.ToolStripStatusLabel>   
 [Collection Editor Dialog Box](http://msdn.microsoft.com/ja-jp/53fb3aad-bffa-4da5-ac89-8438e6fc803c)   
 [方法 : ステータス バー パネルのサイズを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-size-of-status-bar-panels.md)   
 [チュートリアル : ステータス バー情報の実行時更新](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)   
 [方法 : Windows フォームの StatusBar コントロールでクリックされたパネルを確認する](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)   
 [StatusBar コントロールの概要](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)