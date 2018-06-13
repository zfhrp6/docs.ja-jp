---
title: '方法 : Windows フォーム DataGridView コントロールのセルにイメージを表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], displaying images
- data grids [Windows Forms], displaying in grids
- DataGridView control [Windows Forms], displaying images
- data grids [Windows Forms], displaying images in cells
ms.assetid: 53b13d31-1b56-476d-9ab4-18bfac138a22
ms.openlocfilehash: 62a29b9ade4953a1775c2a71b62e4881065f51a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531194"
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a>方法 : Windows フォーム DataGridView コントロールのセルにイメージを表示する
画像やグラフィックはデータの行で表示できる値のいずれかです。 多くの場合、これらのグラフィックスは、従業員の写真や会社のロゴの形をとります。  
  
 画像を組み込むことは、単純な内でデータを表示するときに、<xref:System.Windows.Forms.DataGridView>コントロール。 <xref:System.Windows.Forms.DataGridView>コントロールがネイティブでサポートされている任意のイメージ形式を処理、 <xref:System.Drawing.Image> OLE と同様に、クラス図の一部のデータベースで使用される形式です。  
  
 場合、<xref:System.Windows.Forms.DataGridView>コントロールのデータ ソースのイメージの列がある、によって自動的に表示されます、<xref:System.Windows.Forms.DataGridView>コントロール。  
  
 次のコード例では、埋め込みリソースからアイコンを抽出し、image 列の各セルに表示用のビットマップに変換する方法を示します。 対応するイメージとテキストのセル値を置換する別の例では、次を参照してください。[する方法: Windows フォーム DataGridView コントロールでデータの書式をカスタマイズする](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)です。  
  
## <a name="example"></a>例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
-   という名前に埋め込まれたアイコン リソース`tree.ico`です。  
  
-   <xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType>、および <xref:System.Drawing?displayProperty=nameWithType> の各アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 [Windows フォーム DataGridView コントロールでの列、行、およびセルの基本機能](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [方法: Windows フォーム DataGridView コントロールのデータの書式設定をカスタマイズする](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
