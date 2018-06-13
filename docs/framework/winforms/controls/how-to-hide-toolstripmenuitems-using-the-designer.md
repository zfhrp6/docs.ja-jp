---
title: '方法 : デザイナーを使用して ToolStripMenuItems を非表示にする'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
ms.openlocfilehash: b0018516b9ac337cea3716c4b2eddc6eb859dbb0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534367"
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a>方法 : デザイナーを使用して ToolStripMenuItems を非表示にする
メニュー項目を非表示には、アプリケーションのユーザー インターフェイス (UI) を制御し、ユーザーのコマンドを制限する方法です。 多くの場合、すべてのメニュー項目が利用できない場合は、メニュー全体を非表示にするされます。 これにより、ユーザーの混乱を避けることが少ないが表示されます。 さらに、ことができますを非表示にして、メニューまたはメニュー項目を無効にするように単独で非表示がショートカット キーを使用して、メニュー コマンドにアクセスできないユーザーを妨げません。 メニュー項目を無効にする方法の詳細については、次を参照してください。[する方法: ToolStripMenuItems を無効にするデザイナーの使用](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a>トップレベル メニューとサブメニュー項目を非表示にするには  
  
1.  トップレベルのメニュー項目を選択し、設定、<xref:System.Windows.Forms.ToolStripItem.Visible%2A>または<xref:System.Windows.Forms.ToolStripItem.Available%2A>プロパティを`false`です。  
  
     トップレベルのメニュー項目を非表示にするときにそのメニュー内のすべてのメニュー項目も表示されません。 クリックしてできる場所以外の場合、<xref:System.Windows.Forms.MenuStrip>設定後<xref:System.Windows.Forms.ToolStripItem.Visible%2A>に`false`、全体のトップレベル メニュー項目とサブメニュー項目の操作の実行時の効果を示すため、フォームから消失します。 デザイン時に非表示のトップレベル メニュー項目を表示するのには、をクリックして、<xref:System.Windows.Forms.MenuStrip>で、**コンポーネント トレイ**の**ドキュメント アウトライン**、またはプロパティ グリッドの上部にあります。  
  
> [!NOTE]
>  マージ シナリオでは複数のドキュメント インターフェイス (MDI) 子メニューを除くメニュー全体を非表示にはほとんどありません。  
  
### <a name="to-hide-a-submenu-item"></a>サブメニュー項目を非表示にするには  
  
1.  サブメニュー項目を選択し、設定、<xref:System.Windows.Forms.ToolStripItem.Visible%2A>プロパティを`false`です。  
  
     サブメニュー項目を非表示にするときにそのまま表示されてデザイン時に、フォーム上の作業をさらに簡単に選択できるようにします。 実行時に実際には表示されません。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>  
 <xref:System.Windows.Forms.ToolStripItem.Available%2A>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>  
 [MenuStrip コントロールの概要](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)  
 [方法: デザイナーを使用して ToolStripMenuItems を無効にする](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md)
