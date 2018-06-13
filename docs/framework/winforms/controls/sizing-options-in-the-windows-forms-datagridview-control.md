---
title: Windows フォーム DataGridView コントロールのサイズ変更オプション
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], row sizing
- data grids [Windows Forms], column sizing
- DataGridView control [Windows Forms], column sizing
- DataGridView control [Windows Forms], sizing options
- data grids [Windows Forms], row sizing
- data grids [Windows Forms], sizing options
ms.assetid: a5620a9c-0d06-41e3-8934-c25ddb16c9e6
ms.openlocfilehash: 6e3a7786970ef536da4ef7628cd33ae067ba90be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541755"
---
# <a name="sizing-options-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールのサイズ変更オプション
<xref:System.Windows.Forms.DataGridView> 行、列、およびヘッダーは、多くの異なるオカレンスの結果としてのサイズを変更できます。 次の表は、その要因を示します。  
  
|出現する位置|説明|  
|----------------|-----------------|  
|ユーザーによるサイズ変更|ユーザーをドラッグするか、行、列、またはヘッダー区分線をダブルクリックすると、サイズの調整を行うことができます。|  
|コントロールのサイズ変更|列フィル モードでの列の幅を変更する; のコントロールの幅が変更されたときたとえばとユーザーの親フォームにコントロールがドッキングされているときに、フォームがサイズ変更します。|  
|セル値の変更|コンテンツ ベースの自動サイズ変更モードでは、サイズは、新しい表示値に合わせて変更します。|  
|メソッド呼び出し|プログラムによるコンテンツ ベースのサイズを変更するには、メソッドの呼び出し時にセルの値に基づく日和見的なサイズを調整することができます。|  
|プロパティの設定|特定の高さと幅の値を設定することもできます。|  
  
 既定では、ユーザーによるサイズ変更が有効になっている、自動サイズ変更は無効になり、その列よりも太くセルの値をクリップします。  
  
 次の表は、既定の動作を調整するか、特定の効果を実現するために特定のサイズ変更オプションを使用するを使用することができますシナリオを示しています。  
  
|シナリオ|実装|  
|--------------|--------------------|  
|同様を使用して列フィル モードを表示するためには、比較的少数の水平スクロール バーを表示することがなく、コントロールの幅全体を占有する列のデータがサイズ調整されます。|<xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> プロパティを <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> に設定します。|  
|列フィル モードの使用は、さまざまなサイズの値を表示します。|<xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> プロパティを <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> に設定します。 列を設定して、相対的な列の幅を初期化<xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>プロパティまたはコントロールを呼び出すことによって<xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>メソッド データにコントロールを格納した後にします。|  
|列フィル モードを使用して、さまざまな重要度の値を使用します。|<xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> プロパティを <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> に設定します。 大規模なセット<xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>値は常に、データの一部を表示または以外の場合、サイズ変更オプションを使用する必要がある列が特定の列のモードを入力します。|  
|列フィル モードを使用して、コントロールの背景色が表示されないようにします。|設定、<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>に最後の列のプロパティ<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill>し、その他の列に他のサイズ変更オプションを使用します。 他の列を使用する利用可能な領域が多すぎる場合は、設定、<xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>最後の列のプロパティです。|  
|アイコンまたは ID 列などの固定長列を表示します。|設定<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>に<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>と<xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A>に<xref:System.Windows.Forms.DataGridViewTriState.False>列にします。 幅を設定して初期化、<xref:System.Windows.Forms.DataGridViewColumn.Width%2A>プロパティまたはコントロールを呼び出すことによって<xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>メソッド データにコントロールを格納した後にします。|  
|クリッピングを回避し、領域の使用を最適化するためにセルの内容が変更されるたびに自動的にサイズを調整します。|コンテンツ ベースのサイズ変更モードを表す値を自動サイズ変更プロパティを設定します。 パフォーマンスの低下を避けるためには、大量のデータを操作するとき、表示されている行のみを計算するサイズ変更モードを使用します。|  
|多くの行を操作するときにパフォーマンスの低下を避けるために表示されている行の値に合わせてサイズを調整します。|自動またはプログラムによるサイズ変更の操作には、適切なサイズ変更モードの列挙値を使用します。 スクロール中も新しく表示されている行の値に合わせてサイズを調整するのでサイズ変更メソッドを呼び出す、<xref:System.Windows.Forms.DataGridView.Scroll>イベント ハンドラー。 ユーザーをダブルクリックをカスタマイズするサイズを変更する表示されている行の値のみが、新しいサイズを決定できるようにサイズ変更のメソッドを呼び出す、<xref:System.Windows.Forms.DataGridView.RowDividerDoubleClick>または<xref:System.Windows.Forms.DataGridView.ColumnDividerDoubleClick>イベント ハンドラー。|  
|または、パフォーマンスの低下を避けるために、ユーザーによるサイズ変更を有効にする特定の時点でのみセルの内容に合わせてサイズを調整します。|イベント ハンドラーで、コンテンツ ベースのサイズ変更のメソッドを呼び出します。 などを使用して、<xref:System.Windows.Forms.DataGridView.DataBindingComplete>をバインドされた後のサイズを初期化し、処理するイベント、<xref:System.Windows.Forms.DataGridView.CellValidated>または<xref:System.Windows.Forms.DataGridView.CellValueChanged>ユーザーによる編集内容または変更を補正するためのサイズを調整イベント バインド データ ソースにします。|  
|複数行のセルの内容の行の高さを調整します。|列の幅が段落のテキストを表示するための適切なことを確認し、自動またはプログラムのコンテンツ ベースの行のサイズ変更を使用して、高さを調整します。 使用して複数行のコンテンツを含むセルを表示することも確認、<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>セルのスタイル値<xref:System.Windows.Forms.DataGridViewTriState.True>です。<br /><br /> 通常、列の幅を維持または行の高さを調整する前に、特定の値に設定する列の自動サイズ変更モードを使用します。|  
  
## <a name="resizing-with-the-mouse"></a>マウスを使用してサイズを変更します。  
 既定では、行、列、およびヘッダーのセルの値に基づく自動サイズ変更モードを使用しないユーザーを変更します。 ユーザーが列フィル モードなどの他のモードとサイズを変更することを防止する、次の 1 つ以上を設定<xref:System.Windows.Forms.DataGridView>プロパティ。  
  
-   <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
 個々 の行または列をサイズ変更を設定してからユーザーを防ぐことができますもその<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>プロパティです。 既定では、<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>プロパティの値に基づいています、<xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>列のプロパティの値と<xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>行のプロパティの値。 明示的に設定する場合<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>に<xref:System.Windows.Forms.DataGridViewTriState.True>または<xref:System.Windows.Forms.DataGridViewTriState.False>、ただし、コントロールの値がその行または列が、指定した値で上書きします。 設定<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>に<xref:System.Windows.Forms.DataGridViewTriState.NotSet>継承を復元します。  
  
 <xref:System.Windows.Forms.DataGridViewTriState.NotSet>値の継承の復元、<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>プロパティは返されません、<xref:System.Windows.Forms.DataGridViewTriState.NotSet>値の行または列に追加されていない場合を除き、<xref:System.Windows.Forms.DataGridView>コントロール。 決定する必要がある場合かどうか、<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>を確認して、行または列のプロパティの値が継承されたその<xref:System.Windows.Forms.DataGridViewElement.State%2A>プロパティです。 場合、<xref:System.Windows.Forms.DataGridViewElement.State%2A>値が含まれる、<xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>フラグを<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>プロパティの値は継承できません。  
  
## <a name="automatic-sizing"></a>自動サイズ変更  
 自動サイズ変更の 2 種類があります、<xref:System.Windows.Forms.DataGridView>コントロール: 列フィル モードとコンテンツ ベースの自動サイズ変更します。  
  
 列フィル モードでは、コントロールの表示領域の幅に合わせてコントロールで表示する列が発生します。 このモードの詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールで列の塗りつぶしモード](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md)です。  
  
 行、列、およびセルの内容に合わせて、それぞれのサイズを自動的に調整するヘッダーを構成することもできます。 この場合、サイズの調整は、セルの内容を変更するたびに発生します。  
  
> [!NOTE]
>  仮想モードを使用してカスタム データ キャッシュ内のセル値を保持している場合自動サイズ変更場合にユーザーはセル値を編集しますが、外部のキャッシュされた値を変更するときは発生しません、<xref:System.Windows.Forms.DataGridView.CellValuePushed>イベント ハンドラー。 この場合、呼び出し、<xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A>セルの表示を更新して、現在の自動サイズ変更モードを適用するコントロールを強制する方法です。  
  
 1 つの次元だけのコンテンツ ベースの自動サイズ変更が有効になっている場合: は、行がない列は、列やがない行を — と<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>も有効な場合、サイズの調整は、その他のディメンションが変更されるたびにも発生します。 たとえば、自動サイズ変更用に構成されていない列は行と<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>は有効な場合、ユーザーが列の幅を変更する列の区分線をドラッグでき、行の高さは、セルの内容が完全に表示されるように自動的に調整します。  
  
 両方の行と列のコンテンツ ベースの自動サイズ調整を構成する場合と<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>が有効になって、<xref:System.Windows.Forms.DataGridView>セルの内容が変更され、新しいサイズを計算するときに、理想的なセルの高さと幅の比率を使用するたびに、コントロールのサイズは調整します。  
  
 コントロールの値をオーバーライドしない列のヘッダーと行のサイズ変更モードを構成するのには次の 1 つ以上を設定<xref:System.Windows.Forms.DataGridView>プロパティ。  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A>  
  
 個々 の列のコントロールの列のサイズ変更モードを無効にする次のように設定します。 その<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>プロパティ以外の値を<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>です。 列のサイズ変更モードがによって決まりますが実際にその<xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A>プロパティです。 このプロパティの値が列のに基づいて<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>プロパティ値の値がない限り、<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>いる場合、コントロールの<xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>値を継承します。  
  
 コンテンツに基づく自動サイズ変更慎重に大量のデータを操作するときに使用します。 パフォーマンスの低下を回避するのには、コントロール内のすべての行を分析するのではなく、表示されている行にのみ基づいてのサイズを計算する自動サイズ変更モードを使用します。 最高のパフォーマンスを使用するプログラムによるサイズを変更する代わりにできるように、サイズを変更する特定の時点でなど直後に新しいデータが読み込まれます。  
  
 コンテンツ ベースの自動サイズ変更モードには影響しません、行、列、またはヘッダー行または列を設定して非表示にした<xref:System.Windows.Forms.DataGridViewBand.Visible%2A>プロパティまたはコントロール<xref:System.Windows.Forms.DataGridView.RowHeadersVisible%2A>または<xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A>プロパティ`false`です。 など、大規模なセルの値に合わせてサイズが自動的に設定した後に列を非表示の場合非表示の列は変わりませんのサイズの大きなセル値を含む行が削除された場合。 可視性が変更されたときに、自動サイズ変更は発生しません、列を変更すること<xref:System.Windows.Forms.DataGridViewColumn.Visible%2A>プロパティ`true`現在の内容に基づいて、サイズを再計算することを強制しません。  
  
 行、列、およびヘッダー表示設定に関係なく、プログラムによるコンテンツに基づくサイズ変更に影響します。  
  
## <a name="programmatic-resizing"></a>プログラムによるサイズ変更  
 自動サイズ調整を無効にすると、行、列、または、次のプロパティでヘッダーの高さまたは正確な幅をプログラムで設定できます。  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
  
 行、列、および、次のメソッドを使用してその内容に合わせてヘッダー サイズを変更することができますもプログラム。  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A>  
  
 これらのメソッドは、行、列、または 1 回のヘッダーではなく継続的なサイズ変更するための構成にサイズ変更されます。 クリッピングなしすべてのセルの内容を表示する新しいサイズが自動的に計算します。 ときにプログラムでサイズを変更する列を持つ<xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A>プロパティの値を<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill>、比例して、列を調整する計算のコンテンツ ベースの幅を使用するただし、<xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>プロパティ値、および幅は、実際には列すべての列は、コントロールの使用可能な表示領域を入力できるようにこれらの新しい比率に従って計算されます。  
  
 プログラムによるサイズ変更は、継続的なサイズを変更するとパフォーマンスの低下を避けるために便利です。 ユーザーのサイズ変更可能な行、列、およびヘッダー、および列フィル モードの初期サイズを指定すると便利です。  
  
 通常は特定の時点でプログラムによるサイズ変更メソッドを呼び出します。 たとえばがプログラムでサイズを変更するすべての列データの読み込み後すぐにまたは可能性がありますプログラムでサイズを変更する特定の行の特定のセル値が変更された後にします。  
  
## <a name="customizing-content-based-sizing-behavior"></a>コンテンツ ベースのサイズ変更動作をカスタマイズします。  
 派生を使用する場合は、サイズ変更動作をカスタマイズすることができます<xref:System.Windows.Forms.DataGridView>セル、行、および列の種類をオーバーライドすることで、 <xref:System.Windows.Forms.DataGridViewCell.GetPreferredSize%2A?displayProperty=nameWithType>、 <xref:System.Windows.Forms.DataGridViewRow.GetPreferredHeight%2A?displayProperty=nameWithType>、または<xref:System.Windows.Forms.DataGridViewColumn.GetPreferredWidth%2A?displayProperty=nameWithType>メソッドを呼び出して、派生でサイズ変更メソッドのオーバー ロードの保護された<xref:System.Windows.Forms.DataGridView>コントロール。 保護対象のサイズ変更メソッドのオーバー ロードは、過度に幅または高さのセルの回避、理想的なセルの高さと幅比を実現するペアの作業に設計されています。 呼び出す場合など、`AutoResizeRows(DataGridViewAutoSizeRowsMode,Boolean)`のオーバー ロード、<xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>メソッドの値で渡します`false`の<xref:System.Boolean>パラメーター、理想的な高さと幅、行内のセルのオーバー ロードが計算されますが、行の高さに調整されますのみです。 呼び出す必要があります、<xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>計算最適に列の幅を調整する方法です。  
  
## <a name="content-based-sizing-options"></a>コンテンツ ベースのサイズ変更オプション  
 サイズ変更プロパティおよびメソッドで使用される列挙体では、コンテンツ ベースのサイズ変更と同様の値があります。 これらの値を適切なサイズの計算に使用するセルを制限できます。 すべてのサイズ変更の列挙は、表示されているセルを参照する名前を持つ値は、表示されている行のセルに計算を制限します。 行の除外は、大量の行を使用しているときに、パフォーマンスの低下を避けるために便利です。 計算またはヘッダー以外のセルのセルの値を制限することもできます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>  
 <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>  
 <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>  
 [Windows フォーム DataGridView コントロール内の列と行のサイズ変更](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 [Windows フォーム DataGridView コントロールの列フィル モード](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 [方法: Windows フォーム DataGridView コントロールのサイズ変更モードを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)
