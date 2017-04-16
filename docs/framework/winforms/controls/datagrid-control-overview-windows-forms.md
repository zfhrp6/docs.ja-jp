---
title: "DataGrid コントロールの概要 (Windows フォーム) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataGrid"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "DataGrid コントロールにバインド データセット [Windows フォーム]"
  - "データ バインド、DataGrid コントロール"
  - "DataGrid コントロールの列 [Windows フォーム]"
  - "DataGrid コントロールにバインド データ ソース"
  - "DataGrid コントロールにバインド テーブル [Windows フォーム]"
  - "データ バインディングの DataGrid コントロール [Windows フォーム]"
  - "DataGrid コントロールの概要の DataGrid コントロール [Windows フォーム]"
  - "親テーブル (DataGrid コントロールの)"
  - "DataGrid コントロールに表示するテーブル [Windows フォーム]"
  - "データ グリッドの概要のデータ グリッド"
  - "複数のテーブル (DataGrid コントロールの)"
  - "データ [Windows フォーム] を再度並べ替える"
  - "データ [Windows フォーム] 内の移動"
  - "DataGrid コントロールのバインドされたコントロール"
  - "DataGrid のデータ バインド コントロール"
  - "親テーブルからの移動 (DataGrid での)"
  - "子テーブル、DataGrid コントロール"
ms.assetid: 85604bce-bc03-49d9-9030-dda8896c44b1
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# DataGrid コントロールの概要 (Windows フォーム)
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView>コントロールの置換し、する機能を追加、 <xref:System.Windows.Forms.DataGrid>コントロール。 ただし、、 <xref:System.Windows.Forms.DataGrid>を選択した場合、下位互換性と将来の使用の両方のコントロールが保持されています。 詳細については、次を参照してください。[の相違点の間で Windows フォームの DataGridView コントロールと DataGrid コントロール](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)します。  
  
 Windows フォーム<xref:System.Windows.Forms.DataGrid>コントロールは、一連の行と列のデータを表示します。 最も簡単なケースは、リレーションシップを含まない&1; つのテーブルを持つデータ ソースにグリッドがバインドされている場合です。 その場合は、スプレッドシートのように、単純な行と列でデータが表示されます。 その他のコントロールへのデータ バインディングの詳細については、次を参照してください。[データ連結と Windows フォーム](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)します。  
  
 場合、 <xref:System.Windows.Forms.DataGrid>複数のデータにバインドの関連するテーブルと、グリッドでナビゲーションが有効な場合、グリッドの各行にエキスパンダーが表示されます。 展開コントロールでは、ユーザーは、親テーブルから子テーブルに移動できます。 ノードをクリックすると子テーブルが表示され、[戻る] ボタンをクリックすると、元の親テーブルが表示されます。 この方法では、グリッドはテーブル間の階層リレーションシップを表示します。  
  
 次のスクリーン ショットは、複数のテーブルのデータにバインドされた DataGrid を示しています。  
  
 ![複数のテーブルを持つデータにバインドされた DataGrid](../../../../docs/framework/winforms/controls/media/vbcontrol1.gif "vbControl1")  
複数のテーブルを持つデータにバインドされた DataGrid  
  
 <xref:System.Windows.Forms.DataGrid>データセット、関連テーブル、および豊富な書式設定および編集機能間のナビゲーションのユーザー インターフェイスを提供することができます。  
  
 データの表示と操作は別の機能です。コントロールはユーザー インターフェイスを処理し、データの更新は Windows フォームのデータ バインディング アーキテクチャおよび [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] データ プロバイダーによって処理されます。 このため、同じデータ ソースにバインドされる複数のコントロールが同期状態を保ちます。  
  
> [!NOTE]
>  Visual Basic 6.0 の DataGrid コントロールに慣れている場合は、Windows フォームにはいくつか大きな違いが表示されます<xref:System.Windows.Forms.DataGrid>コントロールです。  
  
 グリッドがバインドされている場合、<xref:System.Data.DataSet>列と行が自動的に作成、書式設定、および入力します。 詳細については、「 [Data Binding and Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)」を参照してください。 次の世代の<xref:System.Windows.Forms.DataGrid>コントロールすることができます追加、削除、再配置、および、ニーズに応じて列と行の書式を設定します。  
  
## <a name="binding-data-to-the-control"></a>コントロールへのデータのバインド  
 <xref:System.Windows.Forms.DataGrid>コントロールが機能するを使用してデータ ソースにバインドされている必要があります、<xref:System.Windows.Forms.DataGrid.DataSource%2A>と<xref:System.Windows.Forms.DataGrid.DataMember%2A>デザイン時にプロパティまたは<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>メソッド実行時にします。 このバインディングの<xref:System.Windows.Forms.DataGrid>をインスタンス化されたデータ ソース オブジェクトになど、<xref:System.Data.DataSet>または<xref:System.Data.DataTable>)。 <xref:System.Windows.Forms.DataGrid>コントロールは、データ上で実行されるアクションの結果を表示します。 ほとんどのデータに固有の動作はによって実行されます、 <xref:System.Windows.Forms.DataGrid>が代わりに、データ ソースをします。  
  
 バインドされたデータセット内のデータが任意のメカニズムにより更新された場合、 <xref:System.Windows.Forms.DataGrid>コントロールが変更を反映します。 データ グリッド、表のスタイル、および列のスタイルがある場合、`ReadOnly`プロパティに設定`false`で、データセット内のデータを更新できます、 <xref:System.Windows.Forms.DataGrid>コントロールです。  
  
 1 つのテーブルを表示できる、 <xref:System.Windows.Forms.DataGrid>一度にします。 ユーザーに表示するテーブルを選択して、関連するテーブルの間で移動できる親子リレーションシップを定義する場合のテーブル間の<xref:System.Windows.Forms.DataGrid>コントロールです。 バインドについては、 <xref:System.Windows.Forms.DataGrid>への制御、[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]デザイン時または実行時に、データ ソースを参照してください[方法: Windows フォーム DataGrid コントロールをデータ ソースにバインド](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)します。  
  
 有効なデータ ソースに、 <xref:System.Windows.Forms.DataGrid>が含まれます。  
  
-   <xref:System.Data.DataTable>クラス  
  
-   <xref:System.Data.DataView>クラス  
  
-   <xref:System.Data.DataSet>クラス  
  
-   <xref:System.Data.DataViewManager>クラス  
  
 ソースがデータセットの場合、データセットは、フォーム内のオブジェクト、または XML Web サービスによってフォームに渡されるオブジェクトの可能性があります。 型指定されたか、型指定されていないデータセットにバインドできます。  
  
 バインドすることも、 <xref:System.Windows.Forms.DataGrid>配列内の要素など、構造内のオブジェクトのパブリック プロパティを公開する場合は、追加の構造を制御します。 グリッドには、構造内の要素のすべてのパブリック プロパティが表示されます。 バインドする場合など、 <xref:System.Windows.Forms.DataGrid>コントロール顧客の配列をオブジェクトに、これらの顧客オブジェクトのすべてのパブリック プロパティをグリッドが表示されます。 場合によっては、構造にバインドすることができますが、結果としてバインドされている構造が、実際のアプリケーションを持たない可能性があることを意味します。 たとえば、整数の配列にバインドできますが、`Integer` データ型はパブリック プロパティをサポートしないため、グリッドがすべてのデータを表示できません。  
  
 要素がパブリック プロパティを公開する場合は、次の構造にバインドできます。  
  
-   実装する任意のコンポーネント、 <xref:System.Collections.IList>インターフェイスです。 これには&1; 次元の配列が含まれます。  
  
-   実装する任意のコンポーネント、 <xref:System.ComponentModel.IListSource>インターフェイスです。  
  
-   実装する任意のコンポーネント、 <xref:System.ComponentModel.IBindingList>インターフェイスです。  
  
 使用できるデータ ソースの詳細については、次を参照してください。 [Windows フォームがサポートされるデータ ソース](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)します。  
  
## <a name="grid-display"></a>グリッドの表示  
 一般的な用途、 <xref:System.Windows.Forms.DataGrid>コントロールでは、データセットのデータの&1; つのテーブルを表示します。 ただし、関連テーブルを含む複数のテーブルを表示するためにコントロールを使用できます。 グリッドの表示は、データ ソースに応じて自動的に調整されます。 さまざまな構成で表示される内容を次の表に示します。  
  
|データ セットの内容|表示される内容|  
|--------------------------|-----------------------|  
|1 つのテーブル。|テーブルがグリッドに表示されます。|  
|複数のテーブル。|グリッドに、ユーザーが移動して表示するテーブルを検索できるツリー ビューを表示できます。|  
|複数の関連テーブル。|グリッドに、テーブルを選択するツリー ビューを表示でき、グリッドに親テーブルを表示するよう指定することもできます。 親テーブル内のレコードでは、ユーザーが関連する子の行に移動できます。|  
  
> [!NOTE]
>  使用して、データセット内のテーブルが関連する、 <xref:System.Data.DataRelation>します。  参照してください[データセットの HYPERLINK"http://msdn.microsoft.com/library/dbwcse3d(v=vs.110)"リレーションシップ](http://msdn.microsoft.com/library/dbwcse3d\(v=vs.110\))または[データセットのリレーションシップ](http://msdn.microsoft.com/library/dbwcse3d\(v=vs.120\))します。  
  
 ときに、 <xref:System.Windows.Forms.DataGrid>コントロールがテーブルに表示され、 <xref:System.Windows.Forms.DataGrid.AllowSorting%2A>にプロパティが設定されている`true`データは、列見出しをクリックして再度並べ替えることができます。 ユーザーは行の追加やセルの編集も実行できます。  
  
 一連のテーブル間のリレーションシップは、ナビゲーションの親/子構造体を使用してユーザーに表示されます。 親テーブルは最高レベルのデータ、および子テーブルは、親テーブルの個別の一覧から派生した個々 のデータ テーブルです。 展開コントロールは、子テーブルを含む各親の行に表示されます。 展開コントロールをクリックすると、子テーブルへの Web のようなリンクの一覧が生成されます。 ユーザーがリンクを選択すると、子テーブルが表示されます。 親行の表示/非表示のアイコンをクリックすると (![親行の表示/非表示のアイコン](../../../../docs/framework/winforms/controls/media/vbicon.png "vbIcon")) は、親テーブルに関する情報を非表示になるか、またはユーザーが非表示に表示します。 ユーザーは、戻るボタンをクリックして、前に表示されていたテーブルに移動することができます。  
  
## <a name="columns-and-rows"></a>列と行  
 <xref:System.Windows.Forms.DataGrid>のコレクションから成る<xref:System.Windows.Forms.DataGridTableStyle>に含まれているオブジェクト、 <xref:System.Windows.Forms.DataGrid>コントロールの<xref:System.Windows.Forms.DataGrid.TableStyles%2A>プロパティです。 テーブルのスタイルのコレクションを含めることが<xref:System.Windows.Forms.DataGridColumnStyle>に含まれているオブジェクト、 <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>のプロパティ、 <xref:System.Windows.Forms.DataGridTableStyle>. 編集することができます、 <xref:System.Windows.Forms.DataGrid.TableStyles%2A>と<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>プロパティからアクセスできるコレクション エディターを使用して、**プロパティ**ウィンドウです。  
  
 どの<xref:System.Windows.Forms.DataGridTableStyle>に関連付けられている、 <xref:System.Windows.Forms.DataGrid>経由でアクセスできるコントロール、 <xref:System.Windows.Forms.GridTableStylesCollection>します。 <xref:System.Windows.Forms.GridTableStylesCollection>と共に、デザイナーで編集できます、 <xref:System.Windows.Forms.DataGridTableStyle>コレクション エディターを使用してプログラムによって、または、 <xref:System.Windows.Forms.DataGrid>コントロールの<xref:System.Windows.Forms.DataGrid.TableStyles%2A>プロパティです。  
  
 ![DataGrid コントロールに含まれるオブジェクト](../../../../docs/framework/winforms/controls/media/vbcolumns1.png "vbColumns1")  
DataGrid コントロールに含まれるオブジェクトを次の図に示します。  
  
 テーブルのスタイルおよび列のスタイルと同期されます<xref:System.Data.DataTable>のオブジェクトと<xref:System.Data.DataColumn>を設定してオブジェクトの`MappingName`プロパティを適切な<xref:System.Data.DataTable.TableName%2A>と<xref:System.Data.DataColumn.ColumnName%2A>プロパティです。 ときに、 <xref:System.Windows.Forms.DataGridTableStyle>を保持していない列にスタイルを追加、 <xref:System.Windows.Forms.DataGrid> 、有効なデータ ソースにバインドされたコントロールと<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>テーブルのスタイルのプロパティが有効に設定されている<xref:System.Data.DataTable.TableName%2A>プロパティ、一連の<xref:System.Windows.Forms.DataGridColumnStyle>オブジェクトを作成してテーブルのスタイルのです。 各<xref:System.Data.DataColumn>で見つかった、<xref:System.Data.DataTable.Columns%2A>のコレクション、 <xref:System.Data.DataTable>、対応する<xref:System.Windows.Forms.DataGridColumnStyle>に追加、 <xref:System.Windows.Forms.GridColumnStylesCollection>します。 <xref:System.Windows.Forms.GridColumnStylesCollection>を通じてアクセス、 <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>のプロパティ、 <xref:System.Windows.Forms.DataGridTableStyle>します。 列を追加またはグリッドを使用して、削除、<xref:System.Windows.Forms.GridColumnStylesCollection.Add%2A>または<xref:System.Windows.Forms.GridColumnStylesCollection.Remove%2A>メソッドを<xref:System.Windows.Forms.GridColumnStylesCollection>します。 詳細については、次を参照してください。[方法: Windows フォーム DataGrid コントロールに追加のテーブルと列](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)と[方法: 削除] または [Windows フォーム DataGrid コントロールの列を非表示に](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)します。  
  
 列の型のコレクションを拡張、 <xref:System.Windows.Forms.DataGridColumnStyle>豊富な書式設定と編集機能が持つクラス。 すべての列型から継承、 <xref:System.Windows.Forms.DataGridColumnStyle>基本クラスです。 作成されるクラスによって異なります、 <xref:System.Data.DataColumn.DataType%2A>のプロパティ、 <xref:System.Data.DataColumn>元となる、 <xref:System.Web.UI.WebControls.DataGridColumn>基づきます。 たとえば、 <xref:System.Data.DataColumn>を持つその<xref:System.Data.DataColumn.DataType%2A>プロパティに設定<xref:System.Boolean>が関連付けられる、 <xref:System.Windows.Forms.DataGridBoolColumn>します。 各列の型に関する説明を次の表に示します。  
  
|列の型|説明|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.DataGridTextBoxColumn>|書式設定された文字列、または書式設定されていない文字列としてデータを受け入れて表示します。 編集機能は同じで、単純なデータを編集する場合と<xref:System.Windows.Forms.TextBox>します。 継承<xref:System.Windows.Forms.DataGridColumnStyle>します。|  
|<xref:System.Windows.Forms.DataGridBoolColumn>|`true`、`false`、および null 値を受け入れて表示します。 継承<xref:System.Windows.Forms.DataGridColumnStyle>します。|  
  
 列の右端をダブルクリックすると、完全キャプションと最も幅の広いエントリを表示するよう列のサイズを変更します。  
  
## <a name="table-styles-and-column-styles"></a>テーブルのスタイルおよび列のスタイル  
 既定の形式を確立するとすぐに、 <xref:System.Windows.Forms.DataGrid>コントロール、データ グリッド内の特定のテーブルが表示されるときに使用される色をカスタマイズすることができます。  
  
 これのインスタンスを作成するのには、 <xref:System.Windows.Forms.DataGridTableStyle>クラスです。 テーブルのスタイルは、特定のテーブルの既定の書式設定から個別の書式を指定する、 <xref:System.Windows.Forms.DataGrid>自体を制御します。 各テーブルは、定義されたテーブルのスタイルを一度に&1; つのみ持つことができます。  
  
 場合によっては、特定の列の外観を、特定のデータ テーブルの列の残りの部分と異なるものにすることが望ましい場合があります。 カスタマイズされた一連の列のスタイルを作成するにを使用して、 <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>プロパティです。  
  
 列のスタイルは、表のスタイルがデータ テーブルに関連するのと同じように、データセット内の列に関連します。 各テーブルに一度に&1; つの表のスタイルのみ定義できるように、各列も、特定のテーブルのスタイルで一度に&1; つの列のスタイルのみ定義できます。 このリレーションシップが、列で定義されている<xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A>プロパティです。  
  
 列のスタイルを追加せずにテーブルのスタイルを作成した場合は、フォームおよびグリッドが実行時に作成されるときに、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] が既定の列のスタイルを追加します。 ただし、テーブルのスタイルを作成して列のスタイルを追加している場合、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] は列のスタイルを作成しません。 また、列のスタイルを定義し、マッピングの名前に割り当てて、グリッドに表示する列を持つようにする必要があります。  
  
 列のスタイルに列を割り当てることでデータ グリッドに含まれる列を指定し、列に割り当てられた列のスタイルがないため、グリッドに表示されていないデータセットのデータの列を含めることができます。 ただし、データセットにデータ列が含まれているため、表示されていないデータをプログラムで編集できます。  
  
> [!NOTE]
>  一般に、表のスタイルをテーブル スタイルのコレクションに追加する前に、列のスタイルを作成し、列のスタイルのコレクションに追加します。 コレクションに空のテーブルのスタイルを追加すると、列のスタイルが自動的に生成されます。 重複した新しい列のスタイルを追加しようとする場合に、例外がスローされますその結果、 <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A>列スタイルのコレクションの値。  
>   
>  多くの列の中で 1 つのだけ列を微調整することが望ましい場合があります。たとえば、50 の列がデータセットに含まれていて、そのうち 49 のみが必要だとします。 この場合は、プログラムでの 49 個の列をそれぞれプログラムで追加するより、50 のすべての列をインポートし、1 つをプログラムで削除する方が簡単です。  
  
## <a name="formatting"></a>書式設定  
 書式設定を適用できる、 <xref:System.Windows.Forms.DataGrid>罫線のスタイル、グリッド線のスタイル、フォント、caption プロパティ、データの配置、および行の間の背景色を交互にコントロールが含まれます。 詳細については、次を参照してください。[方法: Windows フォーム DataGrid コントロールの書式設定](../../../../docs/framework/winforms/controls/how-to-format-the-windows-forms-datagrid-control.md)します。  
  
## <a name="events"></a>イベント  
 一般的なコントロール イベントのほかなど<xref:System.Windows.Forms.Control.MouseDown>、 <xref:System.Windows.Forms.Control.Enter>、および<xref:System.Windows.Forms.DataGrid.Scroll>、 <xref:System.Windows.Forms.DataGrid>コントロールの編集と、グリッド内での移動に関連付けられたイベントをサポートしています。 <xref:System.Windows.Forms.DataGrid.CurrentCell%2A>プロパティは、どのセルが選択を決定します。 <xref:System.Windows.Forms.DataGrid.CurrentCellChanged>イベントは、ユーザーが新しいセルに移動すると発生します。 ユーザーが、親/子リレーションシップを使用して新しいテーブルに移動すると、 <xref:System.Windows.Forms.DataGrid.Navigate>イベントが発生します。 <xref:System.Windows.Forms.DataGrid.BackButtonClick>イベントは、ユーザーが子テーブルを表示するときに、ユーザーが [戻る] ボタンをクリックすると、 <xref:System.Windows.Forms.DataGrid.ShowParentDetailsButtonClick>親行の表示/非表示のアイコンがクリックされたときにイベントが発生します。  
  
## <a name="see-also"></a>関連項目  
 [DataGrid コントロール](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)   
 [方法: Windows フォーム DataGrid コントロールをデータ ソースにバインドします。](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)   
 [方法: テーブルを追加し、列を Windows フォーム DataGrid コントロール](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)   
 [方法: 削除または非表示にする列、Windows フォーム DataGrid コントロール](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)   
 [方法: Windows フォーム DataGrid コントロールの書式設定](../../../../docs/framework/winforms/controls/how-to-format-the-windows-forms-datagrid-control.md)