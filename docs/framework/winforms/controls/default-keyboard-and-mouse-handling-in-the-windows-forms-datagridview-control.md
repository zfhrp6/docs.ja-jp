---
title: "Windows フォーム DataGridView コントロールの既定のキーボード処理とマウス処理 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "データ グリッド, マウス処理"
  - "DataGridView コントロール [Windows フォーム], キーボード処理"
  - "DataGridView コントロール [Windows フォーム], マウス処理"
  - "DataGridView コントロール [Windows フォーム], 移動キー"
  - "キーボード, 既定の処理 (DataGridView コントロール内の)"
  - "マウス, 既定の処理 (DataGridView コントロール内の)"
  - "移動キー, DataGridView コントロール"
ms.assetid: 4519b928-bfc8-4e8b-bb9c-b1e76a0ca552
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Windows フォーム DataGridView コントロールの既定のキーボード処理とマウス処理
キーボードとマウスを介して、ユーザーが <xref:System.Windows.Forms.DataGridView> コントロールとやり取りする方法を次の表に示します。  
  
> [!NOTE]
>  キーボードの動作をカスタマイズするには、<xref:System.Windows.Forms.Control.KeyDown> などの標準キーボード イベントを処理します。  ただし、編集モードでは、ホストされる編集コントロールがキーボード入力を受け取るため、<xref:System.Windows.Forms.DataGridView> コントロールに対するキーボード イベントは発生しません。  編集コントロールのイベントを処理するには、<xref:System.Windows.Forms.DataGridView.EditingControlShowing> イベント ハンドラーで編集コントロールにハンドラーをアタッチします。  または、<xref:System.Windows.Forms.DataGridView> サブクラスで <xref:System.Windows.Forms.DataGridView.ProcessDialogKey%2A> メソッドと <xref:System.Windows.Forms.DataGridView.ProcessDataGridViewKey%2A> メソッドをオーバーライドして、キーボードの動作をカスタマイズすることもできます。  
  
## 既定のキーボード処理  
  
### 基本的な移動キーと入力キー  
  
|キーまたはキーの組み合わせ|Description|  
|-------------------|-----------------|  
|↓|現在のセルの 1 つ下のセルにフォーカスを移動します。  フォーカスが最後の行にある場合は、何も行いません。|  
|←|同じ行の 1 つ前のセルにフォーカスを移動します。  フォーカスが行の最初のセルにある場合は、何も行いません。|  
|→|同じ行の次のセルにフォーカスを移動します。  フォーカスが行の最後のセルにある場合は、何も行いません。|  
|↑|現在のセルの 1 つ上のセルにフォーカスを移動します。  フォーカスが最初の行にある場合は、何も行いません。|  
|Home|現在の行の最初のセルにフォーカスを移動します。|  
|End|現在の行の最後のセルにフォーカスを移動します。|  
|PageDown|完全に表示されている行数分、コントロールを下にスクロールします。  完全に表示されている最後の行にフォーカスを移動します。列は変更しません。|  
|PageUp|完全に表示されている行数分、コントロールを上にスクロールします。  現在表示されている最初の行にフォーカスを移動します。列は変更しません。|  
|Tab|<xref:System.Windows.Forms.DataGridView.StandardTab%2A> プロパティ値が `false` の場合は、現在の行の次のセルにフォーカスを移動します。  行の最後のセルにフォーカスがあるときは、次の行の最初のセルにフォーカスを移動します。  コントロールの最後のセルにフォーカスがあるときは、親コンテナーのタブ オーダーで次のコントロールにフォーカスを移動します。<br /><br /> <xref:System.Windows.Forms.DataGridView.StandardTab%2A> プロパティ値が `true` の場合は、親コンテナーのタブ オーダーで次のコントロールにフォーカスを移動します。|  
|Shift \+ Tab|<xref:System.Windows.Forms.DataGridView.StandardTab%2A> プロパティ値が `false` の場合は、現在の行の 1 つ前のセルにフォーカスを移動します。  行の最初のセルにフォーカスがあるときは、1 つ前の行の最後のセルにフォーカスを移動します。  コントロールの最初のセルにフォーカスがある場合は、親コンテナーのタブ オーダーで 1 つ前のコントロールにフォーカスを移動します。<br /><br /> <xref:System.Windows.Forms.DataGridView.StandardTab%2A> プロパティ値が `true` の場合は、親コンテナーのタブ オーダーで 1 つ前のコントロールにフォーカスを移動します。|  
|Ctrl \+ Tab|<xref:System.Windows.Forms.DataGridView.StandardTab%2A> プロパティ値が `false` の場合は、親コンテナーのタブ オーダーで次のコントロールにフォーカスを移動します。<br /><br /> <xref:System.Windows.Forms.DataGridView.StandardTab%2A> プロパティ値が `true` の場合は、現在の行の次のセルにフォーカスを移動します。  行の最後のセルにフォーカスがあるときは、次の行の最初のセルにフォーカスを移動します。  コントロールの最後のセルにフォーカスがあるときは、親コンテナーのタブ オーダーで次のコントロールにフォーカスを移動します。|  
|Ctrl \+ Shift \+ Tab|<xref:System.Windows.Forms.DataGridView.StandardTab%2A> プロパティ値が `false` の場合は、親コンテナーのタブ オーダーで 1 つ前のコントロールにフォーカスを移動します。<br /><br /> <xref:System.Windows.Forms.DataGridView.StandardTab%2A> プロパティ値が `true` の場合は、現在の行の 1 つ前のセルにフォーカスを移動します。  行の最初のセルにフォーカスがあるときは、1 つ前の行の最後のセルにフォーカスを移動します。  コントロールの最初のセルにフォーカスがある場合は、親コンテナーのタブ オーダーで 1 つ前のコントロールにフォーカスを移動します。|  
|Ctrl \+ 方向キー|矢印の方向にある最も遠いセルにフォーカスを移動します。|  
|Ctrl \+ Home|コントロール内の最初のセルにフォーカスを移動します。|  
|Ctrl \+ End|コントロール内の最後のセルにフォーカスを移動します。|  
|Ctrl \+ PageDown または Ctrl \+ PageUp|PageDown または PageUp と同じです。|  
|F2|<xref:System.Windows.Forms.DataGridView.EditMode%2A> プロパティ値が <xref:System.Windows.Forms.DataGridViewEditMode> または <xref:System.Windows.Forms.DataGridViewEditMode> の場合に、現在のセルを編集モードに設定します。|  
|F4|現在のセルが <xref:System.Windows.Forms.DataGridViewComboBoxCell> の場合に、現在のセルを編集モードにしてドロップダウン リストを表示します。|  
|Alt \+ ↑ または Alt \+ ↓|現在のセルが <xref:System.Windows.Forms.DataGridViewComboBoxCell> の場合に、現在のセルを編集モードにしてドロップダウン リストを表示します。|  
|Space|現在のセルが <xref:System.Windows.Forms.DataGridViewButtonCell>、<xref:System.Windows.Forms.DataGridViewLinkCell>、または <xref:System.Windows.Forms.DataGridViewCheckBoxCell> の場合に、<xref:System.Windows.Forms.DataGridView.CellClick> イベントと <xref:System.Windows.Forms.DataGridView.CellContentClick> イベントを発生させます。  現在のセルが <xref:System.Windows.Forms.DataGridViewButtonCell> の場合は、ボタンも押します。  現在のセルが <xref:System.Windows.Forms.DataGridViewCheckBoxCell> の場合は、\(チェック ボックスの\) チェックの状態も変更します。|  
|Enter|現在のセルおよび行への変更をコミットし、現在のセルの 1 つ下のセルにフォーカスを移動します。  フォーカスが最後の行にある場合は、変更をコミットし、フォーカスは移動しません。|  
|Esc|コントロールが編集モードの場合は、編集をキャンセルします。  コントロールが編集モードではない場合、コントロールが編集をサポートするデータ ソースにバインドされているか、または行レベルのコミット スコープを持つ仮想モードが実装されていれば、現在の行に加えられた変更をすべて元に戻します。|  
|BackSpace|セルを編集するときに、カーソル位置の前にある文字を削除します。|  
|Del|セルを編集するときに、カーソル位置の後にある文字を削除します。|  
|Ctrl \+ Enter|現在のセルに対して行われた変更をコミットします。フォーカスは移動しません。  また、コントロールが編集をサポートするデータ ソースにバインドされている場合、または行レベルのコミット スコープを持つ仮想モードが実装されている場合、現在の行に対する変更をすべてコミットします。|  
|Ctrl \+ 0|セルを編集できる場合に、現在のセルに <xref:System.DBNull.Value?displayProperty=fullName> 値を入力します。  既定では、<xref:System.DBNull> セル値の表示値は、現在のセルに対して有効な <xref:System.Windows.Forms.DataGridViewCellStyle> の <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> プロパティの値です。|  
  
### 選択キー  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> プロパティが `false` に設定され、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A> プロパティが <xref:System.Windows.Forms.DataGridViewSelectionMode> に設定されている場合は、移動キーを使用して現在のセルを変更すると、選択対象が新しいセルに変更されます。  Shift キー、Ctrl キー、および Alt キーはこの動作には影響しません。  
  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> が <xref:System.Windows.Forms.DataGridViewSelectionMode> または <xref:System.Windows.Forms.DataGridViewSelectionMode> に設定されている場合も同じように動作しますが、次の動作が追加されます。  
  
|キーまたはキーの組み合わせ|Description|  
|-------------------|-----------------|  
|Shift \+ Space|行全体または列全体を選択します \(行ヘッダーまたは列ヘッダーを選択するのと同じです\)。|  
|移動キー \(方向キー、PageUp、PageDown、Home、End\)|行全体または列全体が選択されている場合に、現在のセルを新しい行または列に変更すると、選択対象が新しい行全体または列全体に移動します \(選択モードによって異なります\)。|  
  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> が `false` に設定され、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A> が <xref:System.Windows.Forms.DataGridViewSelectionMode> または <xref:System.Windows.Forms.DataGridViewSelectionMode> に設定されている場合は、キーボードを使用して現在のセルを新しい行または列に変更すると、選択対象が新しい行全体または列全体に移動します。  Shift キー、Ctrl キー、および Alt キーはこの動作には影響しません。  
  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> が `true` に設定されている場合は、移動動作は変更されません。ただし、Shift \(Ctrl \+ Shift を含む\) キーを押しながらキーボードを使用する移動では、複数セルの選択動作が変更されます。  移動を開始する前に、コントロールは現在のセルをアンカー セルとしてマークします。  Shift キーを押しながら移動すると、アンカー セルと現在のセルの間のすべてのセルが選択範囲に含められます。  コントロール内のその他のセルは、既に選択されている場合は、選択された状態が保持されます。ただし、キーボードによる移動操作で、これらのセルがアンカー セルと現在のセルの間に一時的に含まれた場合は、選択が解除されることがあります。  
  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> が `true` に設定され、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A> が <xref:System.Windows.Forms.DataGridViewSelectionMode> または <xref:System.Windows.Forms.DataGridViewSelectionMode> に設定されている場合、アンカー セルと現在のセルは同じように動作しますが、選択または選択解除されるのは行全体のみまたは列全体のみです。  
  
## 既定のマウス処理  
  
### 基本的なマウス処理  
  
> [!NOTE]
>  マウスの左ボタンでセルをクリックすると、常に現在のセルが変更されます。  また、マウスの右ボタンでセルをクリックすると、ショートカット メニューがある場合は、ショートカット メニューが開きます。  
  
|マウス操作|Description|  
|-----------|-----------------|  
|マウスの左ボタンを押す|クリックしたセルが現在のセルになり、<xref:System.Windows.Forms.DataGridView.CellMouseDown?displayProperty=fullName> イベントが発生します。|  
|マウスの左ボタンを離す|<xref:System.Windows.Forms.DataGridView.CellMouseUp?displayProperty=fullName> イベントが発生します。|  
|マウスの左ボタンでクリックする|<xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=fullName> イベントと <xref:System.Windows.Forms.DataGridView.CellMouseClick?displayProperty=fullName> イベントが発生します。|  
|マウスの左ボタンを押して列ヘッダー セル上でドラッグする|<xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=fullName> プロパティが `true` の場合、列を新しい位置にドロップできるように移動します。|  
  
### マウスによる選択  
 マウスの中央ボタン \(マウス ホイール\) には選択動作が関連付けられていません。  
  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> プロパティが `false` に設定され、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A> プロパティが <xref:System.Windows.Forms.DataGridViewSelectionMode> に設定されている場合は、次のように動作します。  
  
|マウス操作|Description|  
|-----------|-----------------|  
|マウスの左ボタンでクリックする|ユーザーがセルをクリックした場合、現在のセルだけが選択されます。  ユーザーが行ヘッダーまたは列ヘッダーをクリックした場合、選択動作は行われません。|  
|マウスの右ボタンでクリックする|ショートカット メニューがある場合は、ショートカット メニューが表示されます。|  
  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> が <xref:System.Windows.Forms.DataGridViewSelectionMode> または <xref:System.Windows.Forms.DataGridViewSelectionMode> に設定されている場合も、同様の動作が行われます。ただし、選択モードによっては、行ヘッダーまたは列ヘッダーをクリックすると行全体または列全体が選択され、現在のセルが行または列の最初のセルに設定されます。  
  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> が <xref:System.Windows.Forms.DataGridViewSelectionMode> または <xref:System.Windows.Forms.DataGridViewSelectionMode> に設定されている場合は、行または列の任意のセルをクリックすると行全体または列全体が選択されます。  
  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> が `true` に設定されている場合、Ctrl キーまたは Shift キーを押しながらセルをクリックすると複数セルの選択が変更されます。  
  
 Ctrl キーを押しながらセルをクリックすると、そのセルの選択状態は変化しますが、その他のすべてのセルは現在の選択状態を保持します。  
  
 Shift キーを押しながら特定のセルまたは連続するセルをクリックした場合、現在のセルとアンカー セル \(最初のクリックの前に選択されていたセルの位置にあります\) の間のすべてのセルが選択されます。  マウスをクリックし、複数のセル間でポインターをドラッグした場合、ドラッグ操作の最初にクリックしたセルがアンカー セルになります。  それ以降、Shift キーを押しながらクリックすると、現在のセルは変更されますが、アンカー セルは変更されません。  コントロール内のその他のセルは、既に選択されている場合は、選択された状態が保持されます。ただし、マウスによる移動操作で、これらのセルがアンカー セルと現在のセルの間に一時的に含まれた場合は、選択が解除されることがあります。  
  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> が `true` に設定され、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A> が <xref:System.Windows.Forms.DataGridViewSelectionMode> または <xref:System.Windows.Forms.DataGridViewSelectionMode> に設定されている場合は、Shift キーを押しながら行ヘッダーまたは列ヘッダー \(選択モードによります\) をクリックすると既存の行全体または列全体の選択が変更されます \(そのような選択範囲が存在する場合\)。  それ以外の場合は、選択が解除され、新しい行全体または列全体の選択が開始されます。  ただし、Ctrl キーを押しながら行ヘッダーまたは列ヘッダーをクリックした場合は、クリックした行または列が現在の選択範囲に対して追加または削除されます。現在の選択範囲に対してそれ以外の変更はありません。  
  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> が `true` に設定され、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A> が <xref:System.Windows.Forms.DataGridViewSelectionMode> または <xref:System.Windows.Forms.DataGridViewSelectionMode> に設定されている場合は、Shift キーまたは Ctrl キーを押しながらセルをクリックすると、行全体のみまたは列全体のみが影響を受けることを除き、同じように動作します。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 [DataGridView コントロール](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)