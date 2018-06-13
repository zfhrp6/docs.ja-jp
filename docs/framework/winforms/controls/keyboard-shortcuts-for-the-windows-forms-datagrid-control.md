---
title: Windows フォームの DataGrid コントロール内の移動に使用できるキーボード ショートカット
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard shortcuts [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], navigation keys
ms.assetid: a01780f9-20d5-4f5f-808f-c790c9a007a5
ms.openlocfilehash: c05ddd68beeffe70e048a439929fb31454812612
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542230"
---
# <a name="keyboard-shortcuts-for-the-windows-forms-datagrid-control"></a>Windows フォームの DataGrid コントロール内の移動に使用できるキーボード ショートカット
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。 詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 次の表に、Windows フォーム内のナビゲーションに使用できるキーボード ショートカット<xref:System.Windows.Forms.DataGrid>コントロール。  
  
|アクション|ショートカット|  
|------------|--------------|  
|セルの入力を完了し、次のセルに下に移動します。<br /><br /> 子テーブルのリンクにフォーカスがある場合は、そのテーブルに移動します。|Enter|  
|セルの編集モードの場合は、セルの編集をキャンセルします。<br /><br /> マーキーの選択の場合は、行の編集をキャンセルします。|Esc|  
|セルを編集するときは、挿入ポイントの直前にある文字を削除します。|BACKSPACE キー|  
|セルの編集時に、挿入位置より後に文字を削除します。|Del|  
|現在の行の最初のセルに移動します。|ホーム|  
|最後の現在の行のセルに移動します。|End|  
|現在のセル内の文字を強調表示し、行の末尾にカーソルを置きます。 セルをダブルクリックした場合と同じ動作です。|F2|  
|セルにフォーカスがある場合は、次の行セルに移動します。<br /><br /> 行の最後のセルにフォーカスがある場合は、行の最初の子テーブルのリンクに移動し、それを展開します。<br /><br /> 子のリンクにフォーカスがある場合は、次の子リンクに移動します。<br /><br /> 最後の子リンクにフォーカスがある場合は、次の行の最初のセルに移動します。|Tab|  
|セルにフォーカスがある場合は、行の前のセルに移動します。<br /><br /> 行の最初のセルにフォーカスがある場合は、前の行の最後の展開された子テーブルのリンクに移動または最後の前の行のセルに移動します。<br /><br /> 子のリンクにフォーカスがある場合は、以前の子へのリンクに移動します。<br /><br /> 最初の子リンクにフォーカスがある場合、最後のセルに移動前の行。|Shift + Tab|  
|タブ オーダーの次のコントロールに移動します。|Ctrl + Tab|  
|タブ オーダー内の前のコントロールに移動します。|Ctrl + Shift + Tab|  
|子テーブルの場合、親テーブルに移動します。 [戻る] ボタンをクリックした場合と同じ動作です。|Alt + ←|  
|子テーブルのリンクを展開します。 Alt キーを押しながら下方向は、選択されているだけでなく、すべてのリンクを展開します。|Alt キーを押しながら下方向キーまたは CTRL + プラス記号|  
|子テーブルのリンクを折りたたみます。 ALT + 上向き矢印は、選択されているだけでなく、すべてのリンクを折りたたみます。|Alt キーを押しながら上方向キーまたは CTRL + マイナス記号|  
|矢印の方向でよりもはるかに空白以外のセルに移動します。|CTRL キーを押しながら方向|  
|(子テーブルのリンクを除く) の矢印の方向に 1 行ずつ選択を拡張します。|SHIFT キーを押しながら上/下方向|  
|(子テーブルのリンクを除く) の矢印の方向でよりもはるかに空白行まで選択範囲を拡張します。|CTRL + SHIFT + 上向きまたは下向き矢印|  
|左上隅のセルに移動します。|CTRL + HOME|  
|右下隅のセルに移動します。|CTRL キーを押しながら END キー|  
|選択範囲を先頭の行を拡張します。|CTRL + SHIFT + ホーム|  
|一番下の行を選択範囲を拡大します。|CTRL キーを押しながら SHIFT キーを押しながら END|  
|(子テーブルのリンクを除く)、現在の行を選択します。|SHIFT キーを押しながら SPACE キー|  
|グリッド全体 (子テーブルのリンクを除く) を選択します。|Ctrl + A|  
|子テーブルにある場合、親の行を表示します。|Ctrl + PageDown|  
|子テーブルにある場合、親の行を非表示にします。|Ctrl + PageUp|  
|(子テーブルのリンクを除く) 1 画面下に、選択範囲を拡張します。|Shift + PageDown|  
|(子テーブルのリンクを除く) 1 つの画面上に、選択範囲を拡張します。|Shift + PageUp|  
|呼び出す、<xref:System.Windows.Forms.DataGrid.EndEdit%2A>現在の行のメソッドです。|Ctrl + Enter|  
|入力、<xref:System.DBNull.Value?displayProperty=nameWithType>編集モードでのセルに値。|Ctrl + 0|  
  
## <a name="see-also"></a>関連項目  
 [DataGrid コントロールの概要](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [DataGrid コントロール](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
