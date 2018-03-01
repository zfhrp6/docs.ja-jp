---
title: "TableLayoutPanel コントロールの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TableLayoutPanel
helpviewer_keywords:
- controls [Windows Forms], resizing
- resizable controls [Windows Forms]
- Windows Forms controls, proportional resizing
- Windows Forms, proportional resizing of controls
- layout [Windows Forms], TableLayoutPanel control
- TableLayoutPanel control [Windows Forms], about TableLayoutPanel control
ms.assetid: 337661c8-61cb-44ee-93e0-3662bddec327
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 614887524a49e1163b3049111895166995fdace4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="tablelayoutpanel-control-overview"></a>TableLayoutPanel コントロールの概要
<xref:System.Windows.Forms.TableLayoutPanel> コントロールは、その内容をグリッド内に配置します。 レイアウトがデザイン時および実行時の両方で実行されるため、アプリケーション環境の変化に応じて動的に変更できます。 これにより、パネル内のコントロールを適切にサイズ変更することができるため、親コントロールのサイズ変更や、ローカライズによるテキスト長の変更などの変更に対応できます。  
  
 Windows フォーム コントロールは、<xref:System.Windows.Forms.TableLayoutPanel> の他のインスタンスを含めて、<xref:System.Windows.Forms.TableLayoutPanel> コントロールの子にすることができます。 これにより、実行時の変化に適応する高度なレイアウトを構築することができます。  
  
 <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>、<xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>、および <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> プロパティの値に応じて、<xref:System.Windows.Forms.TableLayoutPanel> コントロールを追加するときに新しいコントロールに合わせて拡張できます。 <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> プロパティまたは <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> プロパティのいずれかを 0 の値に設定すると、<xref:System.Windows.Forms.TableLayoutPanel> が対応する方向にバインド解除されます。  
  
 <xref:System.Windows.Forms.TableLayoutPanel> コントロールが完全に子コントロールになった後で、(水平または垂直の) 展開の方向を制御することもできます。 既定では、<xref:System.Windows.Forms.TableLayoutPanel> コントロールは行を追加することで下方向に拡張します。  
  
 既定の動作とは異なる方法で行と列を動作させる場合は、<xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> プロパティと <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> プロパティを使用して、行と列のプロパティを制御できます。 行または列のプロパティを個別に設定することができます。  
  
 <xref:System.Windows.Forms.TableLayoutPanel> コントロールは、その子コントロールに `Cell`、`Column`、`Row`、`ColumnSpan`、および `RowSpan` の各プロパティを追加します。  
  
 子コントロールで `ColumnSpan` プロパティまたは `RowSpan` プロパティを設定することで、<xref:System.Windows.Forms.TableLayoutPanel> コントロールのセルをマージできます。  
  
1.  [方法: TableLayoutPanel コントロール内でコントロールを配置して伸縮する](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))  
  
2.  [方法: TableLayoutPanel コントロールの行と列を拡大する](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))  
  
3.  [方法: TableLayoutPanel コントロールの列と行を編集する](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))  
  
4.  [チュートリアル: TableLayoutPanel を使用した Windows フォーム上のコントロールの配置](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 [方法: ローカリゼーションに対応した Windows フォーム レイアウトをデザインする](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [方法: データ入力用のサイズ変更可能な Windows フォームを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-resizable-windows-form-for-data-entry.md)  
 [TableLayoutPanel コントロールの推奨される手順](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)
