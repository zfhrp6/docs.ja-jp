---
title: '方法 : ToolStripMenuItems に拡張機能を追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- commands [Windows Forms], grouping on menus
- check marks [Windows Forms], adding to menus
- ToolStripMenuItems [Windows Forms], displaying access keys
- menus [Windows Forms], grouping commands
- menu items [Windows Forms], displaying shortcut keys
- ToolStripMenuItems
- separators [Windows Forms], displaying on menus
- menu items [Windows Forms], showing separators
- menu items [Windows Forms], adding check marks
- ToolStripMenuItems [Windows Forms], adding check marks
- menu items [Windows Forms], adding images
- ToolStripSeparators [Windows Forms], displaying on MenuStrips
- menu items [Windows Forms], displaying access keys
- ToolStripMenuItems [Windows Forms], displaying shortcut keys
- ToolStripMenuItems [Windows Forms], adding images
- keyboard shortcuts [Windows Forms], displaying on menus
- images [Windows Forms], adding to menus
- ToolStripMenuItems [Windows Forms], showing separator bars
ms.assetid: aa5f19bb-b545-4378-bfa6-36ba592f0d7c
ms.openlocfilehash: 37843d27211bd07c2749b3e6fc14ec03d7bf570d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a>方法 : ToolStripMenuItems に拡張機能を追加する
操作性を強化できます<xref:System.Windows.Forms.MenuStrip>と<xref:System.Windows.Forms.ContextMenuStrip>次の方法でコントロール。  
  
-   ワード プロセッシング アプリケーションでは、余白部分に、ルーラーを表示するかどうかなどの機能がオンまたはオフになっているかどうかを指定する、またはどのファイルの一覧では、対象のファイルなど、表示されているを示すためにチェック マークを追加、**ウィンドウ**メニューです。  
  
-   メニュー コマンドを視覚的に表現するイメージを追加します。  
  
-   コマンドを実行するために、マウスの代わりにキーボードを提供するショートカット キーを表示します。 たとえば、実行 ctrl キーを押しながら C キーを押して、**コピー**コマンド。  
  
-   メニューのナビゲーションのマウス、キーボードの代わりを提供するアクセス キーを表示します。 たとえば、選択 ALT キーを押しながら F キーを押すと、**ファイル**メニュー。  
  
-   関連するコマンドをグループ化し、メニューを読みやすくのセパレーター バーを表示します。  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a>メニュー コマンドにチェック マークを表示するには  
  
-   設定の<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>プロパティを`true`です。  
  
     これも設定されている、<xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A>プロパティを`true`です。 既定では、選択されているかどうかに関係なく、チェック マークを付けて表示するメニュー コマンドを追加する場合にのみ、この手順を使用します。  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a>クリックするたびに状態を変更するチェック マークを表示するには  
  
-   メニュー コマンドの設定<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>プロパティを`true`です。  
  
### <a name="to-add-an-image-to-a-menu-command"></a>メニュー コマンドにイメージを追加するには  
  
-   メニュー コマンドの設定<xref:System.Windows.Forms.ToolStripItem.Image%2A>プロパティをイメージの名前にします。 場合、<xref:System.Windows.Forms.ToolStripItemDisplayStyle>このメニュー コマンドのプロパティに設定されて<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>または<xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>イメージを表示することはできません。  
  
> [!NOTE]
>  イメージの余白も表示できます、チェック マークできます。 また、設定することができます、<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>するイメージのプロパティ`true`、し、イメージは、実行時にハッチ境界線と共に表示されます。  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a>メニュー コマンドのショートカット キーを表示するには  
  
-   メニュー コマンドの設定<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>プロパティの CTRL + O など、目的のキーボードの組み合わせを**開く**メニュー コマンド、およびセット、<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>プロパティを`true`です。  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a>メニュー コマンドのカスタム ショートカット キーを表示するには  
  
-   メニュー コマンドの設定<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A>CTRL + SHIFT + O はなく、shift キーを押しながら CTRL + O、およびセットなど、目的のキーボードの組み合わせにプロパティ、<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>プロパティを`true`です。  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a>メニュー コマンドのアクセス キーを表示するには  
  
-   設定すると、<xref:System.Windows.Forms.ToolStripItem.Text%2A>メニュー コマンドは、プロパティには、アンパサンドを入力してください (&) は、アクセス キーとして下線が引か 文字の前にします。 たとえば、入力`&Open`として、<xref:System.Windows.Forms.ToolStripItem.Text%2A>として表示されるメニュー コマンド、メニュー項目のプロパティと、 **O**ペン。  
  
     このメニューにコマンドを移動するにフォーカスを与える alt キーを押して、<xref:System.Windows.Forms.MenuStrip>メニュー名のアクセス キーを押します。 メニューが開き、アクセス キーを持つ項目を表示、ときにのみ、メニュー コマンドを選択するアクセス キーを押す必要があります。  
  
> [!NOTE]
>  メニューに同じシステムで 2 回 ALT キーを押しながら F キーを定義するなどの重複するアクセス キーを定義しないようにします。 重複するアクセス キーの選択順序を保証できません。  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a>メニュー コマンドの間の区切り線を表示するには  
  
-   定義した後、<xref:System.Windows.Forms.MenuStrip>および登録するには、項目を使用して、<xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A>または<xref:System.Windows.Forms.ToolStripItemCollection.Add%2A>とメニュー コマンドを追加するメソッドと<xref:System.Windows.Forms.ToolStripSeparator>コントロールを<xref:System.Windows.Forms.MenuStrip>順序で。  
  
    ```vb  
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
  
    ```csharp  
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
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [MenuStrip コントロールの概要](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
