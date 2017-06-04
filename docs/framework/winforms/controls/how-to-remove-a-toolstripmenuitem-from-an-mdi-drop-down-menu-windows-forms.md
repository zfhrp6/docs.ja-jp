---
title: "方法 : ToolStripMenuItem を MDI ドロップダウン メニューから削除する (Windows フォーム)  | Microsoft Docs"
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
  - "メニュー項目, 削除 (MDI ドロップダウン メニューから)"
  - "MenuStrip コントロール [Windows フォーム], マージ"
  - "MenuStrip コントロール [Windows フォーム], 削除"
ms.assetid: bdafe60d-82ee-45bc-97fe-eeefca6e54c1
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : ToolStripMenuItem を MDI ドロップダウン メニューから削除する (Windows フォーム) 
アプリケーションの中には、マルチ ドキュメント インターフェイス \(MDI\) 子ウィンドウの種類が MDI 親ウィンドウと異なるものもあります。  たとえば、MDI 親がスプレッドシートで、MDI 子がグラフの場合があります。  そのような場合は、異なる種類の MDI 子ウィンドウがアクティブになったときに、MDI 子メニューの内容で MDI 親メニューの内容を更新する必要があります。  
  
 次のプロシージャでは、<xref:System.Windows.Forms.Form.IsMdiContainer%2A>、<xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>、<xref:System.Windows.Forms.MergeAction>、および <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> の各プロパティを使用して、メニュー項目を MDI 親メニューのドロップダウン部分から削除します。  MDI 子ウィンドウを閉じると、削除したメニュー項目が MDI 親メニューに復元されます。  
  
### MenuStrip を MDI ドロップダウン メニューから削除するには  
  
1.  フォームを作成し、その <xref:System.Windows.Forms.Form.IsMdiContainer%2A> プロパティを `true` に設定します。  
  
2.  <xref:System.Windows.Forms.MenuStrip> を `Form1` に追加し、<xref:System.Windows.Forms.MenuStrip> の <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> プロパティを `true` に設定します。  
  
3.  トップレベル メニュー項目をに追加し`Form1`<xref:System.Windows.Forms.MenuStrip>`&File` に <xref:System.Windows.Forms.Control.Text%2A> のプロパティを設定します。  
  
4.  3 つのサブメニュー項目を `&File` メニュー項目に追加し、それらの <xref:System.Windows.Forms.ToolStripItem.Text%2A> プロパティをそれぞれ `&Open`、`&Import from`、および `E&xit` に設定します。  
  
5.  2 つのサブメニュー項目を `&Import from` サブメニュー項目に追加し、それらの <xref:System.Windows.Forms.ToolStripItem.Text%2A> プロパティをそれぞれ `&Word` と `&Excel` に設定します。  
  
6.  プロジェクトにフォームを追加しそのフォームに <xref:System.Windows.Forms.MenuStrip> を追加し`true` に `Form2`<xref:System.Windows.Forms.MenuStrip> の <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> のプロパティを設定します。  
  
7.  トップレベル メニュー項目をに追加し`Form2`<xref:System.Windows.Forms.MenuStrip>`&File` に <xref:System.Windows.Forms.ToolStripItem.Text%2A> のプロパティを設定します。  
  
8.  `&Import from` サブメニュー項目を `Form2` の `&File` メニューに追加し、`&Word` サブメニュー項目を `&File` メニューに追加します。  
  
9. 次の表に示すように、`Form2` メニュー項目の <xref:System.Windows.Forms.MergeAction> プロパティと <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> プロパティを設定します。  
  
    |Form2 メニュー項目|MergeAction 値|MergeIndex 値|  
    |------------------|-------------------|------------------|  
    |File|MatchOnly|\-1|  
    |Import from|MatchOnly|\-1|  
    |Word|\[削除\]|\-1|  
  
10. `Form1` では`&Open`<xref:System.Windows.Forms.ToolStripMenuItem> の <xref:System.Windows.Forms.Control.Click> のイベントのイベント ハンドラーを作成します。  
  
11. このイベント ハンドラー内に次のようなコード例を挿入し、`Form1` の MDI 子フォームとして `Form2` の新しいインスタンスを作成および表示します。  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
  
    ```  
  
     \[C\#\]  
  
    ```  
    private void openToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
  
    ```  
  
12. 次のようなイベント ハンドラーを登録するに `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> にコードを配置します。  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new _  
    System.EventHandler(this.openToolStripMenuItem_Click);  
  
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