---
title: '方法 : Windows フォーム内の ToolStrip 項目の間隔と配置を変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 7951a545fd8cbd0ae30907922551216161171a8d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531265"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a>方法 : Windows フォーム内の ToolStrip 項目の間隔と配置を変更する
<xref:System.Windows.Forms.ToolStrip>コントロールがサイズ変更の間隔などのレイアウト機能を完全にサポート<xref:System.Windows.Forms.ToolStripItem>互いを基準として、コントロールの配置のコントロールに対して、<xref:System.Windows.Forms.ToolStrip>とを基準とするコントロールの間の間隔、<xref:System.Windows.Forms.ToolStrip>です。  
  
 の既定値、<xref:System.Windows.Forms.ToolStripItem.AutoSize%2A>プロパティは`true`、コントロールはサイズが自動的に設定しない限り、<xref:System.Windows.Forms.ToolStripItem.AutoSize%2A>プロパティを`false`です。  
  
### <a name="to-manually-size-a-toolstripitem"></a>ToolStripItem を手動で調整するには  
  
1.  設定、<xref:System.Windows.Forms.ToolStripItem.AutoSize%2A>プロパティを`false`関連付けられたコントロール。  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2.  設定、<xref:System.Windows.Forms.ToolStripItem.Size%2A>プロパティに関連付けられた希望どおり<xref:System.Windows.Forms.ToolStripItem>です。  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a>ToolStripItem の間隔を設定するには  
  
1.  ピクセル単位で、目的の値を挿入、<xref:System.Windows.Forms.ToolStripItem.Margin%2A>関連付けられたコントロールのプロパティです。  
  
     値、<xref:System.Windows.Forms.ToolStripItem.Margin%2A>プロパティは、この順序で、項目と隣接するアイテムの間隔を指定します。 左、上、右、および下です。  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a>コマンド バーの右側に ToolStripItem を配置するには  
  
1.  設定、<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>プロパティを<xref:System.Windows.Forms.ToolStripItemAlignment.Right>関連付けられたコントロール。 既定では、<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>に設定されている<xref:System.Windows.Forms.ToolStripItemAlignment.Left>の左側にコントロールを配置する、<xref:System.Windows.Forms.ToolStrip>です。  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a>ToolStrip の ToolStrip 項目を整理するには  
  
-   設定、<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>プロパティの値を<xref:System.Windows.Forms.ToolStripLayoutStyle>します。  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.Control.Layout>  
 <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>  
 <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>  
 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>  
 <xref:System.Windows.Forms.ToolStripItem.Placement%2A>  
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>  
 [ToolStrip コントロールの概要](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [ToolStrip コントロールのアーキテクチャ](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [ToolStrip テクノロジの概要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
