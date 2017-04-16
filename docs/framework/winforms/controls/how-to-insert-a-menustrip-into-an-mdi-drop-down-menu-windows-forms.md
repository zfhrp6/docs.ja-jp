---
title: "方法 : MDI ドロップダウン メニューに MenuStrip を挿入する (Windows フォーム) | Microsoft Docs"
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
  - "MDI, マージ (メニュー項目を)"
  - "MenuStrip コントロール [Windows フォーム], 挿入"
  - "MenuStrip コントロール [Windows フォーム], マージ"
ms.assetid: 0fad444e-26d9-49af-8860-044d9c10d608
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : MDI ドロップダウン メニューに MenuStrip を挿入する (Windows フォーム)
アプリケーションの中には、マルチ ドキュメント インターフェイス \(MDI\) 子ウィンドウの種類が MDI 親ウィンドウと異なるものもあります。  たとえば、MDI 親がスプレッドシートで、MDI 子がグラフの場合があります。  そのような場合は、異なる種類の MDI 子ウィンドウがアクティブになったときに、MDI 子メニューの内容で MDI 親メニューの内容を更新する必要があります。  
  
 次のプロシージャでは、<xref:System.Windows.Forms.Form.IsMdiContainer%2A>、<xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>、<xref:System.Windows.Forms.MergeAction>、および <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> の各プロパティを使用して、MDI 子メニューのメニュー項目のグループを MDI 親メニューのドロップダウン部分に挿入します。  MDI 子ウィンドウを閉じると、挿入したメニュー項目が MDI 親ウィンドウから削除されます。  
  
### MenuStrip を MDI ドロップダウン メニューに挿入するには  
  
1.  フォームを作成し、その <xref:System.Windows.Forms.Form.IsMdiContainer%2A> プロパティを `true` に設定します。  
  
2.  <xref:System.Windows.Forms.MenuStrip> を `Form1` に追加し、<xref:System.Windows.Forms.MenuStrip> の <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> プロパティを `true` に設定します。  
  
3.  トップレベル メニュー項目を `Form1` <xref:System.Windows.Forms.MenuStrip> に追加し、その <xref:System.Windows.Forms.Control.Text%2A> プロパティを `&File` に設定します。  
  
4.  3 つのサブメニュー項目を `&File` メニュー項目に追加し、それらの <xref:System.Windows.Forms.ToolStripItem.Text%2A> プロパティをそれぞれ `&Open`、`&Import from`、および `E&xit` に設定します。  
  
5.  2 つのサブメニュー項目を `&Import from` サブメニュー項目に追加し、それらの <xref:System.Windows.Forms.ToolStripItem.Text%2A> プロパティをそれぞれ `&Word` と `&Excel` に設定します。  
  
6.  フォームをプロジェクトに追加し、<xref:System.Windows.Forms.MenuStrip> をフォームに追加して、`Form2` <xref:System.Windows.Forms.MenuStrip> の <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> プロパティを `true` に設定します。  
  
7.  トップレベル メニュー項目を `Form2` <xref:System.Windows.Forms.MenuStrip> に追加し、その <xref:System.Windows.Forms.ToolStripItem.Text%2A> プロパティを `&File` に設定します。  
  
8.  `Form2` の `&File` メニューにサブメニュー項目を追加します。追加する順番は、<xref:System.Windows.Forms.ToolStripSeparator>、`&Save`、`&Close` `and Save`、およびもう 1 つの <xref:System.Windows.Forms.ToolStripSeparator> となります。  
  
9. 次の表に示すように、`Form2` メニュー項目の <xref:System.Windows.Forms.MergeAction> プロパティと <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> プロパティを設定します。  
  
    |Form2 メニュー項目|MergeAction 値|MergeIndex 値|  
    |------------------|-------------------|------------------|  
    |File|MatchOnly|\-1|  
    |\[Separator\]|\[挿入\]|2|  
    |保存|\[挿入\]|3|  
    |\[保存して閉じる\]|\[挿入\]|4|  
    |\[Separator\]|\[挿入\]|5|  
  
10. `&Open` <xref:System.Windows.Forms.ToolStripMenuItem> の <xref:System.Windows.Forms.Control.Click> イベントのイベント ハンドラーを作成します。  
  
11. このイベント ハンドラー内に次のようなコード例を挿入し、`Form1` の MDI 子フォームとして `Form2` の新しいインスタンスを作成および表示します。  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
  
    ```  
  
    ```csharp  
    private void openToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
  
    ```  
  
12. 次のようなコードを `&Open` <xref:System.Windows.Forms.ToolStripMenuItem> に配置し、イベント ハンドラーを登録します。  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
  
    ```  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   `Form1` と `Form2` という名前の 2 つの <xref:System.Windows.Forms.Form> コントロール。  
  
-   `menuStrip1` という名前の `Form1` の <xref:System.Windows.Forms.MenuStrip> コントロール、および `menuStrip2` という名前の `Form2` の <xref:System.Windows.Forms.MenuStrip> コントロール。  
  
-   <xref:System?displayProperty=fullName> アセンブリおよび <xref:System.Windows.Forms?displayProperty=fullName> アセンブリへの参照。  
  
## 参照  
 [方法 : MDI 親フォームを作成する](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)   
 [方法 : MDI 子フォームを作成する](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)   
 [MenuStrip コントロールの概要](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)