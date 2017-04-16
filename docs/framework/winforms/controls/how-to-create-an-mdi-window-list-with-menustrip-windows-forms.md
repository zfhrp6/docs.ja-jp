---
title: "方法 : MenuStrip を使用して MDI ウィンドウの一覧を作成する (Windows フォーム) | Microsoft Docs"
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
  - "MDI, 作成 (ウィンドウの一覧を)"
  - "MenuStrip コントロール [Windows フォーム], 作成 (ウィンドウの一覧を)"
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : MenuStrip を使用して MDI ウィンドウの一覧を作成する (Windows フォーム)
マルチ ドキュメント インターフェイス \(MDI: Multiple Document Interface\) を使用してアプリケーションを作成すると、複数のドキュメントを同時に開いて、ドキュメント間で内容のコピーおよび貼り付けを行うことができます。  
  
 ここでは、親フォームの \[ウィンドウ\] メニューに、すべてのアクティブな子フォームの一覧を作成する方法について説明します。  
  
### MDI ウィンドウの一覧を MenuStrip 上に作成するには  
  
1.  フォームを作成し、その <xref:System.Windows.Forms.Form.IsMdiContainer%2A> プロパティを `true` に設定します。  
  
2.  フォームに <xref:System.Windows.Forms.MenuStrip> を追加します。  
  
3.  2 つのトップレベル メニュー項目を <xref:System.Windows.Forms.MenuStrip> に追加し、その <xref:System.Windows.Forms.Control.Text%2A> プロパティをそれぞれ `&File` と `&Window` に設定します。  
  
4.  サブメニュー項目を `&File` メニュー項目に追加し、その <xref:System.Windows.Forms.ToolStripItem.Text%2A> プロパティを `&Open` に設定します。  
  
5.  `&Window` <xref:System.Windows.Forms.ToolStripMenuItem> に <xref:System.Windows.Forms.MenuStrip> の <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> のプロパティを設定します。  
  
6.  プロジェクトにフォームを追加し、このフォームに必用なコントロール \(別の <xref:System.Windows.Forms.MenuStrip> など\) を追加します。  
  
7.  `&New` <xref:System.Windows.Forms.ToolStripMenuItem> の <xref:System.Windows.Forms.Control.Click> のイベントのイベント ハンドラーを作成します。  
  
8.  このイベント ハンドラー内に次のようなコードを挿入し、`Form1` の MDI 子フォームとして `Form2` の新しいインスタンスを作成および表示します。  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As _  
    System.Object, ByVal e As System.EventArgs) Handles _  
    openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
  
    ```  
  
     \[C\#\]  
  
    ```  
    private void newToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
  
    ```  
  
9. イベント ハンドラーを登録するに `&New`<xref:System.Windows.Forms.ToolStripMenuItem> に次のようなコードを配置します。  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
  
    ```  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   `Form1` と `Form2` という名前の 2 つの <xref:System.Windows.Forms.Form> コントロール。  
  
-   `menuStrip1` という名前の `Form1` の <xref:System.Windows.Forms.MenuStrip> コントロール、および `menuStrip2` という名前の `Form2` の <xref:System.Windows.Forms.MenuStrip> コントロール。  
  
-   <xref:System?displayProperty=fullName> アセンブリおよび <xref:System.Windows.Forms?displayProperty=fullName> アセンブリへの参照。  
  
## 参照  
 [方法 : MDI 親フォームを作成する](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)   
 [方法 : MDI 子フォームを作成する](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)   
 [MenuStrip コントロール](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)