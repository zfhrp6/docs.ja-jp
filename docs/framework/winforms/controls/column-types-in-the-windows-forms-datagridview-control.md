---
title: "Windows フォーム DataGridView コントロールの列型 | Microsoft Docs"
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
  - "列 [Windows フォーム], 種類"
  - "データ グリッド, 列"
  - "DataGridView コントロール [Windows フォーム], 列の型"
ms.assetid: f0a0a9f1-8757-4bfd-891f-d7d12870dbed
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Windows フォーム DataGridView コントロールの列型
<xref:System.Windows.Forms.DataGridView> コントロールでは、情報を表示し、ユーザーが情報を変更したり追加したりできるようにさまざまな列型を使用します。  
  
 <xref:System.Windows.Forms.DataGridView> コントロールをバインドし、<xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> プロパティを `true` に設定すると、バインドしたデータ ソースに含まれるデータ型に見合った既定の列型を使用して、列が自動的に生成されます。  
  
 また、任意の列クラスのインスタンスを独自に作成し、<xref:System.Windows.Forms.DataGridView.Columns%2A> プロパティによって返されたコレクションに追加することもできます。  作成したこれらのインスタンスは、非バインド列として使用することも、手動でバインドすることもできます。  手動バインド列は、たとえば、自動生成されたある型の列を、別の型の列に置き換える場合に便利です。  
  
 <xref:System.Windows.Forms.DataGridView> コントロールで使用できる列クラスの一覧を次の表に示します。  
  
|Class|Description|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|テキスト ベースの値で使用されます。  数値や文字列にバインドすると自動的に生成されます。|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|<xref:System.Boolean> 値と <xref:System.Windows.Forms.CheckState> 値で使用されます。  これらの型の値にバインドすると自動的に生成されます。|  
|<xref:System.Windows.Forms.DataGridViewImageColumn>|イメージの表示に使用されます。  バイト配列、<xref:System.Drawing.Image> オブジェクト、または <xref:System.Drawing.Icon> オブジェクトにバインドすると自動的に生成されます。|  
|<xref:System.Windows.Forms.DataGridViewButtonColumn>|セルにボタンを表示するために使用されます。  バインド時に自動的に生成されません。  通常、非バインド列として使用されます。|  
|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|セルにドロップダウン リストを表示するために使用されます。  バインド時に自動的に生成されません。  通常、手動でデータ バインドされます。|  
|<xref:System.Windows.Forms.DataGridViewLinkColumn>|セルにリンクを表示するために使用されます。  バインド時に自動的に生成されません。  通常、手動でデータ バインドされます。|  
|カスタム列型|<xref:System.Windows.Forms.DataGridViewColumn> クラスやその派生クラスを継承して独自の列クラスを作成すると、独自の外観や動作、またはホストされるコントロールを提供できます。  詳細については、「[方法 : Windows フォーム DataGridView コントロールのセルと列を、それぞれの動作と外観を拡張してカスタマイズする](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)」を参照してください。|  
  
 これらの列型について、以下のセクションで詳しく説明します。  
  
## DataGridViewTextBoxColumn  
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn> は、数値や文字列などのテキスト ベースの値で使用する汎用の列型です。  編集モードでは、<xref:System.Windows.Forms.TextBox> コントロールがアクティブなセルに表示されるので、ユーザーはセル値を変更できます。  
  
 セル値は、表示用の文字列に自動的に変換されます。  ユーザーが入力または変更した値は自動的に解析され、適切なデータ型のセル値が生成されます。  この変換は、<xref:System.Windows.Forms.DataGridView> コントロールの <xref:System.Windows.Forms.DataGridView.CellFormatting> イベントと <xref:System.Windows.Forms.DataGridView.CellParsing> イベントを処理することでカスタマイズできます。  
  
 列のセル値のデータ型は、列の <xref:System.Windows.Forms.DataGridViewColumn.ValueType%2A> プロパティで指定されます。  
  
## DataGridViewCheckBoxColumn  
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> は、<xref:System.Boolean> 値と <xref:System.Windows.Forms.CheckState> 値で使用されます。  <xref:System.Boolean> 値は、<xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> プロパティの値に応じて、2 ステートまたは 3 ステート チェック ボックスとして表示されます。  列が <xref:System.Windows.Forms.CheckState> 値にバインドされると、<xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> プロパティ値は既定で `true` になります。  
  
 通常、チェック ボックス セル値は、他のデータと同様にストレージ用として、または一括操作を実行するために使用されます。  ユーザーがチェック ボックス セルをクリックしたときに直ちに応答する場合は、<xref:System.Windows.Forms.DataGridView.CellClick> イベントを処理しますが、このイベントはセル値が更新される前に発生します。  クリック時に新しい値が必要な場合は、現在の値を基に期待される値を計算するという方法が考えられます。  また別の方法として、変更を直ちにコミットし、<xref:System.Windows.Forms.DataGridView.CellValueChanged> イベントを処理してその変更に応答することも考えられます。  セルがクリックされたときに変更をコミットするには、<xref:System.Windows.Forms.DataGridView.CurrentCellDirtyStateChanged> イベントを処理する必要があります。  このハンドラーでは、現在のセルがチェック ボックス セルの場合、<xref:System.Windows.Forms.DataGridView.CommitEdit%2A> メソッドを呼び出し、<xref:System.Windows.Forms.DataGridViewDataErrorContexts> 値を渡します。  
  
## DataGridViewImageColumn  
 <xref:System.Windows.Forms.DataGridViewImageColumn> は、イメージの表示に使用されます。  イメージ列は、データ ソースから自動的に設定でき、非バインド列の場合は手動で設定できます。また <xref:System.Windows.Forms.DataGridView.CellFormatting> イベントのハンドラーで動的に設定することもできます。  
  
 イメージ列をデータ ソースから自動的に設定する場合は、<xref:System.Drawing.Image> クラスでサポートされるすべての形式と、Microsoft® Access や Northwind サンプル データベースで使用される OLE ピクチャ形式を含む各種イメージ形式のバイト配列を使用できます。  
  
 イメージ列の手動設定は、<xref:System.Windows.Forms.DataGridViewButtonColumn> の機能を独自の外観で提供する場合に役立ちます。  <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=fullName> イベントを処理することにより、イメージ セル内のクリックに応答できます。  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting> イベントのハンドラーでのイメージ列のセルの設定は、計算値やイメージ形式以外の値にイメージを提供する場合に役立ちます。  たとえば、"Risk" 列には、アイコンとして表示する `"high"`、`"middle"`、`"low"` などの文字列型の値を設定できます。  また、"Image" 列には、イメージのバイナリ コンテンツではなく、読み込む必要があるイメージの場所を格納できます。  
  
## DataGridViewButtonColumn  
 <xref:System.Windows.Forms.DataGridViewButtonColumn> を使用すると、ボタンを含むセルの列を表示できます。  これは、発注を行ったり別個のウィンドウに子レコードを表示したりという操作を、ユーザーが特定のレコードで簡単に実行できるようにする場合に便利です。  
  
 ボタン列は、<xref:System.Windows.Forms.DataGridView> コントロールをデータ バインディングしたときに自動的に生成されるわけではありません。  ボタン列を使用するには、ボタン列を手動で作成し、<xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=fullName> プロパティによって返されたコレクションに追加する必要があります。  
  
 ボタン セル内のユーザー クリックに応答するには、<xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=fullName> イベントを処理します。  
  
## DataGridViewComboBoxColumn  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn> を使用すると、ドロップダウン リスト ボックスを含むセルの列を表示できます。  これは、Northwind サンプル データベースの Products テーブルの Category 列など、特定の値しか入力できないフィールドでのデータ入力に便利です。  
  
 すべてのセルで共通に使用するドロップダウン リストは、<xref:System.Windows.Forms.ComboBox> ドロップダウン リストの場合と同様に、<xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> プロパティによって返されたコレクションを通じて手動で設定することも、<xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> プロパティ、<xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> プロパティ、および <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> プロパティを通じてデータ ソースにバインドして設定することもできます。  詳細については、「[ComboBox コントロール](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)」を参照してください。  
  
 <xref:System.Windows.Forms.DataGridView> コントロールによって使用されるデータ ソースに実際のセル値をバインドするには、<xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=fullName> の <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> プロパティを設定します。  
  
 コンボ ボックス列は、<xref:System.Windows.Forms.DataGridView> コントロールをデータ バインディングしたときに自動的に生成されるわけではありません。  コンボ ボックス列を使用するには、コンボ ボックス列を手動で作成し、<xref:System.Windows.Forms.DataGridView.Columns%2A> プロパティによって返されたコレクションに追加する必要があります。  
  
## DataGridViewLinkColumn  
 <xref:System.Windows.Forms.DataGridViewLinkColumn> を使用すると、ハイパーリンクを含むセルの列を表示できます。  これは、データ ソース内の URL 値を表示するのに便利です。またボタン列の代わりに使用して、子レコードを表示するウィンドウを開くなど、特別な動作を提供することもできます。  
  
 リンク列は、<xref:System.Windows.Forms.DataGridView> コントロールをデータ バインディングしたときに自動的に生成されるわけではありません。  リンク列を使用するには、リンク列を手動で作成し、<xref:System.Windows.Forms.DataGridView.Columns%2A> プロパティによって返されたコレクションに追加する必要があります。  
  
 ユーザーによるリンクのクリックに応答するには、<xref:System.Windows.Forms.DataGridView.CellContentClick> イベントを処理します。  このイベントは、ユーザーがセル内の場所をクリックしたときに発生する <xref:System.Windows.Forms.DataGridView.CellClick> イベントや <xref:System.Windows.Forms.DataGridView.CellMouseClick> イベントとは別です。  
  
 <xref:System.Windows.Forms.DataGridViewLinkColumn> クラスには、クリックの前後およびクリック時のリンクの外観を変更するプロパティが用意されています。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewColumn>   
 <xref:System.Windows.Forms.DataGridViewButtonColumn>   
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>   
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>   
 <xref:System.Windows.Forms.DataGridViewImageColumn>   
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn>   
 <xref:System.Windows.Forms.DataGridViewLinkColumn>   
 [DataGridView コントロール](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)   
 [方法 : Windows フォーム DataGridView コントロールのセルにイメージを表示する](../../../../docs/framework/winforms/controls/how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)   
 [方法 : Windows フォーム DataGridView コントロールのイメージ列を操作する](../../../../docs/framework/winforms/controls/how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールのカスタマイズ](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)