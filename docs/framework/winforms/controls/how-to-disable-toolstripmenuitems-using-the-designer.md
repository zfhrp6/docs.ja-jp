---
title: '方法 : デザイナーを使用して ToolStripMenuItems を無効にする'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
ms.openlocfilehash: 3ce18d40910145a076cc7084e2fba8ee0229c21f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a>方法 : デザイナーを使用して ToolStripMenuItems を無効にする
制限またはを有効にして、ユーザー アクティビティを応答でのメニュー項目を無効にすると、ユーザーが実行できるコマンドの範囲を広げることができます。 メニュー項目は既定で有効には、作成されるが、これで調整できる場合に、<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>プロパティです。 デザイン時にこのプロパティを操作することができます、**プロパティ**ウィンドウまたはプログラムによってコードで設定します。 詳細については、次を参照してください。[する方法: ToolStripMenuItems を無効にする](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-disable-a-menu-item-at-design-time"></a>デザイン時にメニュー項目を無効にするには  
  
1.  フォームで選択されたメニュー項目を含む設定、<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>プロパティを`false`です。  
  
    > [!TIP]
    >  メニューの最初または最上位レベルのメニュー項目を無効にするには、メニュー内に含まれるすべてのメニュー項目が無効にします。 同様に、サブメニュー項目を持つメニュー項目を無効にするには、サブメニュー項目が無効にします。 指定されたメニュー上のすべてのコマンドがユーザーに利用可能な場合は、この場合は、クリーンなユーザー インターフェイスとして両方を非表示にし、メニュー全体を無効にすることをお勧めプログラミングと見なされます。 非表示にする必要があり、無効にします] メニューの [非表示にするだけでは、ショートカット キーを使用してメニュー コマンドにアクセスを妨げません。 設定、<xref:System.Windows.Forms.ToolStripItem.Visible%2A>をトップレベルのメニュー項目のプロパティ`false`メニュー全体を非表示にします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [方法: ToolStripMenuItems を非表示にする](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)  
 [MenuStrip コントロールの概要](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
