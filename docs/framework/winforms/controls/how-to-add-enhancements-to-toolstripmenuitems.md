---
title: "方法 : ToolStripMenuItems に拡張機能を追加する | Microsoft Docs"
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
  - "チェック マーク, 追加 (メニューに)"
  - "コマンド [Windows フォーム], グループ化 (メニューの)"
  - "イメージ [Windows フォーム], 追加 (メニューに)"
  - "ショートカット キー, 表示 (メニューに)"
  - "メニュー項目, 追加 (チェック マークを)"
  - "メニュー項目, 追加 (イメージを)"
  - "メニュー項目, 表示 (アクセス キーを)"
  - "メニュー項目, 表示 (ショートカット キーを)"
  - "メニュー項目, 表示 (区切り記号を)"
  - "メニュー, グループ化 (コマンドを)"
  - "区切り記号, 表示 (メニューに)"
  - "ToolStripMenuItem"
  - "ToolStripMenuItem, 追加 (チェック マークを)"
  - "ToolStripMenuItem, 追加 (イメージを)"
  - "ToolStripMenuItem, 表示 (アクセス キーを)"
  - "ToolStripMenuItem, 表示 (ショートカット キーを)"
  - "ToolStripMenuItem, 表示 (区分線を)"
  - "ToolStripSeparator, 表示 (MenuStrips に)"
ms.assetid: aa5f19bb-b545-4378-bfa6-36ba592f0d7c
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : ToolStripMenuItems に拡張機能を追加する
<xref:System.Windows.Forms.MenuStrip> コントロールと <xref:System.Windows.Forms.ContextMenuStrip> コントロールの操作性は、次の方法で向上できます。  
  
-   チェック マークを追加して、機能を有効にするかどうか \(ワード プロセッサ アプリケーションの余白部分にルーラーを表示するかどうかなど\) を指定したり、現在表示されているファイルをファイル リスト \(**\[ウィンドウ\]** メニューなど\) に示したりします。  
  
-   メニュー コマンドを視覚的に表現するイメージを追加します。  
  
-   ショートカット キーを表示して、マウスの代わりにキーボードを使ってコマンドを実行できるようにします。  たとえば、Ctrl キーを押しながら C キーを押すと、**Copy** コマンドが実行されます。  
  
-   アクセス キーを表示して、マウスの代わりにキーボードを使ってメニューを移動できるようにします。  たとえば、Alt キーを押しながら F キーを押すと、**\[ファイル\]** メニューが選択されます。  
  
-   区分線を表示して、関連するコマンドをグループ化し、メニューを読みやすくします。  
  
### メニュー コマンドにチェック マークを表示するには  
  
-   <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> プロパティを `true` に設定します。  
  
     これにより、<xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> プロパティも `true` に設定されます。  この手順を使用するのは、メニュー コマンドを選択していなくても、既定でチェック マークを付けて表示する場合のみです。  
  
### クリックするたびに状態が切り替わるチェック マークを表示するには  
  
-   メニュー コマンドの <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> プロパティを `true` に設定します。  
  
### メニュー コマンドにイメージを追加するには  
  
-   メニュー コマンドの <xref:System.Windows.Forms.ToolStripItem.Image%2A> プロパティにイメージの名前を設定します。  このメニュー コマンドの <xref:System.Windows.Forms.ToolStripItemDisplayStyle> プロパティが <xref:System.Windows.Forms.ToolStripItemDisplayStyle> または <xref:System.Windows.Forms.ToolStripItemDisplayStyle> に設定されている場合は、イメージを表示できません。  
  
> [!NOTE]
>  イメージの余白には、チェック マークを表示することもできます。  また、イメージの <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> プロパティを `true` に設定すると、実行時にイメージの周りにハッチングされた境界線が表示されます。  
  
### メニュー コマンドのショートカット キーを表示するには  
  
-   メニュー コマンドの <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> プロパティに適切なキーの組み合わせ \(たとえば、**\[開く**\] メニュー コマンドの場合には、Ctrl \+ O など\) を設定し、<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> プロパティを `true` に設定します。  
  
### メニュー コマンドのカスタム ショートカット キーを表示するには  
  
-   メニュー コマンドの <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> プロパティに適切なキーの組み合わせ \(Shift \+ Ctrl \+ O ではなく、Ctrl \+ Shift \+ O など\) を設定し、<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> プロパティを `true` に設定します。  
  
### メニュー コマンドのアクセス キーを表示するには  
  
-   メニュー コマンドの <xref:System.Windows.Forms.ToolStripItem.Text%2A> プロパティを設定するときは、アクセス キーとして下線を付ける文字の前にアンパサンド \(&\) を入力します。  たとえば、メニュー項目の <xref:System.Windows.Forms.ToolStripItem.Text%2A> プロパティに「`開く(&O)`」と入力すると、メニュー コマンドには "開く\(**O**\)" と表示されます。  
  
     このメニュー コマンドに移動するには、Alt キーを押して <xref:System.Windows.Forms.MenuStrip> にフォーカスを移し、目的のメニューのアクセス キーを押します。  メニューが開き、アクセス キーが設定されたメニュー項目が表示されたら、アクセス キーを押すだけで目的のメニュー コマンドを選択できます。  
  
> [!NOTE]
>  同じメニュー システムに Alt \+ F を 2 回定義するなど、アクセス キーを重複して定義することは避けてください。  重複するアクセス キーの選択順序は保証されません。  
  
### メニュー コマンドの間に区分線を表示するには  
  
-   <xref:System.Windows.Forms.MenuStrip> と、それに含める項目を定義した後に、<xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> メソッドまたは <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> メソッドを使用して、メニュー コマンドと <xref:System.Windows.Forms.ToolStripSeparator> コントロールを任意の順序で <xref:System.Windows.Forms.MenuStrip> に追加します。  
  
     \[Visual Basic\]  
  
    ```  
    ' This code adds a top-level File menu to the MenuStrip.  
    Me.menuStrip1.Items.Add(New ToolStripMenuItem() _  
    {Me.fileToolStripMenuItem})  
  
    ' This code adds the New and Open menu commands, a separator bar,   
    ' and the Save and Exit menu commands to the top-level File menu,   
    ' in that order.  
    Me.fileToolStripMenuItem.DropDownItems.AddRange(New _  
    ToolStripMenuItem() {Me.newToolStripMenuItem, _  
    Me.openToolStripMenuItem, Me.toolStripSeparator1, _  
    Me.saveToolStripMenuItem, Me.exitToolStripMenuItem})  
  
    ```  
  
     \[C\#\]  
  
    ```  
    // This code adds a top-level File menu to the MenuStrip.  
    this.menuStrip1.Items.Add(new ToolStripItem[]_  
    {this.fileToolStripMenuItem});  
  
    // This code adds the New and Open menu commands, a separator bar,   
    // and the Save and Exit menu commands to the top-level File menu,   
    // in that order.  
    this.fileToolStripMenuItem.DropDownItems.AddRange(new _  
    ToolStripItem[] {  
    this.newToolStripMenuItem,  
    this.openToolStripMenuItem,  
    this.toolStripSeparator1,  
    this.saveToolStripMenuItem,  
    this.exitToolStripMenuItem});  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStripMenuItem>   
 [MenuStrip コントロールの概要](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)