---
title: Windows フォーム DataGridView コントロールの選択モード
ms.date: 03/30/2017
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
ms.assetid: a3ebfd3d-0525-479d-9d96-d9e017289b36
ms.openlocfilehash: 43f3648a9c7d64fb4fb900c7df3f01bc18d729b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539573"
---
# <a name="selection-modes-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールの選択モード
アプリケーション内のユーザーの選択に基づいて操作を実行することがあります、<xref:System.Windows.Forms.DataGridView>コントロール。 によって、アクション可能な選択の種類を制限します。 たとえば、アプリケーションは、現在選択されているレコードに対してレポートを印刷できます。 ここでは、構成する場合は、<xref:System.Windows.Forms.DataGridView>コントロールに常に、行内でクリックしてできるようには、全体の行を選択し、一度に 1 つだけその行を選択できるようにします。  
  
 オプションの設定で許可されているを指定することができます、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>プロパティに、次のいずれか<xref:System.Windows.Forms.DataGridViewSelectionMode>列挙値。  
  
|DataGridViewSelectionMode 値|説明|  
|-------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>|セルをクリックすると、それを選択します。 選択範囲の行および列ヘッダーを使用できません。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>|セルをクリックすると、それを選択します。 列ヘッダーをクリックすると、列全体を選択します。 列ヘッダーは、並べ替えに使用できません。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>|セルまたは列ヘッダーをクリックすると、列全体を選択します。 列ヘッダーは、並べ替えに使用できません。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>|セルまたは行ヘッダーをクリックすると、行全体を選択します。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>|既定の選択モード。 セルをクリックすると、それを選択します。 行ヘッダーをクリックすると、全体の行が選択されます。|  
  
> [!NOTE]
>  実行時に自動的に選択モードを変更すると、現在の選択が解除されます。  
  
 既定では、ユーザーを選択できます複数の行、列、またはセルで、マウスをドラッグするを拡張したり、選択範囲の変更を選択すると、コントロール内のすべてのセルを選択する左上のヘッダー セルをクリックして、ctrl キーまたは shift キーを押すとします。 この動作を防ぐためには、設定、<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>プロパティを`false`です。  
  
 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>と<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>モードを選択し、DEL キーを押して行を削除するユーザーを許可します。 現在のセルが編集モードでない場合にのみ、ユーザーが行を削除できる、<xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A>プロパティに設定されている`true`、基になるデータ ソースは、ユーザーによる行の削除をサポートしているとします。 これらの設定には、プログラムによる行の削除ができないようにいないことに注意してください。  
  
## <a name="programmatic-selection"></a>プログラムの選択  
 現在の選択モードでは、プログラムによる選択とユーザーの選択の動作を制限します。 現在の選択範囲を設定してプログラムで変更できます、`Selected`任意のセル、行、または表示されている列のプロパティ、<xref:System.Windows.Forms.DataGridView>コントロール。 使用してコントロールのすべてのセルを選択することも、<xref:System.Windows.Forms.DataGridView.SelectAll%2A>選択モードによって、メソッドです。 選択を解除するを使用して、<xref:System.Windows.Forms.DataGridView.ClearSelection%2A>メソッドです。  
  
 場合、<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>プロパティに設定されている`true`、追加することができます<xref:System.Windows.Forms.DataGridView>要素または変更することで、選択項目から削除する、`Selected`要素のプロパティです。 それ以外の場合、設定、`Selected`プロパティを`true`の 1 つの要素では、選択範囲から、その他の要素を自動的に削除します。  
  
 値を変更することに注意してください、<xref:System.Windows.Forms.DataGridView.CurrentCell%2A>プロパティは現在の選択を変更しません。  
  
 現在選択されているセル、行、または列から列のコレクションを取得することができます、 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>、 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>、および<xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>のプロパティ、<xref:System.Windows.Forms.DataGridView>コントロール。 コントロールのすべてのセルが選択されている場合は、これらのプロパティにアクセスする効率的です。 ここでは、パフォーマンスの低下を避けるため、使用、<xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>メソッド最初。 さらに、選択したセルの数を決定するこれらのコレクションにアクセスする、行、または列できます効率的です。 代わりに、使用する必要があります、 <xref:System.Windows.Forms.DataGridView.GetCellCount%2A>、 <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A>、または<xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A>に渡して、メソッド、<xref:System.Windows.Forms.DataGridViewElementStates.Selected>値。  
  
> [!TIP]
>  選択したセルのプログラムによる使用方法を示すコード例は含まれて、<xref:System.Windows.Forms.DataGridView>クラスの概要です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>  
 <xref:System.Windows.Forms.DataGridViewSelectionMode>  
 [Windows フォーム DataGridView コントロールでの選択およびクリップボードの使用](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 [方法: Windows フォーム DataGridView コントロールの選択モードを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)
