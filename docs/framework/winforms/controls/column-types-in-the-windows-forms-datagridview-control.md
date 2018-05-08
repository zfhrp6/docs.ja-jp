---
title: Windows フォーム DataGridView コントロールの列型
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], types
- DataGridView control [Windows Forms], column types
- data grids [Windows Forms], columns
ms.assetid: f0a0a9f1-8757-4bfd-891f-d7d12870dbed
ms.openlocfilehash: 6630323b66265f478151ec80ab8b225c0b653917
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="column-types-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールの列型
<xref:System.Windows.Forms.DataGridView>コントロールは、その情報を表示して情報を変更または追加のユーザーを有効にするいくつかの列の型を使用します。  
  
 バインドすると、<xref:System.Windows.Forms.DataGridView>を制御し、設定、<xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A>プロパティを`true`列は、バインドされたデータ ソースに含まれるデータ型の適切な既定の列型を使用して自動的に生成されます。  
  
 任意の列のクラスのインスタンスを作成およびによって返されるコレクションに追加することができますも、<xref:System.Windows.Forms.DataGridView.Columns%2A>プロパティです。 非バインド列として使用するため、これらのインスタンスを作成するか、手動でバインドすることができます。 手動でバインドされた列は、別の型の列を含む 1 つの種類、自動的に生成された列を置換するときなどに便利です。  
  
 次の表は、さまざまな列のクラスで使用可能な<xref:System.Windows.Forms.DataGridView>コントロール。  
  
|クラス|説明|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|テキスト ベースの値と共に使用します。 数値や文字列にバインドするときに自動的に生成されます。|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|と共に使用<xref:System.Boolean>と<xref:System.Windows.Forms.CheckState>値。 これらの型の値にバインドするときに自動的に生成されます。|  
|<xref:System.Windows.Forms.DataGridViewImageColumn>|イメージを表示するために使用します。 バイト配列にバインドするときに自動的に生成された<xref:System.Drawing.Image>オブジェクト、または<xref:System.Drawing.Icon>オブジェクト。|  
|<xref:System.Windows.Forms.DataGridViewButtonColumn>|セルにボタンを表示するために使用します。 バインドするときに自動的に生成されます。 通常、非バインド列として使用されます。|  
|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|セルのドロップダウン リストを表示するために使用します。 バインドするときに自動的に生成されます。 通常のデータにバインド手動でします。|  
|<xref:System.Windows.Forms.DataGridViewLinkColumn>|セル内のリンクを表示するために使用します。 バインドするときに自動的に生成されます。 通常のデータにバインド手動でします。|  
|カスタム列型|独自の列のクラスを継承して作成することができます、<xref:System.Windows.Forms.DataGridViewColumn>クラスまたはカスタムの外観、動作、またはホストされるコントロールを提供する派生クラスのいずれか。 詳細については、次を参照してください[する方法: セルのカスタマイズとその動作を拡張すると外観が Windows フォーム DataGridView コントロール内の列。](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)|  
  
 これらの列型は、次のセクションで詳しく説明します。  
  
## <a name="datagridviewtextboxcolumn"></a>[Datagridviewtextboxcolumn]  
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn>が数値や文字列などのテキスト ベースの値で使用するための汎用的な列の型。 編集モードで、<xref:System.Windows.Forms.TextBox>セル値を変更するユーザーを有効にすると、アクティブなセルに、コントロールが表示されます。  
  
 セルの値は、表示する文字列に自動的に変換されます。 入力またはユーザーによって変更された値は、適切なデータ型のセル値の作成に自動的に解析されます。 これらの変換をカスタマイズするには処理することにより、<xref:System.Windows.Forms.DataGridView.CellFormatting>と<xref:System.Windows.Forms.DataGridView.CellParsing>のイベント、<xref:System.Windows.Forms.DataGridView>コントロール。  
  
 列のセル値のデータ型がで指定された、<xref:System.Windows.Forms.DataGridViewColumn.ValueType%2A>列のプロパティです。  
  
## <a name="datagridviewcheckboxcolumn"></a>DataGridViewCheckBoxColumn  
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>と共に使用される<xref:System.Boolean>と<xref:System.Windows.Forms.CheckState>値。 <xref:System.Boolean> 値の値に応じて、2 つの状態または 3 つの状態のチェック ボックスとして表示、<xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A>プロパティです。 列をバインドするときに<xref:System.Windows.Forms.CheckState>、値、<xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A>プロパティの値が`true`既定です。  
  
 通常は、チェック ボックス セルの値は記憶域は、その他のデータと同様に、または一括操作を実行するものです。 処理することができる場合、ユーザーは、チェック ボックス セルをクリックして、すぐに応答する場合、<xref:System.Windows.Forms.DataGridView.CellClick>セルの値が更新される前に、イベントでなく、このイベントが発生します。 1 つのオプションは、予期された値を計算する、クリックの時に新しい値を必要がある場合、現在の値に基づいています。 すぐに、変更をコミットし、処理は、別の方法として、<xref:System.Windows.Forms.DataGridView.CellValueChanged>イベントに応答します。 セルがクリックされたときに、変更をコミットするには、処理、<xref:System.Windows.Forms.DataGridView.CurrentCellDirtyStateChanged>イベント。 呼び出しでは、ハンドラーを現在のセルがチェック ボックス セルの場合、<xref:System.Windows.Forms.DataGridView.CommitEdit%2A>メソッドを渡します、<xref:System.Windows.Forms.DataGridViewDataErrorContexts.Commit>値。  
  
## <a name="datagridviewimagecolumn"></a>DataGridViewImageColumn  
 <xref:System.Windows.Forms.DataGridViewImageColumn>イメージを表示するために使用します。 イメージ列がデータ ソースから自動的に設定、バインドされていない列は、手動で設定されますまたはのハンドラーで動的に読み込まれることができます、<xref:System.Windows.Forms.DataGridView.CellFormatting>イベント。  
  
 イメージ列をデータ ソースからの自動作成の動作では、さまざまなイメージ形式でサポートされているすべての形式を含むバイト配列と、<xref:System.Drawing.Image>クラスおよび Microsoft® アクセスと、Northwind サンプル データベースで使用される OLE 画像形式です。  
  
 機能を提供する場合に便利ですが image 列を手動で設定する、 <xref:System.Windows.Forms.DataGridViewButtonColumn>、カスタマイズされた外観でします。 処理することができます、<xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType>イメージ セル内のクリックに応答するイベントです。  
  
 ハンドラーで image 列のセルを設定する、<xref:System.Windows.Forms.DataGridView.CellFormatting>イベントは、計算値や非イメージ形式の値に画像を提供する場合に便利です。 たとえば、する必要があります「リスク」文字列値を持つ列など`"high"`、 `"middle"`、および`"low"`アイコンとして表示します。 または、画像のバイナリ コンテンツではなく読み込む必要があるイメージの場所が含まれる"Image"列がある可能性があります。  
  
## <a name="datagridviewbuttoncolumn"></a>DataGridViewButtonColumn  
 <xref:System.Windows.Forms.DataGridViewButtonColumn>ボタンが含まれているセルの列を表示することができます。 これは、ユーザーが注文を配置することや、別のウィンドウで、子レコードを表示するなど、特定のレコードに対してアクションを実行するための簡単な方法を提供する場合に便利です。  
  
 データ バインド時にボタン列は自動的に生成されません、<xref:System.Windows.Forms.DataGridView>コントロール。 ボタン列を使用するには、手動で作成してによって返されるコレクションに追加する必要があります、<xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>プロパティです。  
  
 処理することによりユーザーがクリックしたボタン セル内に応答して、<xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType>イベント。  
  
## <a name="datagridviewcomboboxcolumn"></a>DataGridViewComboBoxColumn  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>、ドロップダウン リスト ボックスが含まれているセルの列を表示することができます。 これは、データ フィールドのエントリ、Northwind サンプル データベースの Products テーブルのカテゴリ列などの特定の値を含めることができるのみ便利です。  
  
 設定と同じ方法ですべてのセルの使用、ドロップダウン リストに表示することができます、<xref:System.Windows.Forms.ComboBox>によって返されるコレクションを手動でいずれかのドロップダウン リスト、<xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A>プロパティ、または使用して、データ ソースにバインドすることによって、 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>、 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>、および<xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>プロパティです。 詳細については、次を参照してください。[コンボ ボックス コントロール](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)です。  
  
 によって使用されるデータ ソースに実際のセル値をバインドすることができます、<xref:System.Windows.Forms.DataGridView>コントロールを設定して、<xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A>のプロパティ、<xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType>です。  
  
 データ バインド時に、コンボ ボックスの列が自動的に生成されませんが、<xref:System.Windows.Forms.DataGridView>コントロール。 コンボ ボックスの列を使用するには、手動で作成してによって返されるコレクションに追加する必要があります、<xref:System.Windows.Forms.DataGridView.Columns%2A>プロパティです。  
  
## <a name="datagridviewlinkcolumn"></a>DataGridViewLinkColumn  
 <xref:System.Windows.Forms.DataGridViewLinkColumn>ハイパーリンクが含まれているセルの列を表示することができます。 これは、データ ソースまたは子レコードを含むウィンドウを開くなどの特殊な動作のボタン列の代わりとしての URL 値に役立ちます。  
  
 データ バインド時に、リンク列が自動的に生成されませんが、<xref:System.Windows.Forms.DataGridView>コントロール。 リンク列を使用するには、手動で作成してによって返されるコレクションに追加する必要があります、<xref:System.Windows.Forms.DataGridView.Columns%2A>プロパティです。  
  
 処理することによりユーザーへのリンクがクリックに応答して、<xref:System.Windows.Forms.DataGridView.CellContentClick>イベント。 このイベントは、別個のもの、<xref:System.Windows.Forms.DataGridView.CellClick>と<xref:System.Windows.Forms.DataGridView.CellMouseClick>イベントで、ユーザーがセルの任意の場所をクリックしたときに発生します。  
  
 <xref:System.Windows.Forms.DataGridViewLinkColumn>クラスでは、いくつかのプロパティを提供する前に、実行時と後のリンクの外観を変更するためをクリックします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewButtonColumn>  
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewImageColumn>  
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewLinkColumn>  
 [DataGridView コントロール](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [方法: Windows フォーム DataGridView コントロールのセルにイメージを表示する](../../../../docs/framework/winforms/controls/how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)  
 [方法: Windows フォーム DataGridView コントロールのイメージ列を操作する](../../../../docs/framework/winforms/controls/how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)  
 [Windows フォーム DataGridView コントロールのカスタマイズ](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
