---
title: TableLayoutPanel コントロールにおける AutoSize 動作
ms.date: 03/30/2017
helpviewer_keywords:
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- localizing forms
- layout [Windows Forms], AutoSize
- sizing [Windows Forms], automatic
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- automatic sizing
- AutoSizeMode property
ms.assetid: 9233e0c3-2fa6-405e-8701-959479b1250e
ms.openlocfilehash: 497991106d151cfe1f3944977828e9c77c27e526
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526310"
---
# <a name="autosize-behavior-in-the-tablelayoutpanel-control"></a>TableLayoutPanel コントロールにおける AutoSize 動作
## <a name="distinct-autosize-behaviors"></a>個別の AutoSize 動作  
 <xref:System.Windows.Forms.TableLayoutPanel>コントロールは、次のように自動サイズ変更動作をサポートしています。  
  
-   を介して、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティです。  
  
-   を介して、<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>プロパティを<xref:System.Windows.Forms.TableLayoutPanel>コントロールの列と行のスタイル。  
  
### <a name="the-autosize-property-with-row-and-column-styles"></a>行と列のスタイル AutoSize プロパティ  
 次の表に、間の相互作用、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティおよび<xref:System.Windows.Forms.TableLayoutPanel>コントロールの列と行のスタイル。  
  
|Autosize プロパティの設定|スタイルの相互作用|  
|----------------------|-----------------------|  
|`false`|<xref:System.Windows.Forms.TableLayoutPanel>コントロールが右に左からプロセスが実行され、または次の順序で行または列の領域が割り当てられます。<br /><br /> 1.場合、<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>プロパティに設定されている<xref:System.Windows.Forms.SizeType.Absolute>、ピクセル数で指定された<xref:System.Windows.Forms.ColumnStyle.Width%2A>または<xref:System.Windows.Forms.RowStyle.Height%2A>が割り当てられます。<br />2.場合、<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>プロパティに設定されている<xref:System.Windows.Forms.SizeType.AutoSize>、子コントロールのによって返されるピクセル数<xref:System.Windows.Forms.Control.GetPreferredSize%2A>メソッドが割り当てられます。<br />3.すべてのスペース後<xref:System.Windows.Forms.SizeType.Absolute>と<xref:System.Windows.Forms.SizeType.AutoSize>列または行が割り当てられる列や行の<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A>'éý'<xref:System.Windows.Forms.SizeType.Percent>比例して残りの空き領域を割り当てるために使用されます|  
|`true`|例外と、以前の相互作用のようなを<xref:System.Windows.Forms.SizeType.Percent>列または行は、上の自動サイズ変更を取得します。<br /><br /> <xref:System.Windows.Forms.TableLayoutPanel>コントロールは、十分な空き領域を作成する行、列を拡張できるようになしの列または行を<xref:System.Windows.Forms.SizeType.Percent>スタイルがそのコンテンツをクリップします。 <xref:System.Windows.Forms.TableLayoutPanel>コントロールが比例的によると、新しい領域を割り当て、<xref:System.Windows.Forms.ColumnStyle.Width%2A>または<xref:System.Windows.Forms.RowStyle.Height%2A>プロパティです。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [TableLayoutPanel コントロールの概要](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-overview.md)
