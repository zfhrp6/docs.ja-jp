---
title: '方法 : TableLayoutPanel コントロール内でコントロールを配置して伸縮する'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms], stretching controls
- controls [Windows Forms], stretching
- controls [Windows Forms], aligning
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
ms.openlocfilehash: 5abe233a240e74e41d4defad060383aec155ea71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a>方法 : TableLayoutPanel コントロール内でコントロールを配置して伸縮する
内のコントロールを拡大して整列することができます、<xref:System.Windows.Forms.TableLayoutPanel>で、<xref:System.Windows.Forms.Control.Anchor%2A>と<xref:System.Windows.Forms.Control.Dock%2A>プロパティです。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-align-and-stretch-a-control"></a>配置して伸縮コントロール  
  
1.  ドラッグ、<xref:System.Windows.Forms.TableLayoutPanel>から制御、**ツールボックス**フォーム上にします。  
  
2.  ドラッグ、<xref:System.Windows.Forms.Button>から制御、**ツールボックス**の左上隅のセルに、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。 <xref:System.Windows.Forms.Button>コントロールがセルの中央に配置します。  
  
3.  値を設定、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを`Left,Right`です。 <xref:System.Windows.Forms.Button>端まで拡大に合わせてセルの幅を制御します。  
  
4.  値を設定、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを`Top,Bottom`です。 <xref:System.Windows.Forms.Button>セルの高さが揃うように端まで拡大を制御します。  
  
5.  値を設定、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.Fill>です。 <xref:System.Windows.Forms.Button>コントロールがセルを満たす展開します。  
  
6.  値を設定、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.None>です。 <xref:System.Windows.Forms.Button>コントロールは、元のサイズを返し、セルの左上隅に移動します。 **Windows フォーム デザイナー**設定が、<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを`Top, Left`です。  
  
7.  値を設定、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを`Bottom,Right`です。 <xref:System.Windows.Forms.Button>コントロールがセルの右下隅に移動します。  
  
8.  値を設定、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Anchor%2A>プロパティを<xref:System.Windows.Forms.AnchorStyles.None>です。 <xref:System.Windows.Forms.Button>コントロールがセルの中央に移動します。  
  
## <a name="see-also"></a>関連項目  
 [TableLayoutPanel コントロール](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
