---
title: DataGrid コントロールのサイズ変更方法
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid control [WPF], sizing
- size [WPF], DataGrid
- automatically size DataGrid [WPF]
ms.assetid: 96a0e47e-b010-4302-98ef-2daac446d8db
ms.openlocfilehash: 0019ac9ad82301506d2da279094b2c96e022e915
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557850"
---
# <a name="sizing-options-in-the-datagrid-control"></a>DataGrid コントロールのサイズ変更方法
さまざまなオプションは、コントロールを使用する方法、<xref:System.Windows.Controls.DataGrid>自体のサイズを設定します。 <xref:System.Windows.Controls.DataGrid>、および個々 の行と列、<xref:System.Windows.Controls.DataGrid>その内容を自動的にサイズに設定することができます、または特定の値に設定することができます。 既定では、<xref:System.Windows.Controls.DataGrid>拡大およびその内容のサイズに合わせて縮小されます。  
  
## <a name="sizing-the-datagrid"></a>データ グリッドのサイズ変更  
  
### <a name="cautions-when-using-automatic-sizing"></a>自動サイズ変更を使用する場合の注意事項  
 既定では、<xref:System.Windows.FrameworkElement.Height%2A>と<xref:System.Windows.FrameworkElement.Width%2A>のプロパティ、<xref:System.Windows.Controls.DataGrid>に設定されている<xref:System.Double.NaN?displayProperty=nameWithType>("`Auto`"XAML で)、および<xref:System.Windows.Controls.DataGrid>はその内容のサイズを調整します。  
  
 では、その子のサイズなど、コンテナー内に配置されたときに、<xref:System.Windows.Controls.Canvas>または<xref:System.Windows.Controls.StackPanel>、<xref:System.Windows.Controls.DataGrid>表示、コンテナーの境界を超えるし、スクロール バーは表示されません。 このような状況では、使いやすさとパフォーマンスの両方の影響を与えます。  
  
 場合は、データ セットにバインドするとき、<xref:System.Windows.FrameworkElement.Height%2A>の<xref:System.Windows.Controls.DataGrid>は制限されず、行を追加する、各データ項目にバインドされたデータ セットで続行されます。 これが原因で、<xref:System.Windows.Controls.DataGrid>するにつれて、アプリケーションの表示領域外の行が追加されます。 <xref:System.Windows.Controls.DataGrid>は表示されませんスクロールバーここであるため、<xref:System.Windows.FrameworkElement.Height%2A>に新しい行に合わせて拡大し続けます。  
  
 内の行ごとに、オブジェクトを作成、<xref:System.Windows.Controls.DataGrid>です。 大きなデータ セットを使用して、できるようにするかどうか、<xref:System.Windows.Controls.DataGrid>自動的にそれ自体のサイズ、多数のオブジェクトの作成、アプリケーションのパフォーマンスに影響する可能性があります。  
  
 これらの問題を避けるためには、大きなデータ セットを使用する場合、お勧めする明示的に設定する、<xref:System.Windows.FrameworkElement.Height%2A>の<xref:System.Windows.Controls.DataGrid>を制限するコンテナーに配置すること、またはその<xref:System.Windows.FrameworkElement.Height%2A>など、<xref:System.Windows.Controls.Grid>です。 ときに、<xref:System.Windows.FrameworkElement.Height%2A>制限されている場合は、<xref:System.Windows.Controls.DataGrid>のみ、指定した内に収まる行が作成されます<xref:System.Windows.FrameworkElement.Height%2A>、し、新しいデータを表示する、必要に応じて、これらの行をリサイクルします。  
  
### <a name="setting-the-datagrid-size"></a>データ グリッド サイズの設定  
 <xref:System.Windows.Controls.DataGrid>自動的にサイズを指定された境界内に設定することができます、または<xref:System.Windows.Controls.DataGrid>特定のサイズに設定することができます。 次の表に、コントロールに設定できるプロパティ、<xref:System.Windows.Controls.DataGrid>サイズ。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|<xref:System.Windows.FrameworkElement.Height%2A>|特定の高さの設定、<xref:System.Windows.Controls.DataGrid>です。|  
|<xref:System.Windows.FrameworkElement.MaxHeight%2A>|高さの上限の境界を設定、<xref:System.Windows.Controls.DataGrid>です。 <xref:System.Windows.Controls.DataGrid>この高さに達するまで垂直方向に拡張されます。|  
|<xref:System.Windows.FrameworkElement.MinHeight%2A>|高さの下限の境界を設定、<xref:System.Windows.Controls.DataGrid>です。 <xref:System.Windows.Controls.DataGrid>この高さに達するまで垂直方向に縮小されます。|  
|<xref:System.Windows.FrameworkElement.Width%2A>|特定の幅を設定、<xref:System.Windows.Controls.DataGrid>です。|  
|<xref:System.Windows.FrameworkElement.MaxWidth%2A>|幅の上限の境界を設定、<xref:System.Windows.Controls.DataGrid>です。 <xref:System.Windows.Controls.DataGrid>この幅に達するまで水平方向に拡張されます。|  
|<xref:System.Windows.FrameworkElement.MinWidth%2A>|幅の下限の境界を設定、<xref:System.Windows.Controls.DataGrid>です。 <xref:System.Windows.Controls.DataGrid>この幅に達するまで水平方向に縮小されます。|  
  
## <a name="sizing-rows-and-row-headers"></a>行と行ヘッダーのサイズ変更  
  
### <a name="datagrid-rows"></a>データ グリッドの行  
 既定では、<xref:System.Windows.Controls.DataGrid>行の<xref:System.Windows.FrameworkElement.Height%2A>プロパティに設定されている<xref:System.Double.NaN?displayProperty=nameWithType>("`Auto`"XAML で)、および行の高さがその内容のサイズに拡張されます。 すべての行の高さ、<xref:System.Windows.Controls.DataGrid>を設定して指定することができます、<xref:System.Windows.Controls.DataGrid.RowHeight%2A?displayProperty=nameWithType>プロパティです。 ユーザーは、行のヘッダー区分線をドラッグして行の高さを変更できます。  
  
### <a name="datagrid-row-headers"></a>DataGrid の行ヘッダー  
 行ヘッダーを表示する、<xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A>プロパティに設定する必要があります<xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType>または<xref:System.Windows.Controls.DataGridHeadersVisibility.All?displayProperty=nameWithType>です。 既定では、行ヘッダーが表示され、その内容に合わせてサイズが自動的に調整。 行ヘッダーを指定できます、特定の幅を設定して、<xref:System.Windows.Controls.DataGrid.RowHeaderWidth%2A?displayProperty=nameWithType>プロパティです。  
  
## <a name="sizing-columns-and-column-headers"></a>列および列ヘッダーのサイズ変更  
  
### <a name="datagrid-columns"></a>DataGrid 列  
 <xref:System.Windows.Controls.DataGrid>の値を使用して、<xref:System.Windows.Controls.DataGridLength>と<xref:System.Windows.Controls.DataGridLengthUnitType>構造を絶対または自動サイズ変更モードを指定します。  
  
 次の表に、によって提供される値、<xref:System.Windows.Controls.DataGridLengthUnitType>構造体。  
  
|名前|説明|  
|----------|-----------------|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Auto>|既定の自動サイズ変更モード サイズ<xref:System.Windows.Controls.DataGrid>セルと列ヘッダーの内容に基づく列です。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToCells>|セルに基づく自動サイズ変更モード サイズ<xref:System.Windows.Controls.DataGrid>列ヘッダーを含まない、列内のセルの内容に基づく列です。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToHeader>|ヘッダーに基づく自動サイズ変更モード サイズ<xref:System.Windows.Controls.DataGrid>のみの列ヘッダーの内容に基づく列です。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Pixel>|ピクセル ベース モードのサイズをサイズ変更<xref:System.Windows.Controls.DataGrid>指定された数値に基づく列です。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Star>|星のサイズ変更モードを使用加重比率に基づいて使用可能な領域を配布します。<br /><br /> XAML では、星型の値は n * n が数値の値を表すとして表されます。 1\*は等価\*です。 たとえば、次の 2 つ内の列、<xref:System.Windows.Controls.DataGrid>の幅が\*および 2\*、最初の列は使用可能な領域の 1 つの部分を受信し、2 番目の列は使用可能な領域の 2 つの部分を受信します。|  
  
 <xref:System.Windows.Controls.DataGridLengthConverter>クラスは、数値または文字列値間でデータを変換するために使用できますと<xref:System.Windows.Controls.DataGridLength>値。  
  
 既定では、<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>プロパティに設定されている<xref:System.Windows.Controls.DataGridLength.SizeToHeader%2A>、および<xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType>プロパティに設定されている<xref:System.Windows.Controls.DataGridLength.Auto%2A>です。 サイズ変更モードを設定すると<xref:System.Windows.Controls.DataGridLength.Auto%2A>または<xref:System.Windows.Controls.DataGridLength.SizeToCells%2A>列が表示されている最大限のコンテンツの幅が増加します。 スクロール、これらのサイズ変更モードが発生コンテンツを展開する列がビューをスクロールして、現在の列のサイズよりも大きいをします。 コンテンツのスクロールされて見えない後に、列は圧縮されません。  
  
 内の列、 <xref:System.Windows.Controls.DataGrid> 、指定された境界内でのみ自動的にサイズを設定することも、または列は、特定のサイズに設定することができます。 次の表は、列のサイズを制御する設定できるプロパティを示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|<xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>|すべての列の上限の境界を設定、<xref:System.Windows.Controls.DataGrid>です。|  
|<xref:System.Windows.Controls.DataGridColumn.MaxWidth%2A?displayProperty=nameWithType>|個々 の列の上限の境界を設定します。 オーバーライド<xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>です。|  
|<xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>|すべての列の下限の境界を設定、<xref:System.Windows.Controls.DataGrid>です。|  
|<xref:System.Windows.Controls.DataGridColumn.MinWidth%2A?displayProperty=nameWithType>|個々 の列の下限の境界を設定します。 オーバーライド<xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>です。|  
|<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>|すべての列に特定の幅を設定、<xref:System.Windows.Controls.DataGrid>です。|  
|<xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType>|個々 の列を特定の幅を設定します。 オーバーライド<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>です。|  
  
### <a name="datagrid-column-headers"></a>DataGrid 列ヘッダー  
 既定では、<xref:System.Windows.Controls.DataGrid>列ヘッダーが表示されます。 列ヘッダーを非表示にする、<xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A>プロパティに設定する必要があります<xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType>または<xref:System.Windows.Controls.DataGridHeadersVisibility.None?displayProperty=nameWithType>です。 既定では、列ヘッダーが表示される場合、そのサイズは、コンテンツに合わせて自動的にされます。 列ヘッダーを指定できます、特定の高さを設定して、<xref:System.Windows.Controls.DataGrid.ColumnHeaderHeight%2A?displayProperty=nameWithType>プロパティです。  
  
### <a name="resizing-with-the-mouse"></a>マウスを使用してサイズを変更します。  
 サイズを変更できるユーザー<xref:System.Windows.Controls.DataGrid>行と列、行または列のヘッダー区分線をドラッグします。 <xref:System.Windows.Controls.DataGrid>行または列のヘッダー区分線をダブルクリックして行および列の自動サイズ変更もサポートします。 設定をユーザーが特定の列のサイズを変更することを防ぐために、<xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType>プロパティを`false`個々 の列に対するです。 ユーザーがすべての列のサイズを変更することを防止するには、設定、<xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType>プロパティを`false`です。 ユーザーがすべての行のサイズを変更することを防止するには、設定、<xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A?displayProperty=nameWithType>プロパティを`false`です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.DataGrid>  
 <xref:System.Windows.Controls.DataGridColumn>  
 <xref:System.Windows.Controls.DataGridLength>  
 <xref:System.Windows.Controls.DataGridLengthConverter>
