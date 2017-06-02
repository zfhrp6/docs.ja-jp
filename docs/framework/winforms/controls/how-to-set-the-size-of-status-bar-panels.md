---
title: "方法 : ステータス バー パネルのサイズを設定する | Microsoft Docs"
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
  - "パネル, 設定 (ステータス バーでのサイズを)"
  - "ステータス バー, 設定 (パネル サイズを)"
  - "StatusBar コントロール [Windows フォーム], パネル サイズ"
ms.assetid: a01bee43-d9eb-4954-84e6-45a93532d08d
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : ステータス バー パネルのサイズを設定する
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStripStatusLabel> コントロールは、<xref:System.Windows.Forms.StatusBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.StatusBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  
  
 [StatusBar コントロール](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) コントロールに含まれる <xref:System.Windows.Forms.StatusBarPanel> クラスの各インスタンスには、実行時に幅およびサイズ変更の動作を決定する動的プロパティが多数用意されています。  
  
### パネルのサイズを設定するには  
  
1.  プロシージャで、ステータス バー パネルの <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>、<xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>、および<xref:System.Windows.Forms.StatusBarPanel.Width%2A> の各プロパティ \(またはその中に含まれるサブセット\) を設定します。これには <xref:System.Windows.Forms.StatusBarPanel> コレクションの <xref:System.Windows.Forms.StatusBar.Panels%2A> プロパティを介して渡されるインデックスを使用します。  
  
    ```vb  
    Public Sub SetStatusBarPanelSize()  
    ' Create panel and set text property.  
       StatusBar1.Panels.Add("One")  
    ' Set properties of panels.  
       StatusBar1.Panels(0).AutoSize = StatusBarPanelAutoSize.Spring  
       StatusBar1.Panels(0).Width = 200  
    ' Enable the StatusBar control to display panels.  
       StatusBar1.ShowPanels = True  
        End Sub  
  
    ```  
  
    ```csharp  
    public void SetStatusBarPanelSize()  
    {  
       // Create panel and set text property.  
       statusBar1.Panels.Add("One");  
       // Set properties of panels.  
       statusBar1.Panels[0].AutoSize = StatusBarPanelAutoSize.Spring;  
       statusBar1.Panels[0].Width = 200;  
       statusBar1.ShowPanels = true;  
    }  
  
    ```  
  
    ```cpp  
    public:  
       void SetStatusBarPanelSize()  
       {  
          // Create panel and set text property.  
          statusBar1->Panels->Add("One");  
          // Set properties of panels.  
          statusBar1->Panels[0]->AutoSize =  
             StatusBarPanelAutoSize::Spring;  
          statusBar1->Panels[0]->Width = 200;  
          statusBar1->ShowPanels = true;  
       }  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.StatusBar>   
 <xref:System.Windows.Forms.ToolStripStatusLabel>   
 [チュートリアル : ステータス バー情報の実行時更新](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)   
 [方法 : Windows フォームの StatusBar コントロールでクリックされたパネルを確認する](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)   
 [StatusBar コントロールの概要](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)