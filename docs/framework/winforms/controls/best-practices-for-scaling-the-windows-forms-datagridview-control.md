---
title: "Windows フォーム DataGridView コントロールを拡張するための推奨される手順 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "推奨される手順, DataGridView コントロール"
  - "データ グリッド, 推奨される手順"
  - "DataGridView コントロール [Windows フォーム], 推奨される手順"
  - "DataGridView コントロール [Windows フォーム], 行の共有"
  - "DataGridView コントロール [Windows フォーム], スケーリング"
  - "DataGridView コントロール [Windows フォーム], 共有行"
ms.assetid: 8321a8a6-6340-4fd1-b475-fa090b905aaf
caps.latest.revision: 31
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 31
---
# Windows フォーム DataGridView コントロールを拡張するための推奨される手順
<xref:System.Windows.Forms.DataGridView> コントロールは、最大のスケーラビリティを提供するようにデザインされています。  大量のデータを表示する必要がある場合は、このトピックのガイドラインに従って、大量のメモリ消費やユーザー インターフェイス \(UI\) の応答速度低下を回避することが必要です。  このトピックでは、次の項目について説明します。  
  
-   セル スタイルの効率的な使用  
  
-   ショートカット メニューの効率的な使用  
  
-   自動サイズ変更の効率的な使用  
  
-   選択されているセル、行、および列のコレクションの効率的な使用  
  
-   共有行の使用  
  
-   行が非共有になることの防止  
  
 特別なパフォーマンス要件がある場合には、仮想モードを実装し、独自のデータ管理操作を提供できます。  詳細については、「[Windows フォーム DataGridView コントロールでのデータ表示モード](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
## セル スタイルの効率的な使用  
 各セル、各行、および各列に、個別のスタイル情報を設定できます。  スタイル情報は、<xref:System.Windows.Forms.DataGridViewCellStyle> オブジェクトに格納されます。  多数の <xref:System.Windows.Forms.DataGridView> 要素それぞれについてセル スタイル オブジェクトを作成することは、特に大量のデータを処理する場合、非効率的です。  パフォーマンスへの影響を回避するには、次のガイドラインに従います。  
  
-   個々の <xref:System.Windows.Forms.DataGridViewCell> オブジェクトまたは <xref:System.Windows.Forms.DataGridViewRow> オブジェクトにセル スタイル プロパティを設定することは避けます。  これには、<xref:System.Windows.Forms.DataGridView.RowTemplate%2A> プロパティで指定された行オブジェクトも含まれます。  行テンプレートから新しい行を複製すると、それぞれの行にテンプレートのセル スタイル オブジェクトのコピーが作成されます。  スケーラビリティを最大にするには、セル スタイル プロパティの設定を <xref:System.Windows.Forms.DataGridView> レベルで行います。  たとえば、<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=fullName> プロパティではなく <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName> プロパティを設定します。  
  
-   既定の書式設定以外の書式設定を必要とするセルがある場合、セル、行、または列の複数のグループで同じ <xref:System.Windows.Forms.DataGridViewCellStyle> インスタンスを使用します。  個別のセル、行、および列で <xref:System.Windows.Forms.DataGridViewCellStyle> 型プロパティを直接設定することは避けます。  セル スタイルを共有する例については、「[方法 : Windows フォーム DataGridView コントロールの既定のセル スタイルを設定する](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)」を参照してください。  <xref:System.Windows.Forms.DataGridView.CellFormatting> イベント ハンドラーを処理してセル スタイルを個別に設定することでも、パフォーマンス低下を回避できます。  カスタマイズ例については、「[方法 : Windows フォーム DataGridView コントロールのデータの書式設定をカスタマイズする](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
-   セルのスタイルを確認するときは、<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=fullName> プロパティではなく <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=fullName> プロパティを使用します。  <xref:System.Windows.Forms.DataGridViewCell.Style%2A> プロパティにアクセスすると、そのプロパティがまだ使用されていない場合は <xref:System.Windows.Forms.DataGridViewCellStyle> クラスの新しいインスタンスが作成されます。  また、行、列、またはコントロールからスタイルを継承している場合は、このオブジェクトにセルの一部のスタイル情報が含まれないことがあります。  セル スタイルの継承の詳細については、「[Windows フォーム DataGridView コントロールでのセルのスタイル](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
## ショートカット メニューの効率的な使用  
 各セル、各行、および各列に、個別のショートカット メニューを設定できます。  <xref:System.Windows.Forms.DataGridView> コントロールのショートカット メニューは、<xref:System.Windows.Forms.ContextMenuStrip> コントロールで表されます。  セル スタイル オブジェクトと同様、多数の <xref:System.Windows.Forms.DataGridView> 要素それぞれについてショートカット メニューを作成すると、パフォーマンスの低下を招きます。  このような影響を回避するには、次のガイドラインに従います。  
  
-   個々のセルおよび行にショートカット メニューを作成することは避けます。  行テンプレートも同様です。行テンプレートは、コントロールに新しい行が追加されるときに複製され、このときショートカット メニューも同時に複製されます。  スケーラビリティを最大にするには、コントロールの <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> プロパティのみを使用して、コントロール全体に単一のショートカット メニューを指定します。  
  
-   複数の行またはセルについて複数のショートカット メニューが必要な場合は、<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> イベントまたは <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded> イベントを処理します。  これらのイベントでショートカット メニュー オブジェクトを操作することで、パフォーマンスを調整できます。  
  
## 自動サイズ変更の効率的な使用  
 セルの内容を変更すると、内容全体が欠けることなく表示されるように、行、列、およびヘッダーのサイズが自動的に変更されることがあります。  サイズ変更モードを変更した場合も、行、列、およびヘッダーのサイズが変更される場合があります。  <xref:System.Windows.Forms.DataGridView> コントロールは、正しいサイズを決定するために、各セルが格納する値を調べます。  大量のデータを処理する場合には、自動サイズ変更が発生してこの解析が行われることによって、パフォーマンスが低下する可能性があります。  パフォーマンスの低下を回避するには、次のガイドラインに従います。  
  
-   大量の行セットを処理する <xref:System.Windows.Forms.DataGridView> コントロールでは、自動サイズ変更の使用を避けます。  自動サイズ変更を使用する場合も、表示されている行に基づくサイズ変更のみにします。  仮想モードでも、表示されている行のみを使用します。  
  
    -   行および列に対して、<xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>、<xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>、および <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode> の各列挙値の `DisplayedCells` フィールドまたは `DisplayedCellsExceptHeaders` フィールドを使用します。  
  
    -   行ヘッダーに、<xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode> 列挙値の <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode> フィールドまたは <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode> フィールドを使用します。  
  
-   スケーラビリティを最大にするには、自動サイズ変更を無効にし、プログラムによるサイズ変更を使用します。  
  
 詳細については、「[Windows フォーム DataGridView コントロールのサイズ変更オプション](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
## 選択されているセル、行、および列のコレクションの効率的な使用  
 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> コレクションは、選択範囲のサイズが大きいと効率が低下します。  <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> コレクションおよび <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> コレクションの効率も低下する場合がありますが、通常の <xref:System.Windows.Forms.DataGridView> コントロールではセルの数よりも行の数が少なく、行の数よりも列の数が少ないため、低下の度合いは小さくなります。  これらのコレクション処理時のパフォーマンスの低下を回避するには、次のガイドラインに従います。  
  
-   <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> コレクションの内容にアクセスする前に <xref:System.Windows.Forms.DataGridView> 内のすべてのセルが選択されているかどうかを確認するには、<xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> メソッドの戻り値をチェックします。  ただし、このメソッドを使用すると、行が非共有になることがあります。  詳細については、次のセクションを参照してください。  
  
-   選択されているセルの数を調べる場合は、<xref:System.Windows.Forms.DataGridViewSelectedCellCollection?displayProperty=fullName> の <xref:System.Collections.ICollection.Count%2A> プロパティの使用を避けます。  代わりに、<xref:System.Windows.Forms.DataGridView.GetCellCount%2A?displayProperty=fullName> メソッドを使用して、<xref:System.Windows.Forms.DataGridViewElementStates?displayProperty=fullName> 値を渡します。  同様に、選択されている要素の数を調べる場合は、選択されている行および列のコレクションにアクセスするのではなく、<xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A?displayProperty=fullName> メソッドおよび <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A?displayProperty=fullName> メソッドを使用します。  
  
-   セルに基づく選択を行うモードの使用を避けます。  代わりに、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=fullName> プロパティを <xref:System.Windows.Forms.DataGridViewSelectionMode?displayProperty=fullName> または <xref:System.Windows.Forms.DataGridViewSelectionMode?displayProperty=fullName> に設定します。  
  
## 共有行の使用  
 共有行を使用すると、<xref:System.Windows.Forms.DataGridView> コントロールでメモリを効率的に使用できます。  複数の行で <xref:System.Windows.Forms.DataGridViewRow> クラスのインスタンスを共有すると、行の表示形式と動作に関する情報が最大限共有されます。  
  
 行のインスタンスを共有するとメモリを節約できる一方、行は非共有になりやすくなります。  たとえば、ユーザーがセルを直接操作すると、そのセルの行は非共有になります。  この動作は避けられないので、このトピックで示すガイドラインが役立つのは、大量のデータを処理する場合、およびプログラムを実行するたびにユーザーが操作するデータの割合が比較的小さい場合に限られます。  
  
 バインドされていない <xref:System.Windows.Forms.DataGridView> コントロール内で、値を含むセルがある行は共有できません。  <xref:System.Windows.Forms.DataGridView> コントロールを外部データ ソースにバインドしている場合、または仮想モードを実装して独自のデータ ソースを指定している場合は、セルの値はセル オブジェクトではなくコントロールの外部に格納されるので、行を共有できます。  
  
 行オブジェクトは、その行のすべてのセルの状態が、それらのセルを含む行の状態および列の状態から決定できる場合に限り、共有できます。  セルの状態が変更され、そのセルの行および列の状態からセルの状態を推測できなくなった場合は、行を共有できません。  
  
 たとえば、次のいずれかの状況にある行は共有できません。  
  
-   選択されている列に含まれていない、単一選択されたセルを含む行。  
  
-   <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> プロパティまたは <xref:System.Windows.Forms.DataGridViewCell.ContextMenuStrip%2A> プロパティが設定されているセルを含む行。  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A> プロパティが設定されている <xref:System.Windows.Forms.DataGridViewComboBoxCell> を含む行。  
  
 バインド モードまたは仮想モードでは、<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> イベントおよび <xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded> イベントを処理することで、ツールヒントおよびショートカット メニューを個別のセルに指定できます。  
  
 <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGridViewRowCollection> に行が追加されるたびに、自動的に共有行を使用しようとします。  行が確実に共有されるようにするには、次のガイドラインに従います。  
  
-   <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=fullName> コレクションの <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> メソッドの `Add(Object[])` オーバーロードおよび <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> メソッドの `Insert(Object[])` オーバーロードを呼び出さないようにします。  これらのオーバーロードは、自動的に非共有行を作成します。  
  
-   <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=fullName> プロパティに指定されている行は、次の場合に共有できます。  
  
    -   <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=fullName> コレクションの <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> メソッドの `Add()` オーバーロードまたは `Add(Int32)` オーバーロード、または <xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> メソッドの `Insert(Int32,Int32)` オーバーロードを呼び出すとき。  
  
    -   <xref:System.Windows.Forms.DataGridView.RowCount%2A?displayProperty=fullName> プロパティの値を増加させるとき。  
  
    -   <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=fullName> プロパティを設定するとき。  
  
-   <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=fullName> コレクションの <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>、<xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>、<xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopy%2A>、および <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopies%2A> の各メソッドを呼び出す場合は、`indexSource` パラメーターで指定される行が共有可能であることを確認してください。  
  
-   <xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=fullName> コレクションの <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A> メソッドの `Add(DataGridViewRow)` オーバーロード、<xref:System.Windows.Forms.DataGridViewRowCollection.AddRange%2A> メソッド、<xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A> メソッドの `Insert(Int32,DataGridViewRow)` オーバーロード、および <xref:System.Windows.Forms.DataGridViewRowCollection.InsertRange%2A> メソッドを呼び出す場合は、指定される行が共有可能であることを確認してください。  
  
 行が共有されているかどうかを確認するには、<xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=fullName> メソッドを使用して行オブジェクトを取得し、そのオブジェクトの <xref:System.Windows.Forms.DataGridViewBand.Index%2A> プロパティを調べます。  共有行の <xref:System.Windows.Forms.DataGridViewBand.Index%2A> プロパティの値は常に –1 です。  
  
## 行が非共有になることの防止  
 共有行がコードまたはユーザー操作の結果として非共有行になることがあります。  パフォーマンスへの影響を回避するには、行が非共有にならないようにする必要があります。  アプリケーション開発時に <xref:System.Windows.Forms.DataGridView.RowUnshared> イベントを使用すると、行が非共有行になるときを確認できます。  これは、行の共有の問題をデバッグする際に便利です。  
  
 行が非共有にならないようにするには、次のガイドラインに従います。  
  
-   <xref:System.Windows.Forms.DataGridView.Rows%2A> コレクションに対して、インデックスを指定したり、`foreach` ループで反復処理したりすることを避けます。  通常は、行に直接アクセスする必要はありません。  行を操作する <xref:System.Windows.Forms.DataGridView> のメソッドは、行のインスタンスではなく行インデックスを引数として使用します。  また、行に関連するイベントのハンドラーは、行プロパティを持つイベント引数オブジェクトを受け取ります。これを使用することで、行を非共有にすることなく操作できます。  
  
-   行オブジェクトにアクセスする必要がある場合は、<xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=fullName> メソッドを使用し、行の実際のインデックスを渡します。  ただし、このメソッドで取得した共有行オブジェクトを変更すると、そのオブジェクトを共有するすべての行が変更されます。  一方、新しいレコードの行は、他の行と共有されないため、他のいずれかの行を変更しても影響を受けません。  また、同じ共有行で表される複数の行が、それぞれ異なるショートカット メニューを持つ場合があります。  共有行のインスタンスから正しいショートカット メニューを取得するには、<xref:System.Windows.Forms.DataGridViewRow.GetContextMenuStrip%2A> メソッドを使用し、行の実際のインデックスを渡します。  そうせずに、共有行の <xref:System.Windows.Forms.DataGridViewRow.ContextMenuStrip%2A> プロパティにアクセスすると、共有行のインデックス \-1 が使用され、正しいショートカット メニューを取得できません。  
  
-   <xref:System.Windows.Forms.DataGridViewRow.Cells%2A?displayProperty=fullName> コレクションにインデックスを指定しないようにします。  セルに直接アクセスすると、そのセルの親となる行が非共有になり、新しい <xref:System.Windows.Forms.DataGridViewRow> のインスタンスが作成されます。  セルに関連するイベントのハンドラーは、セル プロパティを持つイベント引数オブジェクトを受け取ります。これを使用することで、行を非共有にすることなくセルを操作できます。  また、<xref:System.Windows.Forms.DataGridView.CurrentCellAddress%2A> プロパティを使用すると、セルに直接アクセスすることなく、現在のセルの行と列のインデックスを取得できます。  
  
-   セルに基づく選択を行うモードの使用を避けます。  このようなモードでは、行が非共有になります。  代わりに、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=fullName> プロパティを <xref:System.Windows.Forms.DataGridViewSelectionMode?displayProperty=fullName> または <xref:System.Windows.Forms.DataGridViewSelectionMode?displayProperty=fullName> に設定します。  
  
-   <xref:System.Windows.Forms.DataGridViewRowCollection.CollectionChanged?displayProperty=fullName> イベントまたは <xref:System.Windows.Forms.DataGridView.RowStateChanged?displayProperty=fullName> イベントを処理しないでください。  これらのイベントでは、行が非共有になります。  また、<xref:System.Windows.Forms.DataGridViewRowCollection.OnCollectionChanged%2A?displayProperty=fullName> メソッドまたは <xref:System.Windows.Forms.DataGridView.OnRowStateChanged%2A?displayProperty=fullName> メソッドを呼び出さないでください。呼び出すと、これらのイベントが発生します。  
  
-   <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=fullName> プロパティの値が <xref:System.Windows.Forms.DataGridViewSelectionMode>、<xref:System.Windows.Forms.DataGridViewSelectionMode>、<xref:System.Windows.Forms.DataGridViewSelectionMode>、または <xref:System.Windows.Forms.DataGridViewSelectionMode> の場合は、<xref:System.Windows.Forms.DataGridView.SelectedCells%2A?displayProperty=fullName> コレクションにアクセスしないでください。  アクセスすると、選択されているすべての行が非共有になります。  
  
-   <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A?displayProperty=fullName> メソッドを呼び出さないでください。  このメソッドを呼び出すと、行が非共有になります。  
  
-   <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=fullName> プロパティの値が <xref:System.Windows.Forms.DataGridViewSelectionMode> の場合は、<xref:System.Windows.Forms.DataGridView.SelectAll%2A?displayProperty=fullName> メソッドを呼び出さないでください。  アクセスすると、すべての行が非共有になります。  
  
-   セルの <xref:System.Windows.Forms.DataGridViewCell.ReadOnly%2A> プロパティまたは <xref:System.Windows.Forms.DataGridViewCell.Selected%2A> プロパティは、その列の対応するプロパティが `true` に設定されているときは `false` に設定しないでください。  アクセスすると、すべての行が非共有になります。  
  
-   <xref:System.Windows.Forms.DataGridViewRowCollection.List%2A?displayProperty=fullName> プロパティにアクセスしないでください。  アクセスすると、すべての行が非共有になります。  
  
-   <xref:System.Windows.Forms.DataGridView.Sort%2A> メソッドの `Sort(IComparer)` オーバーロードを呼び出さないでください。  カスタム比較子で並べ替えを行うと、すべての行が非共有になります。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 [Windows フォーム DataGridView コントロールでのパフォーマンス チューニング](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールでの仮想モード](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールでのデータ表示モード](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールでのセルのスタイル](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)   
 [方法 : Windows フォーム DataGridView コントロールの既定のセル スタイルを設定する](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールのサイズ変更オプション](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)