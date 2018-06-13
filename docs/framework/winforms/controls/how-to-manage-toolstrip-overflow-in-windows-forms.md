---
title: '方法 : Windows フォームの ToolStrip オーバーフローを管理する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], managing overflow
- toolbars [Windows Forms], managing overflow
- examples [Windows Forms], toolbars
- CanOverflow property
ms.assetid: fa10e0ad-4cbf-4c0d-9082-359c2f855d4e
ms.openlocfilehash: 32bbc06320f0dc7f096a4b9021bebfbefedaf8f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534893"
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a>方法 : Windows フォームの ToolStrip オーバーフローを管理する
ときのすべての項目、<xref:System.Windows.Forms.ToolStrip>コントロールが割り当てられた領域に収まらないでオーバーフロー機能を有効にすることができます、<xref:System.Windows.Forms.ToolStrip>固有の仕様のオーバーフロー動作を決定し、 <xref:System.Windows.Forms.ToolStripItem>s。  
  
 追加すると<xref:System.Windows.Forms.ToolStripItem>に割り当てられるよりも多くの領域を必要とする、<xref:System.Windows.Forms.ToolStrip>フォームの現在のサイズを指定、<xref:System.Windows.Forms.ToolStripOverflowButton>で自動的に表示されます、<xref:System.Windows.Forms.ToolStrip>です。 <xref:System.Windows.Forms.ToolStripOverflowButton>が表示されたら、オーバーフローが有効な項目は、ドロップ ダウン オーバーフロー メニューに移動します。 これにより、カスタマイズし、優先順位を設定する方法、<xref:System.Windows.Forms.ToolStrip>項目は、さまざまなフォームのサイズを正しく調整します。 使用して、オーバーフローになったときに、アイテムの外観を変更することも、<xref:System.Windows.Forms.ToolStripItem.Placement%2A>と<xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType>プロパティおよび<xref:System.Windows.Forms.ToolStrip.LayoutCompleted>イベント。 複数デザイン時または実行時に、フォームを拡大する場合<xref:System.Windows.Forms.ToolStripItem>s は、メイン表示できる<xref:System.Windows.Forms.ToolStrip>と<xref:System.Windows.Forms.ToolStripOverflowButton>フォームのサイズを小さくしない可能性がありますも非表示になります。  
  
### <a name="to-enable-overflow-on-a-toolstrip-control"></a>ToolStrip コントロールのオーバーフローを有効にするには  
  
-   いることを確認、<xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>プロパティに設定されていない`false`の<xref:System.Windows.Forms.ToolStrip>です。 既定値は、`True` です。  
  
     ときに<xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>は`True`(既定)、<xref:System.Windows.Forms.ToolStripItem>ドロップダウン オーバーフロー メニューに送信されるときのコンテンツ、<xref:System.Windows.Forms.ToolStripItem>水平方向の幅を超える<xref:System.Windows.Forms.ToolStrip>または垂直方向の高さ<xref:System.Windows.Forms.ToolStrip>です。  
  
### <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a>特定 ToolStripItem のオーバーフロー動作を指定するには  
  
-   設定、<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>のプロパティ、<xref:System.Windows.Forms.ToolStripItem>目的の値にします。 表示される値は`Always`、 `Never`、および`AsNeeded`です。 デフォルトで`AsNeeded`です。  
  
    ```vb  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never;  
    ```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripOverflowButton>  
 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>  
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>  
 [ToolStrip コントロールの概要](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [ToolStrip コントロールのアーキテクチャ](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [ToolStrip テクノロジの概要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
