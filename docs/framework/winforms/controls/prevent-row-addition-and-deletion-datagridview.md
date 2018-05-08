---
title: '方法 : Windows フォーム DataGridView コントロールで行が追加および削除されないようにする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], disabling data entry
- data entry [Windows Forms], disabling in grids
- data grids [Windows Forms], disabling data entry
ms.assetid: ef9539ce-539b-404e-84b6-ac282b64b88c
ms.openlocfilehash: abf09652d4cbbf9f112192931c72afa0caaf9f97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control"></a>方法 : Windows フォーム DataGridView コントロールで行が追加および削除されないようにする
場合によっては、ユーザーが <xref:System.Windows.Forms.DataGridView> コントロールに新しいデータ行を入力したり、既存の行を削除したりできないようにする必要があります。 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> プロパティは新しいレコードのための行がコントロールの一番下に存在しているかどうかを示し、<xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> プロパティは行を削除できるかどうかを示します。 次のコード例は、これらのプロパティを使用し、さらに <xref:System.Windows.Forms.DataGridView.ReadOnly%2A> プロパティも設定して、コントロール全体を読み取り専用にします。  
  
 Visual Studio では、このタスクに対するサポートが用意されています。  参照してください[する方法: Windows フォーム DataGridView コントロールを使用して、デザイナーで防ぐ行の追加および削除](http://msdn.microsoft.com/library/k5c88sw3\(v=vs.110\))です。  
  
## <a name="example"></a>例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#090](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#090)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#090](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#090)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
-   <xref:System?displayProperty=nameWithType> アセンブリおよび <xref:System.Windows.Forms?displayProperty=nameWithType> アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ReadOnly%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A?displayProperty=nameWithType>  
 [Windows フォーム DataGridView コントロールでの列、行、およびセルの基本機能](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)
