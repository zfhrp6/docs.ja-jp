---
title: Windows フォーム DataGridView コントロールを拡張するための推奨される手順
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], row sharing
- data grids [Windows Forms], best practices
- DataGridView control [Windows Forms], shared rows
- DataGridView control [Windows Forms], best practices
- best practices [Windows Forms], dataGridView control
- DataGridView control [Windows Forms], scaling
ms.assetid: 8321a8a6-6340-4fd1-b475-fa090b905aaf
ms.openlocfilehash: 91153df539871de571375d7bf6d49d712a0c43b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529809"
---
# <a name="best-practices-for-scaling-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールを拡張するための推奨される手順
<xref:System.Windows.Forms.DataGridView>コントロールが最大限のスケーラビリティを提供するように設計されています。 大量のデータを表示する必要がある場合または大量のメモリを使用して、ユーザー インターフェイス (UI) の応答性を低下させることを回避するには、このトピックで説明されているガイドラインに従ってください。 このトピックでは、次の問題について説明します。  
  
-   セル スタイルを効率的に使用します。  
  
-   ショートカット メニューを効率的に使用します。  
  
-   自動サイズ変更の効率的に使用します。  
  
-   選択したセル、行、および列のコレクションの効率的な使用  
  
-   共有行の使用  
  
-   行が非共有になることを妨げてください。  
  
 特別なパフォーマンスのニーズがある場合は、仮想モードを実装し、独自のデータ管理操作を提供できます。 詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールでのデータ表示モード](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)です。  
  
## <a name="using-cell-styles-efficiently"></a>セル スタイルを効率的に使用します。  
 各セル、行、および列には、独自のスタイル情報を持つことができます。 スタイル情報が格納されている<xref:System.Windows.Forms.DataGridViewCellStyle>オブジェクト。 多くの個々 のセル スタイル オブジェクトを作成する<xref:System.Windows.Forms.DataGridView>大量のデータを使用する場合に特にに要素が、効率的にすることができます。 パフォーマンスに影響を回避するのには、次のガイドラインを使用します。  
  
-   個々 のセル スタイル プロパティを設定しないように<xref:System.Windows.Forms.DataGridViewCell>または<xref:System.Windows.Forms.DataGridViewRow>オブジェクト。 指定された行のオブジェクトが含まれます、<xref:System.Windows.Forms.DataGridView.RowTemplate%2A>プロパティです。 テンプレートのセル スタイル オブジェクトのコピーが新しい行のテンプレートから複製する各行に表示されます。 スケーラビリティを最大にするでのセル スタイル プロパティを設定、<xref:System.Windows.Forms.DataGridView>レベル。 たとえば、設定、<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>プロパティではなく、<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>プロパティです。  
  
-   一部のセルは、既定の書式設定よりもその他の書式設定を必要とする場合と同じ使用<xref:System.Windows.Forms.DataGridViewCellStyle>セル、行、または列のグループにまたがるインスタンス。 型のプロパティを直接設定しないでください<xref:System.Windows.Forms.DataGridViewCellStyle>個々 のセル、行、および列にします。 セルのスタイルの共有の例は、次を参照してください。[する方法: Windows フォーム DataGridView コントロールの既定のセル スタイルの設定](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)です。 セルのスタイルを処理することにより個別に設定するときにも、パフォーマンスの低下を回避できます、<xref:System.Windows.Forms.DataGridView.CellFormatting>イベント ハンドラー。 例については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールでデータの書式をカスタマイズする](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)です。  
  
-   セルのスタイルを決定するときに使用して、<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType>プロパティではなく、<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>プロパティです。 アクセス、<xref:System.Windows.Forms.DataGridViewCell.Style%2A>プロパティの新しいインスタンスを作成する、<xref:System.Windows.Forms.DataGridViewCellStyle>クラスのプロパティは既に使用されていない場合。 さらに、このオブジェクトには可能性がありますが含まれていませんのセルの完全なスタイル情報には一部のスタイルは、行、列、またはコントロールから継承された場合。 セル スタイルの継承の詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールのセル スタイル](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)です。  
  
## <a name="using-shortcut-menus-efficiently"></a>ショートカット メニューを効率的に使用します。  
 各セル、行、および列には、独自のショートカット メニューを持つことができます。 ショートカット メニューで、<xref:System.Windows.Forms.DataGridView>コントロールがによって表される<xref:System.Windows.Forms.ContextMenuStrip>コントロール。 セル スタイル オブジェクトと同様に、多くの個々 のショートカット メニューを作成します。<xref:System.Windows.Forms.DataGridView>要素には、パフォーマンスが低下します。 この低下を避けるためには、次のガイドラインに従います。  
  
-   個々 のセルと行のショートカット メニューを作成しないでください。 これには、コントロールに新しい行が追加されると共に、ショートカット メニューを複製する行テンプレートが含まれます。 最大限のスケーラビリティ、管理を使用してのみの<xref:System.Windows.Forms.Control.ContextMenuStrip%2A>プロパティ コントロール全体の 1 つのショートカット メニューを指定します。  
  
-   で複数の行またはセルを複数のショートカット メニューを要求する場合は、処理、<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded>または<xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>イベント。 これらのイベントでは、ショートカット メニュー オブジェクトを管理できます。 自分で、パフォーマンスを調整することができます。  
  
## <a name="using-automatic-resizing-efficiently"></a>自動サイズ変更の効率的に使用します。  
 行、列、およびヘッダーに自動的にサイズを変更できるセルの内容の変更としてセルの内容全体がクリッピングなしに表示されるようにします。 サイズ変更モードを変更することができますもサイズを変更する行、列、およびヘッダー。 適切なサイズを決定する、<xref:System.Windows.Forms.DataGridView>コントロールに対応する必要がありますの各セルの値を調べる必要があります。 大きなデータ セットを使用するときにこの分析できるパフォーマンスに悪影響コントロールの自動サイズ変更が発生したとき。 パフォーマンスの低下を避けるためには、次のガイドラインに従います。  
  
-   自動サイズ変更は使用しないでください、<xref:System.Windows.Forms.DataGridView>行の大きなセットで制御します。 自動サイズ変更、表示されている行に基づくサイズ変更のみを使用場合します。 仮想モードにも表示されている行のみを使用します。  
  
    -   行と列を使用して、`DisplayedCells`または`DisplayedCellsExceptHeaders`のフィールド、 <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>、 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>、および<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>列挙体です。  
  
    -   行ヘッダーを使用して、<xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToDisplayedHeaders>または<xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToFirstHeader>のフィールド、<xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>列挙します。  
  
-   スケーラビリティを最大にするには、サイズの自動調整をオフにして、プログラムによるサイズ変更を使用します。  
  
 詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールのサイズ変更オプション](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)です。  
  
## <a name="using-the-selected-cells-rows-and-columns-collections-efficiently"></a>選択したセル、行、および列のコレクションを効率的に使用します。  
 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>大規模な選択にコレクションが効率的に実行されません。 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>と<xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>コレクション解除することも、効率的な度より低いレベルには一般的なセルより少ない数の行があるため<xref:System.Windows.Forms.DataGridView>制御、および行よりも多くの少ない列です。 パフォーマンスの低下を避けるためには、これらのコレクションを使用する場合、次のガイドラインに従います。  
  
-   決定するかどうかのすべてのセル、<xref:System.Windows.Forms.DataGridView>の内容にアクセスする前に選択されている、 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> 、コレクションの戻り値を確認して、<xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>メソッドです。 ただし、このメソッドは、共有が解除する行で発生することに注意してください。 詳細については、次のセクションを参照してください。  
  
-   使用しないでください、<xref:System.Collections.ICollection.Count%2A>のプロパティ、<xref:System.Windows.Forms.DataGridViewSelectedCellCollection?displayProperty=nameWithType>を選択したセルの数を決定します。 代わりに、使用、<xref:System.Windows.Forms.DataGridView.GetCellCount%2A?displayProperty=nameWithType>メソッドを渡します、<xref:System.Windows.Forms.DataGridViewElementStates.Selected?displayProperty=nameWithType>値。 同様に、使用、<xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A?displayProperty=nameWithType>と<xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A?displayProperty=nameWithType>メソッドを選択した行と列コレクションにアクセスするのではなく、選択した要素の数を決定します。  
  
-   セルに基づく選択モードは避けてください。 代わりに、設定、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>プロパティを<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>または<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>です。  
  
## <a name="using-shared-rows"></a>行の共有の使用  
 効率的なメモリの使用を行う、<xref:System.Windows.Forms.DataGridView>共有行を制御します。 行のインスタンスを共有することで、できるだけ、外観と動作に関する多くの情報を共有、<xref:System.Windows.Forms.DataGridViewRow>クラスです。  
  
 行のインスタンスの共有メモリを節約できる行は簡単になる共有されていません。 たとえば、ユーザーは、セルと直接やり取りをするたびにその行は非共有になります。 これを回避することはできません、ためこのトピックのガイドラインでは、非常に大量のデータを使用する場合にのみ、ユーザーが操作するデータの割合が比較的小さいプログラムを実行するたびに場合にのみ役立ちます。  
  
 行を共有することはできません、バインドされていないで<xref:System.Windows.Forms.DataGridView>のセルの値が含まれている場合は、制御します。 ときに、<xref:System.Windows.Forms.DataGridView>コントロールが外部データ ソースにバインドされているか、セル オブジェクトであり、共有する行ではなく、コントロールの外部仮想モードを実装する独自のデータ ソースを指定すると、セルの値が格納されます。  
  
 行オブジェクトは、行の状態と、セルを含む列の状態からすべてのセルの状態を特定できない場合にのみ共有できます。 場合は、行と列の状態から不要になった推測できるように、セルの状態を変更すると、行を共有することはできません。  
  
 たとえば、行は、次の状況のいずれかで共有できません。  
  
-   行には、選択した列に含まれていない 1 つの選択したセルが含まれています。  
  
-   行を含むセルに含まれるその<xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A>または<xref:System.Windows.Forms.DataGridViewCell.ContextMenuStrip%2A>プロパティを設定します。  
  
-   行に含まれる、<xref:System.Windows.Forms.DataGridViewComboBoxCell>でその<xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A>プロパティ セットです。  
  
 バインド モードまたは仮想モードで使用できるツールヒントとショートカット メニューの個々 のセルの処理によって、<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>と<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded>イベント。  
  
 <xref:System.Windows.Forms.DataGridView>コントロールは自動的に試みますに行が追加されるたびに、共有された行を使用して、<xref:System.Windows.Forms.DataGridViewRowCollection>です。 次のガイドラインを使用して、行を共有することを確認してください。  
  
-   通話を避けるため、`Add(Object[])`のオーバー ロード、<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>メソッドおよび`Insert(Object[])`のオーバー ロード、<xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A>のメソッド、<xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>コレクション。 これらのオーバー ロードは、共有されていない行を自動的に作成します。  
  
-   あることを確認で指定された行、<xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>プロパティは、次の場合に共有できます。  
  
    -   呼び出すときに、`Add()`または`Add(Int32)`のオーバー ロードが、<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>メソッドまたは`Insert(Int32,Int32)`のオーバー ロード、<xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A>のメソッド、<xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>コレクション。  
  
    -   値を増やすときに、<xref:System.Windows.Forms.DataGridView.RowCount%2A?displayProperty=nameWithType>プロパティです。  
  
    -   設定するときに、<xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>プロパティです。  
  
-   あることを確認で示される行、`indexSource`を呼び出すときに、パラメーターを共有することができます、 <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>、 <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>、 <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopy%2A>、および<xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopies%2A>のメソッド、<xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>コレクション。  
  
-   指定された行の行で共有できることを呼び出すときに、必ず、`Add(DataGridViewRow)`のオーバー ロード、<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>メソッド、<xref:System.Windows.Forms.DataGridViewRowCollection.AddRange%2A>メソッド、`Insert(Int32,DataGridViewRow)`のオーバー ロード、<xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A>メソッド、および<xref:System.Windows.Forms.DataGridViewRowCollection.InsertRange%2A>のメソッド<xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>コレクション。  
  
 行を共有するかどうかを判断するのには、使用、<xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType>行オブジェクトを取得し、オブジェクトのメソッド<xref:System.Windows.Forms.DataGridViewBand.Index%2A>プロパティです。 常に共有行である、 <xref:System.Windows.Forms.DataGridViewBand.Index%2A> – 1 のプロパティの値。  
  
## <a name="preventing-rows-from-becoming-unshared"></a>行が非共有になることを妨げてください。  
 共有行は、コードまたはユーザーの操作の結果として共有されていないになることができます。 パフォーマンスに影響を回避するのには、共有が解除する行の原因を避ける必要があります。 処理できるアプリケーションの開発中、<xref:System.Windows.Forms.DataGridView.RowUnshared>行に非共有になる時期を決定するイベントです。 これは、機能は、行の共有の問題をデバッグするときに便利です。  
  
 行が非共有にならないようにするのには、次のガイドラインを使用します。  
  
-   インデックス作成を避けるため、<xref:System.Windows.Forms.DataGridView.Rows%2A>またはコレクションを反復処理に使用して、`foreach`ループします。 行に直接アクセスする通常必要はありません。 <xref:System.Windows.Forms.DataGridView> 行を操作するメソッドは、行のインスタンスではなく、行のインデックスの引数を取ります。 さらに、行に関連するイベント ハンドラーは発生させずに共有が解除する行を操作に使用できる行のプロパティを持つイベント引数オブジェクトを受け取ります。  
  
-   行オブジェクトにアクセスする必要がある場合、<xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType>メソッドと行の実際のインデックスを渡します。 ただし、このメソッドを使用して取得共有行オブジェクトを変更すると、このオブジェクトを共有するすべての行は変更することに注意してください。 新しいレコードの行とは共有されません他の行では、ただし、ため、他の行を変更するときに影響しません。 共有行によって表される複数の異なる行に異なるショートカット メニューがあることにも注意してください。 共有行のインスタンスから正しいショートカット メニューを取得する、<xref:System.Windows.Forms.DataGridViewRow.GetContextMenuStrip%2A>メソッドと行の実際のインデックスを渡します。 共有行にアクセスする場合は<xref:System.Windows.Forms.DataGridViewRow.ContextMenuStrip%2A>プロパティ代わりに、-1 の場合、共有行のインデックスを使用し、正しいショートカット メニューを取得しません。  
  
-   インデックス作成を避けるため、<xref:System.Windows.Forms.DataGridViewRow.Cells%2A?displayProperty=nameWithType>コレクション。 セルに直接アクセスすると、その親の行が解除された場合、新しくインスタンス化する<xref:System.Windows.Forms.DataGridViewRow>です。 セルに関連するイベント ハンドラーは、共有が解除する行を引き起こすことがなくセルを操作に使用できるセル プロパティを持つイベント引数オブジェクトを受け取ります。 使用することも、<xref:System.Windows.Forms.DataGridView.CurrentCellAddress%2A>セルに直接アクセスしなくても、現在のセルの行と列のインデックスを取得するプロパティです。  
  
-   セルに基づく選択モードは避けてください。 これらのモードでは、共有が解除する行が発生します。 代わりに、設定、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>プロパティを<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>または<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>です。  
  
-   処理しない、<xref:System.Windows.Forms.DataGridViewRowCollection.CollectionChanged?displayProperty=nameWithType>または<xref:System.Windows.Forms.DataGridView.RowStateChanged?displayProperty=nameWithType>イベント。 これらのイベントには、共有が解除する行が発生します。 また、呼び出す必要はありません、<xref:System.Windows.Forms.DataGridViewRowCollection.OnCollectionChanged%2A?displayProperty=nameWithType>または<xref:System.Windows.Forms.DataGridView.OnRowStateChanged%2A?displayProperty=nameWithType>メソッドで、これらのイベントを発生させます。  
  
-   アクセスしない、<xref:System.Windows.Forms.DataGridView.SelectedCells%2A?displayProperty=nameWithType>コレクションと、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>プロパティの値が<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>、 <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>、 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>、または<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>です。 これにより、すべての選択した行を非共有になります。  
  
-   呼び出す必要はありません、<xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A?displayProperty=nameWithType>メソッドです。 このメソッドには、行を非共有になる可能性があります。  
  
-   呼び出す必要はありません、<xref:System.Windows.Forms.DataGridView.SelectAll%2A?displayProperty=nameWithType>メソッドと、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>プロパティの値が<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>です。 これにより、すべての行を非共有になります。  
  
-   設定しないでください、<xref:System.Windows.Forms.DataGridViewCell.ReadOnly%2A>または<xref:System.Windows.Forms.DataGridViewCell.Selected%2A>にセル プロパティ`false`にその列に対応するプロパティを設定すると`true`です。 これにより、すべての行を非共有になります。  
  
-   アクセスしない、<xref:System.Windows.Forms.DataGridViewRowCollection.List%2A?displayProperty=nameWithType>プロパティです。 これにより、すべての行を非共有になります。  
  
-   呼び出す必要はありません、`Sort(IComparer)`のオーバー ロード、<xref:System.Windows.Forms.DataGridView.Sort%2A>メソッドです。 カスタムの比較演算子の並び替えにすると、すべての行を非共有になります。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 [Windows フォーム DataGridView コントロールでのパフォーマンス チューニング](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [Windows フォーム DataGridView コントロールでの仮想モード](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 [Windows フォーム DataGridView コントロールでのデータ表示モード](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)  
 [Windows フォーム DataGridView コントロールでのセルのスタイル](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [方法: Windows フォーム DataGridView コントロールの既定のセル スタイルを設定する](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 [Windows フォーム DataGridView コントロールのサイズ変更オプション](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)
