---
title: DataGrid コントロールの既定のキーボード動作とマウス動作
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid [WPF], keyboard behavior
- DataGrid [WPF], mouse behavior
- keyboard behavior [WPF], DataGrid
- mouse behavior [WPF], DataGrid
ms.assetid: 563b8854-ca39-4d97-8235-17eaa0f93c8d
ms.openlocfilehash: 559b84d3e6b5ece6c71f17e6766cac4ec14824cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557421"
---
# <a name="default-keyboard-and-mouse-behavior-in-the-datagrid-control"></a>DataGrid コントロールの既定のキーボード動作とマウス動作
このトピックとユーザーの対話方法について説明します、<xref:System.Windows.Controls.DataGrid>キーボードとマウスを使用して制御します。  
  
 一般的な対話、<xref:System.Windows.Controls.DataGrid>ナビゲーション、選択、および編集が含まれます。 選択の動作の影響を受ける、<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>と<xref:System.Windows.Controls.DataGrid.SelectionUnit%2A>プロパティです。 このトピックで説明されている動作を起こす既定値は<xref:System.Windows.Controls.DataGridSelectionMode.Extended?displayProperty=nameWithType>と<xref:System.Windows.Controls.DataGridSelectionUnit.FullRow?displayProperty=nameWithType>です。 これらの値を変更すると、説明されているとは異なる動作が発生する可能性があります。 セルが編集モードのときは、編集コントロールがの標準キーボード動作をオーバーライド可能性があります、<xref:System.Windows.Controls.DataGrid>です。  
  
## <a name="default-keyboard-behavior"></a>既定のキーボードの動作  
 次の表に、既定のキーボード動作、<xref:System.Windows.Controls.DataGrid>です。  
  
|キーまたはキーの組み合わせ|説明|  
|----------------------------|-----------------|  
|↓|現在のセルの直下のセルにフォーカスを移動します。 最後の行にフォーカスがある場合は、下矢印キーを押して何も行われません。|  
|↑|現在のセルの上に直接セルにフォーカスを移動します。 最初の行にフォーカスがある場合は、上方向キーを押して何も行われません。|  
|←|行の前のセルにフォーカスを移動します。 行の最初のセルにフォーカスがある場合は、左矢印キーを押すと何も行われません。|  
|→|次の行のセルにフォーカスを移動します。 行の最後のセルにフォーカスがある場合は、右矢印キーを押して何も行われません。|  
|ホーム|現在の行の最初のセルにフォーカスを移動します。|  
|End|現在の行の最後のセルにフォーカスを移動します。|  
|PAGE DOWN|行がグループ化されていない場合は、完全に表示されている行の数でコントロールを下をスクロールします。 列を変更することがなく、最後に完全に表示されている行に、フォーカスを移動します。<br /><br /> 行がグループ化されている場合は、最後の行にフォーカスを移動、<xref:System.Windows.Controls.DataGrid>列を変更することがなくです。|  
|PAGE UP|行がグループ化されていない場合、完全に表示されている行の数でコントロールを上方向へスクロールします。 最初の表示されている行の列を変更せずにフォーカスを移動します。<br /><br /> 行がグループ化されている場合は、最初の行にフォーカスを移動、<xref:System.Windows.Controls.DataGrid>列を変更することがなくです。|  
|Tab|現在の行の次のセルにフォーカスを移動します。 行の最後のセルにフォーカスがある場合は、次の行の最初のセルにフォーカスを移動します。 コントロール内の最後のセルにフォーカスがある場合は、親コンテナーのタブ オーダーの次のコントロールにフォーカスを移動します。<br /><br /> 現在のセルが編集モードとし、現在の行からを移動する タブの原因がフォーカスを押すと、行に対して行われた変更がコミット フォーカスを変更する前にいます。 場合、|  
|Shift + Tab|現在の行の前のセルにフォーカスを移動します。 行の最初のセルにフォーカスがある場合は、前の行の最後のセルにフォーカスを移動します。 コントロール内の最初のセルにフォーカスがある場合は、親コンテナーのタブ オーダーの前のコントロールにフォーカスを移動します。<br /><br /> 現在のセルが編集モードとし、現在の行からを移動する タブの原因がフォーカスを押すと、行に対して行われた変更がコミット フォーカスを変更する前にいます。 場合、|  
|Ctrl +↓|現在の列の最後のセルにフォーカスを移動します。|  
|Ctrl + ↑|現在の列の最初のセルにフォーカスを移動します。|  
|Ctrl + →|現在の行の最後のセルにフォーカスを移動します。|  
|Ctrl + ←|現在の行の最初のセルにフォーカスを移動します。|  
|CTRL + HOME|コントロール内の最初のセルにフォーカスを移動します。|  
|CTRL キーを押しながら END キー|コントロール内の最後のセルにフォーカスを移動します。|  
|Ctrl + PageDown|PAGEDOWN と同じです。|  
|Ctrl + PageUp|ページの上と同じです。|  
|F2|場合、<xref:System.Windows.Controls.DataGrid.IsReadOnly%2A?displayProperty=nameWithType>プロパティは`false`と<xref:System.Windows.Controls.DataGridColumn.IsReadOnly%2A?displayProperty=nameWithType>プロパティは`false`現在の列のセルの編集モードに現在のセルを挿入します。|  
|Enter|現在のセルと行に変更をコミットし、現在のセルの直下のセルにフォーカスを移動します。 最後の行にフォーカスがある場合は、フォーカスを移動させることがなく変更をコミットします。|  
|Esc|コントロールが編集モードである場合は、編集をキャンセルし、コントロールに加えられた変更を元に戻します。 場合は、基になるデータ ソースを実装して<xref:System.ComponentModel.IEditableObject>、行全体の編集モードをキャンセル、2 回目の esc キーを押します。|  
|BACKSPACE キー|セルを編集するときは、カーソルより前に、の文字を削除します。|  
|Del|セルの編集時に、カーソルより後の文字を削除します。|  
|Ctrl + Enter|現在のセルにフォーカスを移動せず変更をコミットします。|  
|Ctrl + A|場合<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>に設定されている<xref:System.Windows.Controls.DataGridSelectionMode.Extended>のすべての行を選択、<xref:System.Windows.Controls.DataGrid>です。|  
  
## <a name="selection-keys"></a>選択キー  
 場合、<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>プロパティに設定されている<xref:System.Windows.Controls.DataGridSelectionMode.Extended>ナビゲーションの動作は変わりませんが (CTRL + SHIFT を含む) shift キーを押しながらキーボードで移動すると、複数行の選択が変更されます。 ナビゲーションが開始する前に、コントロールは、アンカー行として、現在の行をマークします。 Shift キーを押しながら移動するときに、選択範囲には、アンカー行と、現在の行の間のすべての行が含まれています。  
  
 次の選択キーは、複数行の選択を変更します。  
  
-   Shift + ↓  
  
-   Shift + ↑  
  
-   Shift + PageDown  
  
-   Shift + PageUp  
  
-   Ctrl + Shift + ↓  
  
-   Ctrl + Shift + ↑  
  
-   CTRL + SHIFT + ホーム  
  
-   CTRL キーを押しながら SHIFT キーを押しながら END  
  
## <a name="default-mouse-behavior"></a>マウスの既定の動作  
 次の表に、マウス デフォルトでは、<xref:System.Windows.Controls.DataGrid>です。  
  
|マウス操作|説明|  
|------------------|-----------------|  
|選択されていない行をクリックします。|クリックされた行は、現在の行、およびクリックされたセルの現在のセルになります。|  
|現在のセルをクリックします。|現在のセルを実行すると、編集モードにします。|  
|列のヘッダー セルにドラッグします。|場合、<xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A?displayProperty=nameWithType>プロパティは`true`と<xref:System.Windows.Controls.DataGridColumn.CanUserReorder%2A?displayProperty=nameWithType>プロパティは`true`現在の列の列に移動できるように、新しい場所に削除できます。|  
|列ヘッダーの区切り線をドラッグします。|場合、<xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType>プロパティは`true`と<xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType>プロパティは`true`現在の列の列のサイズを変更します。|  
|列ヘッダーの区切り線をダブルクリックします。|場合、<xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType>プロパティは`true`と<xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType>プロパティは`true`サイズが自動的に、現在の列の列を使用して、<xref:System.Windows.Controls.DataGridLength.Auto%2A>サイズ変更モード。|  
|列ヘッダー セルをクリックします。|場合、<xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A?displayProperty=nameWithType>プロパティは`true`と<xref:System.Windows.Controls.DataGridColumn.CanUserSort%2A?displayProperty=nameWithType>プロパティは`true`現在の列の列を並べ替えます。<br /><br /> まだ並べ替えられている列のヘッダーをクリックすると、その列の並べ替えの方向は逆です。<br /><br /> SHIFT キーを押しながら複数の列見出しをクリックした順番で複数の列で並べ替えられます。|  
|Ctrl キーを押しながら、行をクリックして|場合<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>に設定されている<xref:System.Windows.Controls.DataGridSelectionMode.Extended>、連続しない複数行の選択状態を変更します。<br /><br /> 行は既に選択されている場合は、行を選択解除します。|  
|SHIFT + 行をクリックしてください|場合<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>に設定されている<xref:System.Windows.Controls.DataGridSelectionMode.Extended>、連続する複数の行の選択を変更します。|  
|行グループ ヘッダーをクリックします。|展開またはグループを折りたたみます。|  
|左上隅にある [すべて選択] ボタンをクリックして、 <xref:System.Windows.Controls.DataGrid>|場合<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>に設定されている<xref:System.Windows.Controls.DataGridSelectionMode.Extended>のすべての行を選択、<xref:System.Windows.Controls.DataGrid>です。|  
  
## <a name="mouse-selection"></a>マウスの選択  
 場合、<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>プロパティに設定されている<xref:System.Windows.Controls.DataGridSelectionMode.Extended>、ctrl キーまたは shift キーを押しながら、行をクリックすると、複数の行の選択が変更されます。  
  
 CTRL キーを押しながら、行をクリックすると、行は、その他のすべての行が現在の選択状態を保持の選択状態を変更します。 連続していない行を選択します。  
  
 Shift キーを押しながら、行をクリックすると、選択範囲には、現在の行と、クリックする前に、現在の行の位置にあるアンカー行の間のすべての行が含まれています。 Shift キーを押しながらそれ以降のクリックでは、現在の行がアンカー行ではなくを変更します。 隣接する行の範囲 を選択しないでください。  
  
 隣接する行の連続していない範囲を選択するには、CTRL + SHIFT を組み合わせて指定できます。 これを行うには、shift キーを使用して、最初の範囲を選択 + 前述のようにクリックします。 行の最初の範囲を選択した後、ctrl キーを押し + をクリックして [次へ] の範囲内で最初の行を選択、CTRL + SHIFT を押しながら次の範囲の最後の行をクリックできます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.DataGrid>  
 <xref:System.Windows.Controls.DataGrid.SelectionMode%2A>
