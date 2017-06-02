---
title: "Windows フォーム DataGridView コントロールの選択モード | Microsoft Docs"
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
  - "DataGridView コントロール [Windows フォーム], 選択モード"
  - "選択, モード (DataGridView コントロール内の)"
ms.assetid: a3ebfd3d-0525-479d-9d96-d9e017289b36
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Windows フォーム DataGridView コントロールの選択モード
作成したアプリケーションで実行するアクションを、<xref:System.Windows.Forms.DataGridView> コントロール内のユーザーの選択に基づいて決定する必要がある場合があります。  実行するアクションによっては、可能な選択の種類を制限することが必要になります。  たとえば、現在選択されているレコードに関するレポートを印刷できるアプリケーションを作成するとします。  この場合、行内の任意の場所をクリックすると必ず行全体が選択され、一度に 1 行だけ選択できるように <xref:System.Windows.Forms.DataGridView> コントロールを設定する必要があります。  
  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=fullName> プロパティを次の <xref:System.Windows.Forms.DataGridViewSelectionMode> 列挙値のいずれかに設定すると、許可する選択を指定できます。  
  
|DataGridViewSelectionMode の値|Description|  
|----------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode>|セルをクリックすると、そのセルが選択されます。  行ヘッダーおよび列ヘッダーを使用した選択はできません。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode>|セルをクリックすると、そのセルが選択されます。  列ヘッダーをクリックすると、その列全体が選択されます。  列ヘッダーを使用した並べ替えはできません。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode>|セルまたは列ヘッダーをクリックすると、その列全体が選択されます。  列ヘッダーを使用した並べ替えはできません。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode>|セルまたは行ヘッダーをクリックすると、その行全体が選択されます。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode>|既定の選択モードです。  セルをクリックすると、そのセルが選択されます。  行ヘッダーをクリックすると、その行全体が選択されます。|  
  
> [!NOTE]
>  実行時に選択モードを変更すると、その時点での選択は自動的に解除されます。  
  
 既定では、ユーザーは、選択範囲を拡大または変更する際に Ctrl キーまたは Shift キーを押しながらマウスをドラッグすることで、複数の行、列、またはセルを選択できます。また、左上隅のヘッダー セルをクリックすることで、コントロール内のすべてのセルを選択できます。  この動作を無効にするには、<xref:System.Windows.Forms.DataGridView.MultiSelect%2A> プロパティを `false` に設定します。  
  
 <xref:System.Windows.Forms.DataGridViewSelectionMode> モードおよび <xref:System.Windows.Forms.DataGridViewSelectionMode> モードでは、ユーザーは、行を選択して Del キーを押すことで、選択した行を削除できます。  ユーザーが行を削除できるのは、現在のセルが編集モードになっておらず、<xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> プロパティが `true` に設定されており、基になるデータ ソースでユーザーによる行の削除がサポートされている場合に限られます。  これらの設定に関係なく、プログラムからは行を削除できます。  
  
## プログラムによる選択  
 ユーザーによる選択と同様、プログラムによる選択の動作も、現在の選択モードによって制限されます。  <xref:System.Windows.Forms.DataGridView> コントロール内のセル、行、または列の `Selected` プロパティを設定すると、プログラムから現在の選択を変更できます。  また、選択モードによっては、<xref:System.Windows.Forms.DataGridView.SelectAll%2A> メソッドによってコントロール内のすべてのセルを選択することもできます。  選択を解除するには、<xref:System.Windows.Forms.DataGridView.ClearSelection%2A> メソッドを使用します。  
  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> プロパティが `true` に設定されている場合は、<xref:System.Windows.Forms.DataGridView> の要素の `Selected` プロパティを変更することにより、その要素を選択に追加したり、選択から解除したりできます。  それ以外の場合は、1 つの要素の `Selected` プロパティを `true` に設定すると、他の要素の選択は自動的に解除されます。  
  
 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> プロパティの値を変更しても、現在の選択は変更されません。  
  
 <xref:System.Windows.Forms.DataGridView> コントロールの <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>、<xref:System.Windows.Forms.DataGridView.SelectedRows%2A>、および <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> の各プロパティから、現在選択されているセル、行、または列のコレクションを取得できます。  コントロール内のすべてのセルが選択されている場合は、これらのプロパティを使用するのは効率的ではありません。  このような場合のパフォーマンス低下を回避するには、先に <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> メソッドを使用します。  また、選択されているセル、行、または列の数を調べる際にも、これらのコレクションを使用することは非効率的である場合があります。  代わりに、<xref:System.Windows.Forms.DataGridView.GetCellCount%2A>、<xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A>、または <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A> の各メソッドを使用し、<xref:System.Windows.Forms.DataGridViewElementStates> の値を渡してください。  
  
> [!TIP]
>  選択されているセルをプログラムで使用する方法を示すコード例は、<xref:System.Windows.Forms.DataGridView> クラスの概要にあります。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>   
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>   
 <xref:System.Windows.Forms.DataGridViewSelectionMode>   
 [Windows フォーム DataGridView コントロールでの選択およびクリップボードの使用](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)   
 [方法 : Windows フォーム DataGridView コントロールの選択モードを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)