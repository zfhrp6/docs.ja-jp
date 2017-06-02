---
title: "Windows フォームの DataGrid コントロール内の移動に使用できるキーボード ショートカット | Microsoft Docs"
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
  - "DataGrid コントロール [Windows フォーム], 移動キー"
  - "ショートカット キー, DataGrid コントロール"
ms.assetid: a01780f9-20d5-4f5f-808f-c790c9a007a5
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Windows フォームの DataGrid コントロール内の移動に使用できるキーボード ショートカット
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 Windows フォームの <xref:System.Windows.Forms.DataGrid> コントロール内の移動に使用できるキーボード ショートカットの一覧を示します。  
  
|動作|Shortcut|  
|--------|--------------|  
|現在のセルへの入力を終了し、次のセルへ移動します。<br /><br /> フォーカスが子テーブルのリンクにある場合は、その子テーブルに移動します。|Enter|  
|セル内が編集モードの場合は、セルの編集をキャンセルします。<br /><br /> マーキー選択の場合は、該当する行の編集をキャンセルします。|Esc|  
|セルを編集するときに、カーソル位置の前にある文字列を削除します。|BackSpace|  
|セルを編集するときに、カーソル位置の後にある文字列を削除します。|Del|  
|現在の行にある最初のセルに移動します。|Home|  
|現在の行にある最後のセルに移動します。|End|  
|現在のセルの文字列を強調表示し、行の最後にカーソルを位置付けます。  セルをダブルクリックするのと同じ動作になります。|F2|  
|セルにフォーカスがある場合は、同一行の次のセルに移動します。<br /><br /> フォーカスが行の最後のセルにある場合は、その行の最初の子テーブルへのリンクへ移動し、展開します。<br /><br /> 子リンクにフォーカスがある場合は、次の子リンクに移動します。<br /><br /> 最後の子リンクにフォーカスがある場合は、次の行の最初のセルに移動します。|Tab|  
|セルにフォーカスがある場合は、同一行の 1 つ前のセルに移動します。<br /><br /> 行の最初のセルにフォーカスがある場合は、1 つ前の行の最後に展開された子テーブルへのリンク、または 1 つ前の行の最後のセルに移動します。<br /><br /> 子リンクにフォーカスがある場合は、1 つ前の子リンクに移動します。<br /><br /> 最初の子リンクにフォーカスがある場合は、1 つ前の行の最後のセルに移動します。|Shift \+ Tab|  
|タブ オーダー内の次のコントロールに移動します。|Ctrl \+ Tab|  
|タブ オーダー内の 1 つ前のコントロールに移動します。|Ctrl \+ Shift \+ Tab|  
|子テーブル内の場合は、親テーブルへ移動します。  \[戻る\] をクリックするのと同じ動作になります。|Alt \+ ←|  
|子テーブルへのリンクを展開します。  Alt キーを押しながら ↓ キーを押すと、選択されているリンクだけでなく、すべてのリンクが展開されます。|Alt \+ ↓ または Ctrl \+ プラス記号 \(\+\)|  
|子テーブルへのリンクを折りたたみます。  Alt キーを押しながら ↑ キーを押すと、選択されているリンクだけでなく、すべてのリンクが折りたたまれます。|Alt \+ ↑ または Ctrl \+ マイナス記号 \(\-\)|  
|矢印の方向にある最も遠い、空白でないセルへ移動します。|Ctrl \+ 方向キー|  
|選択範囲を矢印の方向に 1 行分拡張します \(子テーブルのリンクは除外します\)。|Shift \+ ↑ または Shift \+ ↓|  
|矢印の方向にある最も遠い、空白でない行まで選択範囲を拡張します \(子テーブルのリンクは除きます\)。|Ctrl \+ Shift \+ ↑ または Ctrl \+ Shift \+ ↓|  
|左上のセルへ移動します。|Ctrl \+ Home|  
|右下のセルへ移動します。|Ctrl \+ End|  
|一番上の行まで選択範囲を拡張します。|Ctrl \+ Shift \+ Home|  
|一番下の行まで選択範囲を拡張します。|Ctrl \+ Shift \+ End|  
|現在の行を選択します \(子テーブルのリンクは除きます\)。|Shift \+ Space|  
|グリッド全体を選択します \(子テーブルのリンクは除きます\)。|Ctrl \+ A|  
|子テーブル内の場合は、親テーブルの行を表示します。|Ctrl \+ PageDown|  
|子テーブル内の場合は、親テーブルの行を非表示にします。|Ctrl \+ PageUp|  
|選択範囲を 1 画面分下に拡張します \(子テーブルのリンクは除きます\)。|Shift \+ PageDown|  
|選択範囲を 1 画面分上に拡張します \(子テーブルのリンクは除きます\)。|Shift \+ PageUp|  
|現在の行で <xref:System.Windows.Forms.DataGrid.EndEdit%2A> メソッドを呼び出します。|Ctrl \+ Enter|  
|編集モードのときにセルに <xref:System.DBNull.Value?displayProperty=fullName> 値を入力します。|Ctrl \+ 0|  
  
## 参照  
 [DataGrid コントロールの概要](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)   
 [DataGrid コントロール](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)