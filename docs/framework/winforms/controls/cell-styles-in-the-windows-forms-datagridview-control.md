---
title: Windows フォーム DataGridView コントロールでのセルのスタイル
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
ms.openlocfilehash: 463fbbffe1e88991934f08fbe7e7445b2e233081
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529660"
---
# <a name="cell-styles-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールでのセルのスタイル
内の各セル、<xref:System.Windows.Forms.DataGridView>コントロールがテキスト形式、背景色、前景色、およびフォントなどの独自のスタイルを持つことができます。 通常、ただし、複数のセルが共有の特定のスタイル特性。  
  
 スタイルを共有するセルのグループには、コントロール内の特定の行または列、特定の値を含むすべてのセルまたはすべてのセル内のすべてのセルが含まれます。 これらのグループが重なるために、各セルは、複数の場所からスタイル情報を取得する可能性があります。 たとえば、することがすべてのセル、<xref:System.Windows.Forms.DataGridView>赤い前景の色を使用する負の数と同じフォントがのみに通貨の書式を使用する通貨列内のセルと通貨のセルのみを使用するコントロール。  
  
## <a name="the-datagridviewcellstyle-class"></a>DataGridViewCellStyle クラス  
 <xref:System.Windows.Forms.DataGridViewCellStyle>クラスには、visual スタイルに関連する次のプロパティが含まれています。  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> および <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> および <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 このクラスには、書式設定に関連する次のプロパティも含まれています。  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> および <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> および <xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 これらのプロパティとその他のセル スタイル プロパティの詳細については、次を参照してください。、<xref:System.Windows.Forms.DataGridViewCellStyle>リファレンス ドキュメントとトピックは、「参照」セクションに一覧表示します。  
  
## <a name="using-datagridviewcellstyle-objects"></a>DataGridViewCellStyle オブジェクトを使用します。  
 取得することができます<xref:System.Windows.Forms.DataGridViewCellStyle>のオブジェクトのさまざまなプロパティを<xref:System.Windows.Forms.DataGridView>、 <xref:System.Windows.Forms.DataGridViewColumn>、 <xref:System.Windows.Forms.DataGridViewRow>、および<xref:System.Windows.Forms.DataGridViewCell>クラスと派生クラスにします。 これらのプロパティのいずれかがまだ設定されていない場合、その値を取得する方が、新規に作成されます<xref:System.Windows.Forms.DataGridViewCellStyle>オブジェクト。 インスタンス化できます独自<xref:System.Windows.Forms.DataGridViewCellStyle>オブジェクトし、これらのプロパティに割り当てます。  
  
 共有することでスタイル情報が不要な重複を回避できます<xref:System.Windows.Forms.DataGridViewCellStyle>オブジェクトを複数の間で<xref:System.Windows.Forms.DataGridView>要素。 コントロール、列、およびセル レベルへの各レベルを使用してダウン行レベル フィルターで設定されたスタイルをためには、各レベル上位のレベルとは異なるスタイル プロパティだけを設定してもスタイルの重複を回避できます。 これは、次のスタイルの継承セクションで詳しく説明します。  
  
 次の表に、プライマリ プロパティを取得または設定<xref:System.Windows.Forms.DataGridViewCellStyle>オブジェクト。  
  
|プロパティ|クラス|説明|  
|--------------|-------------|-----------------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView>、 <xref:System.Windows.Forms.DataGridViewColumn>、 <xref:System.Windows.Forms.DataGridViewRow>、と派生クラス|取得またはコントロール全体 (ヘッダー セルを含む)、列、または行のすべてのセルで使用される既定のスタイルを設定します。|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|取得またはコントロール内のすべての行で使用される既定のセル スタイルを設定します。 これは、ヘッダー セルには含まれません。|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|取得またはコントロール内の行を交互に使用する既定のセル スタイルを設定します。 帳簿のような効果を作成するために使用します。|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|取得またはコントロールの行ヘッダーで使用される既定のセル スタイルを設定します。 Visual スタイルが有効になっている場合は、現在のテーマでオーバーライドします。|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|取得またはコントロールの列ヘッダーで使用される既定のセル スタイルを設定します。 Visual スタイルが有効になっている場合は、現在のテーマでオーバーライドします。|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|<xref:System.Windows.Forms.DataGridViewCell> クラスと派生クラス|取得またはセル レベルで指定されたスタイルを設定します。 これらのスタイルより高いレベルから継承したオーバーライドします。|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell>、 <xref:System.Windows.Forms.DataGridViewRow>、 <xref:System.Windows.Forms.DataGridViewColumn>、と派生クラス|現在のセル、行、またはより高いレベルから継承したスタイルを含む列に適用されているすべてのスタイルを取得します。|  
  
 前述のように、自動的にスタイル プロパティの値を取得するインスタンスを作成、新しい<xref:System.Windows.Forms.DataGridViewCellStyle>かどうか、プロパティが設定されていない以前のオブジェクトします。 行と列のクラスが不必要にこれらのオブジェクトの作成を避けるためには、<xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A>プロパティをチェックできるかどうか、<xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A>プロパティが設定されています。 同様に、セルのクラスが、<xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A>プロパティを示すかどうか、<xref:System.Windows.Forms.DataGridViewCell.Style%2A>プロパティが設定されています。  
  
 各スタイル プロパティに、対応する*PropertyName* `Changed`でイベントを<xref:System.Windows.Forms.DataGridView>コントロール。 行、列、およびセルのプロパティ、イベントの名前の先頭に"`Row`「,」`Column`"、または"`Cell`"(たとえば、 <xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>)。 別に、対応するスタイル プロパティが設定されている場合にこれらの各イベントが発生した<xref:System.Windows.Forms.DataGridViewCellStyle>オブジェクト。 取得するときに、これらのイベントが発生しません、<xref:System.Windows.Forms.DataGridViewCellStyle>スタイル プロパティからオブジェクトし、そのプロパティ値を変更します。 セル スタイル オブジェクト自体への変更に応答するには、処理、<xref:System.Windows.Forms.DataGridView.CellStyleContentChanged>イベント。  
  
## <a name="style-inheritance"></a>スタイルの継承  
 各<xref:System.Windows.Forms.DataGridViewCell>からその外観を取得、<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>プロパティです。 <xref:System.Windows.Forms.DataGridViewCellStyle>型のプロパティの階層からこのプロパティによって返されるオブジェクトはその値を継承<xref:System.Windows.Forms.DataGridViewCellStyle>です。 これらのプロパティを以下の順序、<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>非ヘッダー セルの値を取得します。  
  
1.  <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
3.  <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType> (奇数のインデックス番号を含む行のセル) の場合のみ  
  
4.  <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
5.  <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
6.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 行と列のヘッダー セルの<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>プロパティが特定の順序でソースのプロパティの次の一覧から値が格納されます。  
  
1.  <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType> または <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
  
3.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 次の図は、このプロセスを示しています。  
  
 ![DataGridViewCellStyle 型のプロパティ](../../../../docs/framework/winforms/controls/media/datagridviewcells1.gif "DataGridViewCells1")  
  
 特定の行や列によって継承されたスタイルをアクセスすることもできます。 列<xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A>プロパティは、次のプロパティからその値を継承します。  
  
1.  <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 行<xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A>プロパティは、次のプロパティからその値を継承します。  
  
1.  <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType> (奇数のインデックス番号を含む行のセル) の場合のみ  
  
3.  <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
4.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 各プロパティについて、<xref:System.Windows.Forms.DataGridViewCellStyle>によって返されるオブジェクト、`InheritedStyle`プロパティ値は、プロパティ、以外の値に設定した対応するプロパティを持つ適切なリストの最初のセル スタイルを取得、<xref:System.Windows.Forms.DataGridViewCellStyle>クラスの既定値です。  
  
 次の表に示す方法、<xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>例セルのプロパティの値がそのを含む列から継承されます。  
  
|型のプロパティ `DataGridViewCellStyle`|例`ForeColor`取得したオブジェクトの値|  
|----------------------------------------------|----------------------------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Black%2A?displayProperty=nameWithType>|  
  
 ここで、<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>セルの行からの値は、一覧の最初の実際の値。 これは、<xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>のセルのプロパティの値<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>です。  
  
 次の図はどのように異なる<xref:System.Windows.Forms.DataGridViewCellStyle>プロパティは、さまざまな場所からその値を継承できます。  
  
 ![DataGridView プロパティ&#45;値の継承](../../../../docs/framework/winforms/controls/media/datagridviewcells2.gif "DataGridViewCells2")  
  
 スタイルの継承を利用して複数の場所で同じ情報を指定することがなく、コントロール全体の適切なスタイルを指定できます。  
  
 ヘッダー セルは、の説明に従って、スタイルの継承に参加、によって返されるオブジェクト、<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>と<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>のプロパティ、<xref:System.Windows.Forms.DataGridView>コントロールがある値をオーバーライドするプロパティによって返されるオブジェクトの初期プロパティ値<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>プロパティです。 によって返されるオブジェクトに対して設定されたプロパティが必要なかどうか、<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>行および列のヘッダーに適用するプロパティによって返されるオブジェクトの対応するプロパティを設定する必要があります、<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>と<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>プロパティを既定値が示されます<xref:System.Windows.Forms.DataGridViewCellStyle>クラスです。  
  
> [!NOTE]
>  Visual スタイルが有効な場合、行および列ヘッダー (を除き、 <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) が自動的にこれらのプロパティで指定された任意のスタイルをオーバーライドする現在のテーマによってスタイルが設定します。  
  
 <xref:System.Windows.Forms.DataGridViewButtonColumn>、 <xref:System.Windows.Forms.DataGridViewImageColumn>、および<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>型の列によって返されるオブジェクトのいくつかの値も初期化<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>プロパティです。 詳細については、これらの型のリファレンス ドキュメントを参照してください。  
  
## <a name="setting-styles-dynamically"></a>動的なスタイルを設定  
 特定の値を持つセルのスタイルをカスタマイズするには、ハンドラーを実装する、<xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>イベント。 このイベントのハンドラーの引数を受け取る、<xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs>型です。 このオブジェクトには内の場所と共に書式が設定されるセルの値を決定するのに便利なプロパティが含まれています、<xref:System.Windows.Forms.DataGridView>コントロール。 このオブジェクトにも含まれています、<xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A>プロパティの値に初期化される、<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>書式が設定されるセルのプロパティです。 セルの値と場所を適切なスタイル情報を指定するセルのスタイル プロパティを変更することができます。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView.RowPrePaint>と<xref:System.Windows.Forms.DataGridView.RowPostPaint>も、イベントを受信する<xref:System.Windows.Forms.DataGridViewCellStyle>オブジェクト、イベントのデータが行のコピーでは、大文字小文字で<xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A>読み取り専用のために変更し、プロパティ、コントロールには影響しません。  
  
 などのイベントに応答の個々 のセルのスタイルを変更することができますも動的に、<xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=nameWithType>と<xref:System.Windows.Forms.DataGridView.CellMouseLeave>イベント。 ハンドラーでなど、<xref:System.Windows.Forms.DataGridView.CellMouseEnter>イベント、セルの背景色の現在の値を格納する可能性があります (セルのを介して取得<xref:System.Windows.Forms.DataGridViewCell.Style%2A>プロパティ)、上にマウスを置くと、セルを強調表示する新しい色に設定します。 ハンドラーで、<xref:System.Windows.Forms.DataGridView.CellMouseLeave>イベント、元の値に背景色を復元できます。  
  
> [!NOTE]
>  セルに格納されている値をキャッシュ<xref:System.Windows.Forms.DataGridViewCell.Style%2A>プロパティは、特定のスタイル値が設定されているかに関係なく重要です。 スタイルの設定を一時的に置換する場合をセルに戻ってより高いレベルからスタイルの設定を継承することにより元の「設定ではない」状態に復元すること。 有効で、スタイルを継承するかどうかに関係なく、セルの実際のスタイルを決定する必要がある場合は、セルを使用して<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>プロパティです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.InheritedStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>  
 [Windows フォームの DataGridView コントロールの基本的な書式設定およびスタイル設定](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [方法: Windows フォーム DataGridView コントロールの既定のセル スタイルを設定する](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 [Windows フォーム DataGridView コントロールでのデータの書式設定](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)
