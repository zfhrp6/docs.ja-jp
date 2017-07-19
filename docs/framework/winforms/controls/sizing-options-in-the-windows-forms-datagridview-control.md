---
title: "Windows フォーム DataGridView コントロールのサイズ変更オプション | Microsoft Docs"
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
  - "データ グリッド, 列のサイズ変更"
  - "データ グリッド, 行のサイズ変更"
  - "データ グリッド, サイズ変更オプション"
  - "DataGridView コントロール [Windows フォーム], 列のサイズ変更"
  - "DataGridView コントロール [Windows フォーム], 行のサイズ変更"
  - "DataGridView コントロール [Windows フォーム], サイズ変更オプション"
ms.assetid: a5620a9c-0d06-41e3-8934-c25ddb16c9e6
caps.latest.revision: 29
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 29
---
# Windows フォーム DataGridView コントロールのサイズ変更オプション
<xref:System.Windows.Forms.DataGridView> の行、列、およびヘッダーのサイズは、さまざまな要因によって変更されることがあります。  次の表にその要因を示します。  
  
|要因|Description|  
|--------|-----------------|  
|ユーザーによるサイズ変更|ユーザーは、行、列、またはヘッダーの区分線をドラッグまたはダブルクリックすることで、サイズを調整できます。|  
|コントロールのサイズ変更|列フィル モードでは、コントロールが親フォームにドッキングしたり、ユーザーがフォームのサイズを変更したりすることでコントロールの幅が変わると、列幅も変更されます。|  
|セルの値の変更|内容に基づいて自動的にサイズ変更するモードでは、新しい表示値に合わせてサイズが変更されます。|  
|メソッドの呼び出し|プログラムによって内容に基づくサイズ変更を行う場合、メソッド呼び出し時のセルの値に合わせてサイズが調整されます。|  
|プロパティの設定|高さと幅に特定の値を設定することもできます。|  
  
 既定では、ユーザーによるサイズ変更は有効、自動サイズ変更は無効になっており、列幅よりも幅が大きいセル値は欠けた状態で表示されます。  
  
 次の表に、既定の動作を調整する場合や、特定の目的に合わせて各サイズ変更オプションを使用する場合のシナリオを示します。  
  
|シナリオ|実装|  
|----------|--------|  
|列フィル モードを使用して、水平スクロール バーが表示されないようにコントロールの幅全体に比較的少数の列をすべて表示し、同程度のサイズのデータを表示する場合。|<xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> プロパティを <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode> に設定します。|  
|列フィル モードを使用して、さまざまなサイズの表示値を表示する場合。|<xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> プロパティを <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode> に設定します。  列の <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> プロパティを設定するか、コントロールにデータが入力された後でコントロールの <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> メソッドを呼び出して、相対的な列幅を初期化します。|  
|列フィル モードを使用して、さまざまな重要度の値を表示する場合。|<xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> プロパティを <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode> に設定します。  データの一部を常に表示する必要がある列の <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> に大きい値を設定するか、特定の列にフィル モード以外のサイズ変更オプションを使用します。|  
|列フィル モードを使用して、コントロールの背景色が表示されないようにする場合。|最終列の <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> プロパティを <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode> に設定し、それ以外の列には他のサイズ変更オプションを使用します。  他の列が使用可能な領域を大量に使用している場合、最終列の <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> プロパティを設定します。|  
|アイコンや ID などの固定幅の列を表示する場合。|その列の <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> を <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode> に、<xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> を <xref:System.Windows.Forms.DataGridViewTriState> に設定します。  <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> プロパティを設定するか、コントロールにデータが入力された後でコントロールの <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A> メソッドを呼び出して、列の幅を初期化します。|  
|セルの内容が変更されるたびに、表示が欠けず、スペースが最も有効に使用されるように、サイズを自動的に調整する場合。|自動サイズ変更のプロパティに、内容に基づくサイズ変更モードを表す値を設定します。  大量のデータを処理する場合にパフォーマンス低下を避けるには、表示されている行のみを計算するサイズ変更モードを使用します。|  
|多数の行を処理する際のパフォーマンス低下を避けるために、表示されている行の値に合わせてサイズを調整する場合。|自動サイズ変更またはプログラムによるサイズ変更を指定する、適切なサイズ変更モード列挙値を使用します。  スクロール操作で新しく表示された行の値に合わせてサイズを調整するには、<xref:System.Windows.Forms.DataGridView.Scroll> イベント ハンドラーでサイズ変更メソッドを呼び出します。  ユーザーのダブルクリックによるサイズ変更を、表示されている行の値のみに合わせて新しいサイズが決定されるようにカスタマイズするには、<xref:System.Windows.Forms.DataGridView.RowDividerDoubleClick> イベント ハンドラーまたは <xref:System.Windows.Forms.DataGridView.ColumnDividerDoubleClick> イベント ハンドラーでサイズ変更メソッドを呼び出します。|  
|パフォーマンス低下を避けるため、またはユーザーによるサイズ変更を有効にするために、セルの内容に合わせたサイズ調整を特定の場合に限定する場合。|イベント ハンドラーで、内容に基づくサイズ変更のメソッドを呼び出します。  たとえば、<xref:System.Windows.Forms.DataGridView.DataBindingComplete> イベントを使用して、バインディング後にサイズを初期化し、<xref:System.Windows.Forms.DataGridView.CellValidated> を処理したり、<xref:System.Windows.Forms.DataGridView.CellValueChanged> イベントを使用して、ユーザーによる編集やバインドされたデータ ソースの変更に対応してサイズを調整したりします。|  
|複数行にわたる内容を持つセルが含まれる行の高さを調整する場合。|列幅を段落テキストの表示に適切なサイズにし、行の高さを内容に基づく自動サイズ変更またはプログラムによるサイズ変更を使用して調整します。  また、複数行の内容を含むセルは、セル スタイル <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> に値 <xref:System.Windows.Forms.DataGridViewTriState> を使用して表示します。<br /><br /> 通常は、行の高さを調整する前に、列の自動サイズ変更モードを使用して列幅を操作するか、列幅に特定の値を設定します。|  
  
## マウス操作によるサイズ変更  
 既定では、ユーザーは、セルの値に基づく自動サイズ変更モードを使用していない行、列、およびヘッダーのサイズを変更できます。  列フィル モードなど、それ以外のモードの場合にユーザーがサイズ変更できないようにするには、<xref:System.Windows.Forms.DataGridView> の次の 1 つまたは複数のプロパティを設定します。  
  
-   <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
 また、特定の行または列の <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> プロパティを設定して、それらの行または列をユーザーがサイズ変更できないようにすることもできます。  既定では、<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> プロパティの値は、列の <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A> プロパティの値、および行の <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A> プロパティの値に基づいています。  ただし、<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> を <xref:System.Windows.Forms.DataGridViewTriState> または <xref:System.Windows.Forms.DataGridViewTriState> に明示的に設定すると、その行または列のコントロール値は指定した値でオーバーライドされます。  継承の状態に戻すには、<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> を <xref:System.Windows.Forms.DataGridViewTriState> に設定します。  
  
 <xref:System.Windows.Forms.DataGridViewTriState> により、値は継承された状態に戻るので、その行または列が <xref:System.Windows.Forms.DataGridView> コントロールに追加されていない場合を除き、<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> プロパティの値として <xref:System.Windows.Forms.DataGridViewTriState> が返されることはありません。  行または列の <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> プロパティが継承されているかどうかを調べる必要がある場合は、<xref:System.Windows.Forms.DataGridViewElement.State%2A> プロパティを確認します。  <xref:System.Windows.Forms.DataGridViewElement.State%2A> 値に <xref:System.Windows.Forms.DataGridViewElementStates> フラグが含まれている場合、<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> プロパティの値は継承されていません。  
  
## 自動サイズ変更  
 <xref:System.Windows.Forms.DataGridView> コントロールの自動サイズ変更には、列フィル モードと、内容に基づく自動サイズ変更の 2 種類があります。  
  
 列フィル モードでは、コントロール内のすべての表示可能列が、コントロールの表示領域の幅を埋めるように表示されます。  このモードの詳細については、「[Windows フォーム DataGridView コントロールの列フィル モード](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
 また、セルの内容に合わせて自動的にサイズ調整されるように、行、列、およびヘッダーを設定することもできます。  この場合は、セルの内容が変わるたびにサイズ調整が発生します。  
  
> [!NOTE]
>  仮想モードを使用してセルの値をカスタム データ キャッシュに格納する場合、自動サイズ変更は、セルの値を編集すると発生しますが、キャッシュされた値を <xref:System.Windows.Forms.DataGridView.CellValuePushed> イベント ハンドラーの外部で変更しても発生しません。  この場合、<xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> メソッドを呼び出すことにより、コントロールがセルの表示を更新し、現在の自動サイズ変更モードを適用するように強制できます。  
  
 内容に基づく自動サイズ変更が 1 次元のみ有効 \(行のみ有効で列は無効、または列のみ有効で行は無効\) な状態でも、<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> が有効だと、無効な側の次元が変更された場合にもサイズ調整が発生します。  たとえば、自動サイズ変更が行については有効で列については無効な場合に、<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> が有効だと、ユーザーが列の区分線をドラッグして列幅を変更すると、セルの内容が完全に表示されるように行の高さが自動的に調整されます。  
  
 内容に基づくサイズ変更を行と列の両方について設定し、<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> を有効にした場合は、セルの内容が変わるたびに <xref:System.Windows.Forms.DataGridView> コントロールで自動的にサイズが調整され、新しいサイズの計算時には最適なセルの高さと幅の比率が使用されます。  
  
 コントロールの値をオーバーライドしないでヘッダー、行、および列のサイズ変更モードを設定するには、次のいずれかの <xref:System.Windows.Forms.DataGridView> プロパティを設定します。  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A>  
  
 特定の列についてコントロールの列サイズ変更モードをオーバーライドするには、その列の <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> プロパティを <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode> 以外の値に設定します。  列のサイズ変更モードは、実際にはその列の <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> プロパティによって決まります。  このプロパティの値は、列の <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> プロパティの値に基づきますが、これが <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode> の場合にはコントロールの <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> 値が継承されます。  
  
 内容に基づく自動サイズ変更の使用は、大量のデータを処理する場合には注意が必要です。  パフォーマンス低下を避けるには、コントロール内のすべての行を分析してサイズを計算する自動サイズ変更モードではなく、表示されている行のみに基づく自動サイズ変更モードを使用します。  パフォーマンスを最大にするには、プログラムによるサイズ変更を使用して、新しいデータが読み込まれた直後などのタイミングを指定してサイズ変更してください。  
  
 内容に基づく自動サイズ変更モードは、行または列の <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> プロパティ、あるいはコントロールの <xref:System.Windows.Forms.DataGridView.RowHeadersVisible%2A> プロパティまたは <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> プロパティを `false` に設定して非表示にしている行、列、またはヘッダーには機能しません。  たとえば、大きいセル値に合わせて列のサイズが自動的に変更された後でその列を非表示にすると、その大きいセル値を含む行が削除されても非表示列のサイズは変わりません。  表示と非表示を切り替えても自動サイズ変更は発生しません。したがって、列の <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> プロパティを `true` に戻しても、現在の内容に基づくサイズの再計算は行われません。  
  
 プログラムによって内容に基づくサイズ変更を行う場合、その変更は、表示されるかどうかに関係なく、行、列、およびヘッダーに作用します。  
  
## プログラムによるサイズ変更  
 自動サイズ変更が無効の場合、プログラムで次のプロパティを使用して、行、列、またはヘッダーの幅や高さを厳密に設定できます。  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=fullName>  
  
 また、プログラムで次のメソッドを使用して、行、列、およびヘッダーのサイズをその内容に合わせて変更できます。  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A>  
  
 これらのメソッドは、行、列、またはヘッダーのサイズを継続的に設定するのではなく、そのとき 1 度だけ変更します。  新しいサイズは、セルの内容すべてが欠けることなく表示されるように自動的に計算されます。  ただし、<xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> プロパティの値が <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode> の列のサイズをプログラムによって変更すると、内容に基づいて計算された幅を使用して列の <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> プロパティの値の比率が調整され、実際の列幅は、その新しい比率に応じてすべての列がコントロールの表示可能領域に収まるように計算されます。  
  
 プログラムによるサイズ変更は、頻繁なサイズ変更によるパフォーマンス低下を避けるのに役立ちます。  また、ユーザーによる行、列、およびヘッダーのサイズ変更が可能な場合や、列フィル モードを使用する場合の初期サイズを決めるのにも役立ちます。  
  
 通常、プログラムでは、特定のタイミングでサイズ変更のメソッドを呼び出します。  たとえば、データ読み込み直後にプログラムによってすべての列のサイズを変更したり、特定のセルの値が変更された後にプログラムによって行のサイズを変更したりします。  
  
## 内容に基づくサイズ変更動作のカスタマイズ  
 派生した <xref:System.Windows.Forms.DataGridView> のセル、行、および列の種類を操作する場合、サイズ変更の動作は、派生した <xref:System.Windows.Forms.DataGridView> コントロールの <xref:System.Windows.Forms.DataGridViewCell.GetPreferredSize%2A?displayProperty=fullName>、<xref:System.Windows.Forms.DataGridViewRow.GetPreferredHeight%2A?displayProperty=fullName>、または <xref:System.Windows.Forms.DataGridViewColumn.GetPreferredWidth%2A?displayProperty=fullName> の各メソッドをオーバーライドすることによって、またはコントロールのサイズ変更のプロテクト メソッドのオーバーロードを呼び出すことによって、カスタマイズできます。  サイズ変更のプロテクト メソッドのオーバーロードは、組み合わせて使用することでセルの高さと幅の最適な比率が得られるようにデザインされており、これによって極端に長いまたは高いセルが作成されることを回避できます。  たとえば、<xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A> メソッドの `AutoResizeRows(DataGridViewAutoSizeRowsMode,Boolean)` オーバーロードを呼び出し、<xref:System.Boolean> パラメーターに `false` を渡すと、このオーバーロードはその行のセルの最適な高さと幅を計算しますが、行の高さだけを調整します。  計算された最適なサイズに列幅を調整するには、この後で <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> メソッドを呼び出す必要があります。  
  
## 内容に基づくサイズ変更のオプション  
 サイズ変更に関するプロパティとメソッドで使用する列挙体には、内容に基づくサイズ変更と同様の値が使用されます。  これらの値を使用して、適切なサイズを計算する際にどのセルを使用するかを制限できます。  サイズ変更の列挙体では、表示されているセルを表す名前の値を指定することで、サイズを計算する基準を表示されている行のセルに限定できます。  大量の行を処理する場合には、行を除外することはパフォーマンス低下を避けるのに役立ちます。  また、ヘッダーのセルまたはヘッダー以外のセルの値のみに計算を限定することもできます。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>   
 <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>   
 <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>   
 [Windows フォーム DataGridView コントロール内の列と行のサイズ変更](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールの列フィル モード](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md)   
 [方法 : Windows フォーム DataGridView コントロールのサイズ変更モードを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)