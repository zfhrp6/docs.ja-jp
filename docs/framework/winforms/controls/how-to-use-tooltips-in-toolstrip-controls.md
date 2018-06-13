---
title: '方法 : ToolStrip コントロールにツールヒントを使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
ms.openlocfilehash: 2b10b3fcf3930d5848f1d7a9602cfcc945bc8975
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534074"
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a>方法 : ToolStrip コントロールにツールヒントを使用する
表示することができます、<xref:System.Windows.Forms.ToolTip>の<xref:System.Windows.Forms.ToolStrip>コントロールの設定で目的のコントロール<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>プロパティを`true`です。  
  
### <a name="to-display-a-tooltip"></a>ツールヒントを表示するには  
  
-   設定、<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>するコントロールのプロパティ`true`です。  
  
     既定値<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType>は`true`、および既定値の<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType>と<xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType>は`false`します。  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a>ToolStripButton のツールヒント テキストの ToolTipText プロパティを使用するには  
  
1.  設定、<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>するボタンのプロパティ`true`です。  
  
2.  設定、<xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType>するボタンのプロパティ`false`です。  
  
     `AutoToolTip`プロパティは`true`に対して既定で<xref:System.Windows.Forms.ToolStripButton>、 <xref:System.Windows.Forms.ToolStripDropDownButton>、および<xref:System.Windows.Forms.ToolStripSplitButton>です。  
  
     A<xref:System.Windows.Forms.ToolStripButton>を使用してその`Text`プロパティを<xref:System.Windows.Forms.ToolTip>既定テキストです。 カスタム テキストを表示するこの手順を使用して、 <xref:System.Windows.Forms.ToolStripButton><xref:System.Windows.Forms.ToolTip>です。  
  
> [!NOTE]
>  設定した場合<xref:System.Windows.Forms.ToolStripItemDisplayStyle>に<xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>または<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>ボタンのテキストは表示されませんが、ツール ヒントが表示されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>  
 <xref:System.Windows.Forms.ToolStripButton>  
 <xref:System.Windows.Forms.ToolStripDropDownButton>  
 <xref:System.Windows.Forms.ToolStripSplitButton>  
 [ToolStrip コントロールの概要](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
