---
title: 既定のキーボードとマウスの Windows フォームの DataGridView コントロールでの処理
ms.date: 02/13/2018
helpviewer_keywords:
- data grids [Windows Forms], mouse handling
- DataGridView control [Windows Forms], navigation keys
- keyboards [Windows Forms], default handling in DataGridView control
- DataGridView control [Windows Forms], keyboard handling
- mouse [Windows Forms], default handling in DataGridView control
- DataGridView control [Windows Forms], mouse handling
- navigation keys [Windows Forms], DataGridView control
ms.assetid: 4519b928-bfc8-4e8b-bb9c-b1e76a0ca552
ms.openlocfilehash: b0ed468fe7d38fbeda90d5347338bce14059b730
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529569"
---
# <a name="default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control"></a>既定のキーボードとマウスの Windows フォームの DataGridView コントロールでの処理

次の表とユーザーの対話方法について説明する、<xref:System.Windows.Forms.DataGridView>キーボードとマウスを制御します。  
  
> [!NOTE]
>  キーボードの動作をカスタマイズすることがイベントを処理する標準のキーボードなど<xref:System.Windows.Forms.Control.KeyDown>です。 編集モードで、ただし、ホストされる編集コントロールが受信キーボード入力やキーボード イベントの発生、<xref:System.Windows.Forms.DataGridView>コントロール。 編集コントロールのイベントを処理するには、編集コントロールに、ハンドラーをアタッチ、<xref:System.Windows.Forms.DataGridView.EditingControlShowing>イベント ハンドラー。 キーボードの動作をカスタマイズする代わりに、<xref:System.Windows.Forms.DataGridView>サブクラスをオーバーライドすることで、<xref:System.Windows.Forms.DataGridView.ProcessDialogKey%2A>と<xref:System.Windows.Forms.DataGridView.ProcessDataGridViewKey%2A>メソッドです。  
  
## <a name="default-keyboard-handling"></a>既定のキーボード処理  
  
### <a name="basic-navigation-and-entry-keys"></a>基本的なナビゲーション キーとエントリ キー  
  
|キーまたはキーの組み合わせ|説明|  
|----------------------------|-----------------|  
|↓|現在のセルの直下のセルにフォーカスを移動します。 最後の行にフォーカスがある場合は、何も行われません。|  
|←|行の前のセルにフォーカスを移動します。 行の最初のセルにフォーカスがある場合は、何も行われません。|  
|→|次の行のセルにフォーカスを移動します。 行の最後のセルにフォーカスがある場合は、何も行われません。|  
|↑|現在のセルの上に直接セルにフォーカスを移動します。 最初の行にフォーカスがある場合は、何も行われません。|  
|ホーム|現在の行の最初のセルにフォーカスを移動します。|  
|End|現在の行の最後のセルにフォーカスを移動します。|  
|PAGE DOWN|コントロールを下を完全に表示されている行の数でスクロールします。 列を変更することがなく、最後に完全に表示されている行に、フォーカスを移動します。|  
|PAGE UP|コントロールを完全に表示されている行の数、スクロールします。 最初の表示されている行の列を変更せずにフォーカスを移動します。|  
|Tab|場合、<xref:System.Windows.Forms.DataGridView.StandardTab%2A>プロパティの値が`false`、現在の行の次のセルにフォーカスを移動します。 行の最後のセルにフォーカスがある場合は、次の行の最初のセルにフォーカスを移動します。 コントロール内の最後のセルにフォーカスがある場合は、親コンテナーのタブ オーダーの次のコントロールにフォーカスを移動します。<br /><br /> 場合、<xref:System.Windows.Forms.DataGridView.StandardTab%2A>プロパティの値が`true`、親コンテナーのタブ オーダーの次のコントロールにフォーカスを移動します。|  
|Shift + Tab|場合、<xref:System.Windows.Forms.DataGridView.StandardTab%2A>プロパティの値が`false`、現在の行の前のセルにフォーカスを移動します。 行の最初のセルにフォーカスがある場合は、前の行の最後のセルにフォーカスを移動します。 コントロール内の最初のセルにフォーカスがある場合は、親コンテナーのタブ オーダーの前のコントロールにフォーカスを移動します。<br /><br /> 場合、<xref:System.Windows.Forms.DataGridView.StandardTab%2A>プロパティの値が`true`、親コンテナーのタブ オーダー内の前のコントロールにフォーカスを移動します。|  
|Ctrl + Tab|場合、<xref:System.Windows.Forms.DataGridView.StandardTab%2A>プロパティの値が`false`、親コンテナーのタブ オーダーの次のコントロールにフォーカスを移動します。<br /><br /> 場合、<xref:System.Windows.Forms.DataGridView.StandardTab%2A>プロパティの値が`true`、現在の行の次のセルにフォーカスを移動します。 行の最後のセルにフォーカスがある場合は、次の行の最初のセルにフォーカスを移動します。 コントロール内の最後のセルにフォーカスがある場合は、親コンテナーのタブ オーダーの次のコントロールにフォーカスを移動します。|  
|Ctrl + Shift + Tab|場合、<xref:System.Windows.Forms.DataGridView.StandardTab%2A>プロパティの値が`false`、親コンテナーのタブ オーダー内の前のコントロールにフォーカスを移動します。<br /><br /> 場合、<xref:System.Windows.Forms.DataGridView.StandardTab%2A>プロパティの値が`true`、現在の行の前のセルにフォーカスを移動します。 行の最初のセルにフォーカスがある場合は、前の行の最後のセルにフォーカスを移動します。 コントロール内の最初のセルにフォーカスがある場合は、親コンテナーのタブ オーダーの前のコントロールにフォーカスを移動します。|  
|CTRL キーを押しながら方向|矢印の方向で最も遠いセルにフォーカスを移動します。|  
|CTRL + HOME|コントロール内の最初のセルにフォーカスを移動します。|  
|CTRL キーを押しながら END キー|コントロール内の最後のセルにフォーカスを移動します。|  
|CTRL + ページ上/下|PAGE down キーまたはページの上と同じです。|  
|F2|場合、セルの編集モードに現在のセルを挿入、<xref:System.Windows.Forms.DataGridView.EditMode%2A>プロパティの値が<xref:System.Windows.Forms.DataGridViewEditMode.EditOnF2>または<xref:System.Windows.Forms.DataGridViewEditMode.EditOnKeystrokeOrF2>です。|
|F3|場合は、現在の列を並べ替え、<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>プロパティの値が<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>です。 現在の列ヘッダーをクリックした場合と同じです。 .NET Framework 4.7.2 以降で使用可能です。 この機能を有効にするには、は、アプリケーションは .NET Framework 4.7.2 またはそれ以降のバージョンを対象とまたは AppContext スイッチを使用してユーザー補助機能強化を明示的に選択する必要があります。|  
|F4|現在のセルがある場合、<xref:System.Windows.Forms.DataGridViewComboBoxCell>セルが編集モードに、ドロップダウン リストが表示されます。|  
|ALT キーを押しながら上/下方向|現在のセルがある場合、<xref:System.Windows.Forms.DataGridViewComboBoxCell>セルが編集モードに、ドロップダウン リストが表示されます。|  
|Space|現在のセルがある場合、 <xref:System.Windows.Forms.DataGridViewButtonCell>、 <xref:System.Windows.Forms.DataGridViewLinkCell>、または<xref:System.Windows.Forms.DataGridViewCheckBoxCell>を生成、<xref:System.Windows.Forms.DataGridView.CellClick>と<xref:System.Windows.Forms.DataGridView.CellContentClick>イベント。 現在のセルがある場合、 <xref:System.Windows.Forms.DataGridViewButtonCell>、また、ボタンを押します。 現在のセルがある場合、<xref:System.Windows.Forms.DataGridViewCheckBoxCell>もチェックの状態を変更します。|  
|Enter|現在のセルと行に変更をコミットし、現在のセルの直下のセルにフォーカスを移動します。 最後の行にフォーカスがある場合は、フォーカスを移動させることがなく変更をコミットします。|  
|Esc|コントロールが編集モードである場合は、編集をキャンセルします。 コントロールが編集モードにない場合は、コントロールが編集をサポートするデータ ソースにバインドされている場合、現在の行に行われた変更を元に戻します。 または行レベルのコミットのスコープを持つ仮想モードが実装されています。|  
|BACKSPACE キー|セルを編集するときは、挿入ポイントの直前にある文字を削除します。|  
|Del|セルの編集時に、挿入位置より後に文字を削除します。|  
|Ctrl + Enter|現在のセルにフォーカスを移動せず変更をコミットします。 コントロールが編集または仮想モードをサポートするデータ ソースにバインドされている場合は、現在の行への変更が実装されてコミット行レベルのコミットのスコープ。|  
|Ctrl + 0|入力した、<xref:System.DBNull.Value?displayProperty=nameWithType>セルを編集する場合は、現在のセルに値します。 既定では、表示の値を<xref:System.DBNull>セル値がの値、<xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A>のプロパティ、<xref:System.Windows.Forms.DataGridViewCellStyle>現在のセルに対して有効です。|  
  
### <a name="selection-keys"></a>選択キー

 場合、<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>プロパティに設定されている`false`と<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>プロパティに設定されている<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>、新しいセルに、選択範囲を変更するナビゲーション キーを使用して、現在のセルを変更します。 Shift キーを押し、CTRL、ALT の各キーは、この動作は影響しません。  
  
 場合、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>に設定されている<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>または<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>、同じ動作が発生したが、次の項目を追加します。  
  
|キーまたはキーの組み合わせ|説明|  
|----------------------------|-----------------|  
|SHIFT キーを押しながら SPACE キー|すべての行または列 (行または列ヘッダーをクリックした場合と同じ) を選択します。|  
|ナビゲーション キー (方向キー、ページの上下 HOME、END)|完全行または列が選択されている場合、新しい行または列に現在のセルを変更するに移動、新しい行または列 (選択モード) に応じて。|  
  
 場合<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>に設定されている`false`と<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>に設定されている<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>または<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>キーボードを使用して新しい行または列に現在のセルを変更する、新しい行または列に移動します。 Shift キーを押し、CTRL、ALT の各キーは、この動作は影響しません。  
  
 場合<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>に設定されている`true`ナビゲーションの動作は変わりませんが (CTRL + SHIFT を含む) shift キーを押しながらキーボードで移動すると、複数のセルの選択が変更されます。 ナビゲーションが開始する前に、コントロールは、現在のセルをアンカー セルとしてマークします。 Shift キーを押しながら移動するときに、選択範囲には、アンカー セルと現在のセル間のすべてのセルが含まれています。 既に選択されている、選択されていない場合は、キーボードのナビゲーションは一時的にアンカー セルと現在のセルの場合、コントロールの他のセルが選択された保持されます。  
  
 場合<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>に設定されている`true`と<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>に設定されている<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>または<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>、アンカー セルと現在のセルの動作は同じですが、完全行や列だけになる選択または選択解除しました。  
  
## <a name="default-mouse-handling"></a>既定のマウス処理
  
### <a name="basic-mouse-handling"></a>基本的なマウス処理
  
> [!NOTE]
>  マウスの左ボタンを含むセルをクリックすると、常に現在のセルを変更します。 マウスの右ボタンを含むセルをクリックすると 1 つが利用可能なときに、ショートカット メニューが開きます。  
  
|マウス操作|説明|  
|------------------|-----------------|  
|マウスの左ボタンを押す|クリックされたセルは、現在のセル、させ、<xref:System.Windows.Forms.DataGridView.CellMouseDown?displayProperty=nameWithType>イベント。|  
|マウスの左ボタン|<xref:System.Windows.Forms.DataGridView.CellMouseUp?displayProperty=nameWithType> イベントを発生させます。|  
|マウスの左ボタンをクリックします。|発生させる、<xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType>と<xref:System.Windows.Forms.DataGridView.CellMouseClick?displayProperty=nameWithType>イベント|  
|マウスの左ボタンを押す、および列ヘッダー セルにドラッグ|場合、<xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>プロパティは`true`の新しい場所に削除できるように、列を移動します。|  
  
### <a name="mouse-selection"></a>マウスの選択

 選択の動作は、マウスの中央ボタンやマウス ホイールを関連付けではありません。  
  
 場合、<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>プロパティに設定されている`false`と<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>プロパティに設定されている<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>、次の動作が発生します。  
  
|マウス操作|説明|  
|------------------|-----------------|  
|マウスの左ボタンをクリックします。|ユーザーがセルをクリックした場合は、現在のセルのみを選択します。 選択動作はありません、ユーザーが行または列ヘッダーをクリックするとします。|  
|マウスの右ボタンをクリックします。|1 つが利用可能な場合は、ショートカット メニューを表示します。|  
  
 同じ動作が発生したときに、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>に設定されている<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>または<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>によって選択モード行または列ヘッダーをクリックするとは、行全体または列を選択および行または列の最初のセルに、現在のセルを設定することを除き、します。  
  
 場合<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>に設定されている<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>または<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>、行または列の任意のセルをクリックすると行全体または列を選択します。  
  
 場合<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>に設定されている`true`、複数のセル選択範囲の変更は ctrl キーまたは shift キーを押しながらセルをクリックします。  
  
 CTRL キーを押しながら、セルをクリックすると、セルは、現在選択状態を保持する他のすべてのセルの選択状態を変更します。  
  
 Shift キーを押しながら、セルまたは一連のセルをクリックすると、選択範囲には、現在のセルと最初のクリックする前に現在のセルの位置のアンカー セル間のすべてのセルが含まれています。 をクリックして、複数のセル、ポインターをドラッグすると、ドラッグ操作の先頭でクリックされたセルがアンカー セルにします。 Shift キーを押しながらそれ以降のクリックでは、現在のセルがないのアンカー セルを変更します。 既に選択されている、選択されていない場合は、マウスのナビゲーションは一時的にアンカー セルと現在のセルの場合、コントロールの他のセルが選択された保持されます。  
  
 場合<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>に設定されている`true`と<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>に設定されている<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>または<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>場合は、このような完全行または列の既存の選択範囲を変更、shift キーを押しながら (に応じて選択モード) の行または列ヘッダーをクリックすると、選択範囲が存在します。 それ以外の場合、選択を解除を行全体または列の新しい選択を開始します。 CTRL キーを押しながら、行または列ヘッダーをクリックすると、ただしは追加またはそれ以外の場合、現在の選択を変更することがなく、現在の選択項目からクリックされた行または列を削除します。  
  
 場合<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>に設定されている`true`と<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>に設定されている<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>または<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>そののみ完全行を除くと同様の動作、SHIFT または CTRL を押しながら、セルをクリックすると、および列には影響します。  
  
## <a name="see-also"></a>関連項目

<xref:System.Windows.Forms.DataGridView>  
 [DataGridView コントロール](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
