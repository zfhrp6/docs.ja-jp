---
title: Windows フォームの DataGridView コントロール内のデータの並べ替え
ms.date: 02/13/2018
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
ms.openlocfilehash: 1cbfb4a19e9bb0db5cbb595a91a254a3a8e3f309
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536014"
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a>Windows フォームの DataGridView コントロール内のデータの並べ替え

既定では、ユーザーが内のデータを並べ替えることができます、<xref:System.Windows.Forms.DataGridView>コントロールのテキスト ボックスの列見出しをクリックして (またはテキスト ボックスのセルは、.NET Framework 4.7.2 およびそれ以降のバージョンにフォーカスがあるときは、f3 キーを押して)。 変更することができます、<xref:System.Windows.Forms.DataGridViewColumn.SortMode>これを行う方が良い場合、その他の列の型を並べ替えるにはユーザーを許可する特定の列のプロパティです。 並べ替えることもできますデータ プログラムで、任意の列または複数の列です。

## <a name="in-this-section"></a>このセクションの内容

[Windows フォーム DataGridView コントロール内の列の並べ替えモード](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
コントロール内のデータを並べ替えるためのオプションについて説明します。

[方法: Windows フォーム DataGridView コントロール内の列の並べ替えモードを設定する](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)  
既定では並べ替えできない列で並べ替えを行うユーザーを有効にする方法について説明します。

[方法: Windows フォーム DataGridView コントロールの並べ替え機能をカスタマイズする](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
プログラムでデータを並べ替える方法を使用して並べ替えをカスタマイズする方法について説明、<xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType>イベントまたは実装することによって、<xref:System.Collections.IComparer>インターフェイスです。

## <a name="reference"></a>参照

<xref:System.Windows.Forms.DataGridView>  
<xref:System.Windows.Forms.DataGridView> コントロールのリファレンス ドキュメントを提供します。  

<xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridView.Sort%2A>メソッドです。

<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>プロパティです。

<xref:System.Windows.Forms.DataGridViewColumnSortMode>  
リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridViewColumnSortMode>列挙します。

## <a name="see-also"></a>関連項目

[DataGridView コントロール](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
[Windows フォーム DataGridView コントロールの列型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  