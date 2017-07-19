---
title: "DataGrid コントロールのサイズ変更方法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "自動的なサイズ変更 (DataGrid を)"
  - "DataGrid コントロール [WPF], サイズ変更"
  - "サイズ [WPF], DataGrid"
ms.assetid: 96a0e47e-b010-4302-98ef-2daac446d8db
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# DataGrid コントロールのサイズ変更方法
<xref:System.Windows.Controls.DataGrid> のサイズは、さまざまな方法で制御できます。  <xref:System.Windows.Controls.DataGrid> のサイズと、<xref:System.Windows.Controls.DataGrid> を構成する行および列のサイズは、そのコンテンツに応じて自動的に設定するか、特定の値を設定することで変更できます。  既定では、<xref:System.Windows.Controls.DataGrid> は、そのコンテンツのサイズに合わせて伸縮します。  
  
## DataGrid のサイズ変更  
  
### 自動サイズ変更を使用する際の注意点  
 既定では、<xref:System.Windows.Controls.DataGrid> の <xref:System.Windows.FrameworkElement.Height%2A> プロパティと <xref:System.Windows.FrameworkElement.Width%2A> プロパティが <xref:System.Double.NaN?displayProperty=fullName> \(XAML では "`Auto`"\) に設定され、<xref:System.Windows.Controls.DataGrid> のサイズが、そのコンテンツの大きさに合わせて調整されるようになっています。  
  
 子のサイズが制限されないコンテナー内 \(<xref:System.Windows.Controls.Canvas>、<xref:System.Windows.Controls.StackPanel> など\) に配置した場合、<xref:System.Windows.Controls.DataGrid> がコンテナーの可視領域を越えて拡張され、スクロール バーは表示されません。  これはユーザビリティの面でも、パフォーマンスの面でも問題があります。  
  
 <xref:System.Windows.Controls.DataGrid> をデータ セットにバインドした場合、DataGrid の <xref:System.Windows.FrameworkElement.Height%2A> を制限しない限り、バインドされたデータ セットのデータ項目ごとに、際限なく行が追加されていきます。  最終的には、行が追加されるに従って、<xref:System.Windows.Controls.DataGrid> の大きさがアプリケーションの可視領域を越えることが予想されます。  この場合、<xref:System.Windows.Controls.DataGrid> そのものは、新しい行を表示できるよう、<xref:System.Windows.FrameworkElement.Height%2A> が絶えず拡張されるため、スクロール バーは表示されません。  
  
 オブジェクトは、<xref:System.Windows.Controls.DataGrid> 内の行ごとに作成されます。  <xref:System.Windows.Controls.DataGrid> のサイズが自動的に調整されるように設定した場合、扱うデータ セットが大きいと、多数のオブジェクトが作成されるために、アプリケーションのパフォーマンスが低下する可能性があります。  
  
 大きなデータ セットを扱う際の問題を防ぐために、<xref:System.Windows.Controls.DataGrid> の <xref:System.Windows.FrameworkElement.Height%2A> に具体的な値を設定するか、DataGrid の配置先を <xref:System.Windows.FrameworkElement.Height%2A> が制限されるコンテナー \(<xref:System.Windows.Controls.Grid> など\) にすることをお勧めします。  <xref:System.Windows.FrameworkElement.Height%2A> が制限されている場合、<xref:System.Windows.Controls.DataGrid> の行は、指定された <xref:System.Windows.FrameworkElement.Height%2A> の範囲内でのみ作成され、新しいデータを表示するために必要な分だけ、これらの行が再利用されます。  
  
### DataGrid のサイズ設定  
 <xref:System.Windows.Controls.DataGrid> は、指定された範囲内で自動的にサイズが調整されるように設定することも、<xref:System.Windows.Controls.DataGrid> に特定のサイズを設定することもできます。  次の表は、<xref:System.Windows.Controls.DataGrid> のサイズ制御に関連したプロパティを示しています。  
  
|プロパティ|Description|  
|-----------|-----------------|  
|<xref:System.Windows.FrameworkElement.Height%2A>|<xref:System.Windows.Controls.DataGrid> の特定の高さを設定します。|  
|<xref:System.Windows.FrameworkElement.MaxHeight%2A>|<xref:System.Windows.Controls.DataGrid> の高さの上限を設定します。  <xref:System.Windows.Controls.DataGrid> のサイズは、この高さに達するまで垂直方向に拡張されます。|  
|<xref:System.Windows.FrameworkElement.MinHeight%2A>|<xref:System.Windows.Controls.DataGrid> の高さの下限を設定します。  <xref:System.Windows.Controls.DataGrid> のサイズは、この高さに達するまで垂直方向に縮小されます。|  
|<xref:System.Windows.FrameworkElement.Width%2A>|<xref:System.Windows.Controls.DataGrid> の特定の幅を設定します。|  
|<xref:System.Windows.FrameworkElement.MaxWidth%2A>|<xref:System.Windows.Controls.DataGrid> の幅の上限を設定します。  <xref:System.Windows.Controls.DataGrid> のサイズは、この幅に達するまで水平方向に拡張されます。|  
|<xref:System.Windows.FrameworkElement.MinWidth%2A>|<xref:System.Windows.Controls.DataGrid> の幅の下限を設定します。  <xref:System.Windows.Controls.DataGrid> のサイズは、この幅に達するまで水平方向に縮小されます。|  
  
## 行と行ヘッダーのサイズ変更  
  
### DataGrid の行  
 既定では、<xref:System.Windows.Controls.DataGrid> の行の <xref:System.Windows.FrameworkElement.Height%2A> プロパティが <xref:System.Double.NaN?displayProperty=fullName> \(XAML では "`Auto`"\) に設定されているため、行の高さは、そのコンテンツの大きさに合わせて拡張されます。  <xref:System.Windows.Controls.DataGrid> 内のすべての行の高さは、<xref:System.Windows.Controls.DataGrid.RowHeight%2A?displayProperty=fullName> プロパティを設定することによって指定できます。  ユーザーは、行ヘッダーの区分線をドラッグすることによって行の高さを変更できます。  
  
### DataGrid の行ヘッダー  
 行ヘッダーを表示するには、<xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> プロパティを <xref:System.Windows.Controls.DataGridHeadersVisibility?displayProperty=fullName> または <xref:System.Windows.Controls.DataGridHeadersVisibility?displayProperty=fullName> に設定する必要があります。  既定では、行ヘッダーを表示すると、そのサイズはコンテンツに合わせて自動的に調整されます。  行ヘッダーには、<xref:System.Windows.Controls.DataGrid.RowHeaderWidth%2A?displayProperty=fullName> プロパティを設定することによって特定の幅を指定できます。  
  
## 列と列ヘッダーのサイズ変更  
  
### DataGrid の列  
 <xref:System.Windows.Controls.DataGrid> の絶対サイズ変更モードまたは自動サイズ変更モードを指定する際には、<xref:System.Windows.Controls.DataGridLength> および <xref:System.Windows.Controls.DataGridLengthUnitType> 構造体の値が使用されます。  
  
 <xref:System.Windows.Controls.DataGridLengthUnitType> 構造体の値を次の表に示します。  
  
|名前|Description|  
|--------|-----------------|  
|<xref:System.Windows.Controls.DataGridLengthUnitType>|既定の自動サイズ変更モードでは、セルと列ヘッダーの両方のコンテンツに基づき、<xref:System.Windows.Controls.DataGrid> 列のサイズが変更されます。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType>|セル ベースの自動サイズ変更モードでは、列内のセルのコンテンツに基づき \(列ヘッダーは含みません\)、<xref:System.Windows.Controls.DataGrid> 列のサイズが変更されます。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType>|ヘッダー ベースの自動サイズ変更モードでは、列ヘッダーのコンテンツにのみ基づき、<xref:System.Windows.Controls.DataGrid> 列のサイズが変更されます。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType>|ピクセル ベースのサイズ変更モードでは、<xref:System.Windows.Controls.DataGrid> 列のサイズが、指定された数値に基づいて設定されます。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType>|スター サイズ変更モードでは、使用可能なスペースを加重比率に基づいて配分できます。<br /><br /> XAML では、スター値は n\* と表現されます \(n は数値を表します\)。  1\* は \* と同じ意味です。  たとえば、<xref:System.Windows.Controls.DataGrid> の 2 つの列の幅がそれぞれ \* と 2\* であるとした場合、最初の列には使用可能なスペースの 3 分の 1 が割り当てられ、2 番目の列には使用可能なスペースの 3 分の 2 が割り当てられます。|  
  
 <xref:System.Windows.Controls.DataGridLengthConverter> クラスを使用すると、数値 \(または文字列値\) と <xref:System.Windows.Controls.DataGridLength> 値との間でデータを変換できます。  
  
 既定では、<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=fullName> プロパティが <xref:System.Windows.Controls.DataGridLength.SizeToHeader%2A> に、<xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=fullName> プロパティが <xref:System.Windows.Controls.DataGridLength.Auto%2A> に設定されます。  サイズ変更モードを <xref:System.Windows.Controls.DataGridLength.Auto%2A> または <xref:System.Windows.Controls.DataGridLength.SizeToCells%2A> に設定した場合、最も幅の広い可視コンテンツの幅に合わせて列が拡張されます。  これらのサイズ変更モードでは、現在の列サイズよりも大きいコンテンツをスクロールして表示すると列が拡張されます。  コンテンツを表示領域の外側にスクロールした後も、列は縮小されません。  
  
 <xref:System.Windows.Controls.DataGrid> の列のサイズは、指定された範囲内で自動的に調整されるようにしたり、特定のサイズを設定したりすることもできます。  次の表は、列のサイズ制御に関連したプロパティを示しています。  
  
|プロパティ|Description|  
|-----------|-----------------|  
|<xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=fullName>|<xref:System.Windows.Controls.DataGrid> 内のすべての列の上限を設定します。|  
|<xref:System.Windows.Controls.DataGridColumn.MaxWidth%2A?displayProperty=fullName>|個々の列の上限を設定します。  <xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=fullName> をオーバーライドします。|  
|<xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=fullName>|<xref:System.Windows.Controls.DataGrid> 内のすべての列の下限を設定します。|  
|<xref:System.Windows.Controls.DataGridColumn.MinWidth%2A?displayProperty=fullName>|個々の列の下限を設定します。  <xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=fullName> をオーバーライドします。|  
|<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=fullName>|<xref:System.Windows.Controls.DataGrid> のすべての列に対し、特定の幅を設定します。|  
|<xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=fullName>|個々の列に対し、特定の幅を設定します。  <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=fullName> をオーバーライドします。|  
  
### DataGrid の列ヘッダー  
 既定では、<xref:System.Windows.Controls.DataGrid> に列ヘッダーが表示されます。  列ヘッダーを非表示にするには、<xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> プロパティを <xref:System.Windows.Controls.DataGridHeadersVisibility?displayProperty=fullName> または <xref:System.Windows.Controls.DataGridHeadersVisibility?displayProperty=fullName> に設定する必要があります。  既定では、列ヘッダーを表示した場合、そのサイズは、コンテンツに合わせて自動的に調整されます。  列ヘッダーには、<xref:System.Windows.Controls.DataGrid.ColumnHeaderHeight%2A?displayProperty=fullName> プロパティを設定することによって特定の高さを指定できます。  
  
### マウス操作によるサイズ変更  
 ユーザーは、行ヘッダーまたは列ヘッダーの区分線をドラッグすることによって、<xref:System.Windows.Controls.DataGrid> 行または列のサイズを変更できます。  <xref:System.Windows.Controls.DataGrid> では、行ヘッダーまたは列ヘッダーの区分線をダブルクリックすることによる行または列の自動サイズ変更もサポートされます。  特定の列のサイズを変更できないようにするには、個々の列について、<xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=fullName> プロパティを `false` に設定します。  すべての列のサイズを変更できないようにするには、<xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=fullName> プロパティを `false` に設定します。  すべての行のサイズを変更できないようにするには、<xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A?displayProperty=fullName> プロパティを `false` に設定します。  
  
## 参照  
 <xref:System.Windows.Controls.DataGrid>   
 <xref:System.Windows.Controls.DataGridColumn>   
 <xref:System.Windows.Controls.DataGridLength>   
 <xref:System.Windows.Controls.DataGridLengthConverter>