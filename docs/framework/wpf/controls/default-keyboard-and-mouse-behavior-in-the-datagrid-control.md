---
title: "DataGrid コントロールの既定のキーボード動作とマウス動作 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DataGrid [WPF], キーボード動作"
  - "DataGrid [WPF], マウスの動作"
  - "キーボード動作 [WPF], DataGrid"
  - "マウスの動作 [WPF], DataGrid"
ms.assetid: 563b8854-ca39-4d97-8235-17eaa0f93c8d
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# DataGrid コントロールの既定のキーボード動作とマウス動作
このトピックでは、ユーザーがキーボードとマウスを使用して <xref:System.Windows.Controls.DataGrid> コントロールと対話する方法について説明します。  
  
 <xref:System.Windows.Controls.DataGrid> に対する標準的な対話操作には、ナビゲーション、選択、編集などがあります。  選択動作は、<xref:System.Windows.Controls.DataGrid.SelectionMode%2A> プロパティおよび <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> プロパティの影響を受けます。  このトピックで説明した動作の前提となる既定値は、<xref:System.Windows.Controls.DataGridSelectionMode?displayProperty=fullName> および <xref:System.Windows.Controls.DataGridSelectionUnit?displayProperty=fullName> です。  これらの値を変更すると、ここでの説明内容とは動作が異なる場合があります。  セルが編集モードになっている場合、<xref:System.Windows.Controls.DataGrid> の標準キーボードの動作は、編集コントロールによってオーバーライドされます。  
  
## キーボードの既定の動作  
 <xref:System.Windows.Controls.DataGrid> におけるキーボードの既定の動作を次の表に示します。  
  
|キーまたはキーの組み合わせ|Description|  
|-------------------|-----------------|  
|↓|現在のセルの 1 つ下のセルにフォーカスを移動します。  フォーカスが最後の行にある場合は、何も行いません。|  
|↑|現在のセルの 1 つ上のセルにフォーカスを移動します。  フォーカスが最初の行にある場合は、何も行いません。|  
|←|同じ行の 1 つ前のセルにフォーカスを移動します。  フォーカスが行の最初のセルにある場合は、何も行いません。|  
|→|同じ行の次のセルにフォーカスを移動します。  フォーカスが行の最後のセルにある場合は、何も行いません。|  
|Home|現在の行の最初のセルにフォーカスを移動します。|  
|End|現在の行の最後のセルにフォーカスを移動します。|  
|PageDown|行がグループ化されていない場合、完全に表示されている行数分、コントロールを下にスクロールします。  完全に表示されている最後の行にフォーカスを移動します。列は変更しません。<br /><br /> 行がグループ化されている場合、<xref:System.Windows.Controls.DataGrid> 内の最後の行にフォーカスを移動します。列は変更されません。|  
|PageUp|行がグループ化されていない場合、完全に表示されている行数分、コントロールを上にスクロールします。  現在表示されている最初の行にフォーカスを移動します。列は変更しません。<br /><br /> 行がグループ化されている場合、<xref:System.Windows.Controls.DataGrid> 内の先頭の行にフォーカスを移動します。列は変更されません。|  
|Tab|現在の行の次のセルにフォーカスを移動します。  行の最後のセルにフォーカスがあるときは、次の行の最初のセルにフォーカスを移動します。  コントロールの最後のセルにフォーカスがあるときは、親コンテナーのタブ オーダーで次のコントロールにフォーカスを移動します。<br /><br /> 現在のセルが編集モードになっている場合、Tab キーを押すと、フォーカスが現在の行から移動します。その行に対して行われた変更は、フォーカスが変わる前にコミットされます。|  
|Shift \+ Tab|現在の行の前のセルにフォーカスを移動します。  行の最初のセルにフォーカスがあるときは、1 つ前の行の最後のセルにフォーカスを移動します。  コントロールの最初のセルにフォーカスがある場合は、親コンテナーのタブ オーダーで 1 つ前のコントロールにフォーカスを移動します。<br /><br /> 現在のセルが編集モードになっている場合、Tab キーを押すと、フォーカスが現在の行から移動します。その行に対して行われた変更は、フォーカスが変わる前にコミットされます。|  
|Ctrl \+ ↓|現在の列の最後のセルにフォーカスを移動します。|  
|Ctrl \+ ↑|現在の列の最初のセルにフォーカスを移動します。|  
|Ctrl \+ →|現在の行の最後のセルにフォーカスを移動します。|  
|Ctrl \+ ←|現在の行の最初のセルにフォーカスを移動します。|  
|Ctrl \+ Home|コントロール内の最初のセルにフォーカスを移動します。|  
|Ctrl \+ End|コントロール内の最後のセルにフォーカスを移動します。|  
|Ctrl \+ PageDown|PageDown と同じです。|  
|Ctrl \+ PageUp|PageUp と同じです。|  
|F2|<xref:System.Windows.Controls.DataGrid.IsReadOnly%2A?displayProperty=fullName> プロパティが `false` で、現在の列の <xref:System.Windows.Controls.DataGridColumn.IsReadOnly%2A?displayProperty=fullName> プロパティが `false` の場合、現在のセルを編集モードに設定します。|  
|Enter|現在のセルおよび行への変更をコミットし、現在のセルの 1 つ下のセルにフォーカスを移動します。  フォーカスが最後の行にある場合は、変更をコミットし、フォーカスは移動しません。|  
|Esc|コントロールが編集モードの場合は、編集を取り消し、コントロール内で行われた変更をすべて元に戻します。  基になるデータ ソースに <xref:System.ComponentModel.IEditableObject> が実装されている場合、Esc キーを 2 回押すと、行全体の編集モードが取り消されます。|  
|BackSpace|セルを編集するときに、カーソル位置の前にある文字を削除します。|  
|Del|セルを編集するときに、カーソル位置の後にある文字を削除します。|  
|Ctrl \+ Enter|現在のセルに対して行われた変更をコミットします。フォーカスは移動しません。|  
|Ctrl \+ A|<xref:System.Windows.Controls.DataGrid.SelectionMode%2A> が <xref:System.Windows.Controls.DataGridSelectionMode> に設定されている場合、<xref:System.Windows.Controls.DataGrid> 内のすべての行を選択します。|  
  
## 選択キー  
 <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> プロパティが <xref:System.Windows.Controls.DataGridSelectionMode> に設定されている場合は、移動動作は変更されません。ただし、Shift \(Ctrl \+ Shift を含む\) キーを押しながらキーボードを使用する移動では、複数行の選択範囲が変更されます。  移動を開始する前に、コントロールは現在の行をアンカー行としてマークします。  Shift キーを押しながら移動すると、アンカー行と現在の行の間のすべての行が選択範囲に含められます。  
  
 次の選択キーでは、複数行の選択範囲が変更されます。  
  
-   Shift \+ ↓  
  
-   Shift \+ ↑  
  
-   Shift \+ PageDown  
  
-   Shift \+ PageUp  
  
-   Ctrl \+ Shift \+ ↓  
  
-   Ctrl \+ Shift \+ ↑  
  
-   Ctrl \+ Shift \+ Home  
  
-   Ctrl \+ Shift \+ End  
  
## マウスの既定の動作  
 <xref:System.Windows.Controls.DataGrid> におけるマウスの既定の動作を次の表に示します。  
  
|マウス操作|Description|  
|-----------|-----------------|  
|未選択の行をクリック|クリックした行が現在の行になり、クリックしたセルが現在のセルになります。|  
|現在のセルをクリック|現在のセルを編集モードにします。|  
|列ヘッダー セルをドラッグ|<xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A?displayProperty=fullName> プロパティが `true` で、現在の列の <xref:System.Windows.Controls.DataGridColumn.CanUserReorder%2A?displayProperty=fullName> プロパティが `true` の場合、列を移動して別の位置にドロップできます。|  
|列ヘッダーの区切りをドラッグ|<xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=fullName> プロパティが `true` で、現在の列の <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=fullName> プロパティが `true` の場合、列のサイズが変更されます。|  
|列ヘッダーの区切りをダブルクリック|現在の列の <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=fullName> プロパティが `true` で、<xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=fullName> プロパティが `true` である場合、<xref:System.Windows.Controls.DataGridLength.Auto%2A> サイズ変更モードを使用して列のサイズを自動調整します。|  
|列ヘッダー セルをクリック|<xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A?displayProperty=fullName> プロパティが `true` で、現在の列の <xref:System.Windows.Controls.DataGridColumn.CanUserSort%2A?displayProperty=fullName> プロパティが `true` の場合、列の並べ替えが実行されます。<br /><br /> 既に並べ替えられた列のヘッダーをクリックすると、逆順で並べ替えが行われます。<br /><br /> Shift キーを押しながら複数の列ヘッダーをクリックすると、クリックした順番で、複数の列に基づいて並べ替えが適用されます。|  
|Ctrl キーを押しながら行をクリック|<xref:System.Windows.Controls.DataGrid.SelectionMode%2A> が <xref:System.Windows.Controls.DataGridSelectionMode> に設定されている場合、不連続の複数の行を選択できます。<br /><br /> 既に行が選択されている場合、行の選択を解除します。|  
|Shift キーを押しながら行をクリック|<xref:System.Windows.Controls.DataGrid.SelectionMode%2A> が <xref:System.Windows.Controls.DataGridSelectionMode> に設定されている場合、連続する複数の行を選択できます。|  
|行グループ ヘッダーをクリック|グループの展開または折りたたみを行います。|  
|<xref:System.Windows.Controls.DataGrid> の左上隅の \[すべて選択\] ボタンをクリック|<xref:System.Windows.Controls.DataGrid.SelectionMode%2A> が <xref:System.Windows.Controls.DataGridSelectionMode> に設定されている場合、<xref:System.Windows.Controls.DataGrid> 内のすべての行を選択します。|  
  
## マウスによる選択  
 <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> プロパティが <xref:System.Windows.Controls.DataGridSelectionMode> に設定されている場合、Ctrl キーまたは Shift キーを押しながら行をクリックすると複数行の選択範囲が変更されます。  
  
 Ctrl キーを押しながら行をクリックすると、その行の選択状態は変化しますが、その他のすべての行は現在の選択状態を保持します。  隣接しない行を選択するにはこの方法を使用します。  
  
 Shift キーを押しながら特定の行をクリックした場合、現在の行とアンカー行 \(クリックの前に選択されていた行\) の間のすべての行が選択されます。  それ以降、Shift キーを押しながらクリックすると、現在の行は変更されますが、アンカー行は変更されません。  隣接する行の範囲を選択するにはこの方法を使用します。  
  
 Ctrl キーを押しながら Shift キーを押すと、離れて存在する隣接行範囲を選択できます。  そのためには、前の説明に従い、Shift キーを押しながらのクリック操作で、1 つ目の範囲を選択します。  1 つ目の行範囲を選択したら、Ctrl キーを押しながらのクリック操作で、次の範囲内の先頭行をまず選択し、Ctrl キーと Shift キーを押した状態で、その範囲の最後の行をクリックします。  
  
## 参照  
 <xref:System.Windows.Controls.DataGrid>   
 <xref:System.Windows.Controls.DataGrid.SelectionMode%2A>