---
title: "方法 : ToolStrip コントロールにツールヒントを使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bc52dd1b629829564532fd93650737f51e5d7f24
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
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
