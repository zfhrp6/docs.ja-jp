---
title: '方法 : Windows フォーム DataGridView コントロール内の列の並べ替えモードを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
ms.openlocfilehash: 08d90bb45006af798b629f58821cbf50ee9ef089
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535732"
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a>方法 : Windows フォーム DataGridView コントロール内の列の並べ替えモードを設定する
<xref:System.Windows.Forms.DataGridView>他の列の型が自動的に並べ替えられていないときに、既定では、自動並べ替えコントロール、テキスト ボックスの列を使用します。 これらの既定値をオーバーライドする場合があります。 たとえば、テキスト、数値、または列挙型のセルの値の代わりにイメージを表示することができます。 イメージを並べ替えることはできません、中に、それが表す基になる値を並べ替えることができます。  
  
 <xref:System.Windows.Forms.DataGridView>コントロール、<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>列のプロパティの値の並べ替えの動作を決定します。  
  
 次の手順に示します、`Priority`から列[する方法: Windows フォーム DataGridView コントロールでデータの書式をカスタマイズする](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)です。 この列は image 列であり、既定では並べ替えられません。 自動的に並べ替えることができますので、ただし、文字列の場合は、実際のセル値が含まれます。  
  
### <a name="to-set-the-sort-mode-for-a-column"></a>列の並べ替えモードを設定するには  
  
-   <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> プロパティを設定します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   `Priority` という名前の列を含む `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
-   <xref:System?displayProperty=nameWithType> アセンブリおよび <xref:System.Windows.Forms?displayProperty=nameWithType> アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
 [Windows フォームの DataGridView コントロールでのデータの並べ替え](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [Windows フォーム DataGridView コントロール内の列の並べ替えモード](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [方法: Windows フォーム DataGridView コントロールの並べ替え機能をカスタマイズする](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
