---
title: "Windows フォーム DataGridView コントロールでのセルのスタイル | Microsoft Docs"
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
  - "セル, スタイル"
  - "データ グリッド, セル スタイル"
  - "DataGridView コントロール [Windows フォーム], セル スタイル"
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
caps.latest.revision: 33
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 33
---
# Windows フォーム DataGridView コントロールでのセルのスタイル
<xref:System.Windows.Forms.DataGridView> コントロール内の各セルは、テキスト形式、背景色、前景色、フォントなど、独自のスタイルを持つことができます。  ただし、通常は複数のセルが特定のスタイル特性を共有します。  
  
 スタイルを共有するセルのグループとしては、特定の行または列のすべてのセル、特定の値を格納するすべてのセル、またはコントロール内のすべてのセル、などがあります。  これらのグループは重複するため、各セルは複数の場所からスタイル情報を取得できます。  たとえば、<xref:System.Windows.Forms.DataGridView> コントロールのすべてのセルに同じフォントを使用し、通貨列のセルだけに通貨書式を使用し、負数を持つ通貨セルだけに赤の前景色を使用するように指定することもできます。  
  
## DataGridViewCellStyle クラス  
 <xref:System.Windows.Forms.DataGridViewCellStyle> クラスには、visual スタイルに関連する次のプロパティが含まれます。  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> および <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> および <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 また、このクラスには書式設定に関連する次のプロパティも含まれます。  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> および <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> および <xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 これらのプロパティおよびその他のセル スタイル プロパティの詳細については、<xref:System.Windows.Forms.DataGridViewCellStyle> のリファレンス ドキュメント、および後の「参照」セクションに示したトピックを参照してください。  
  
## DataGridViewCellStyle オブジェクトの使用  
 <xref:System.Windows.Forms.DataGridViewCellStyle> オブジェクトは、<xref:System.Windows.Forms.DataGridView>、<xref:System.Windows.Forms.DataGridViewColumn>、<xref:System.Windows.Forms.DataGridViewRow>、<xref:System.Windows.Forms.DataGridViewCell> の各クラス、およびその派生クラスのさまざまなプロパティから取得できます。  これらのプロパティのいずれかが設定されていない場合、その値を取得すると、新しい <xref:System.Windows.Forms.DataGridViewCellStyle> オブジェクトが作成されます。  独自に作成した <xref:System.Windows.Forms.DataGridViewCellStyle> オブジェクトをインスタンス化して、これらのプロパティを割り当てることもできます。  
  
 複数の <xref:System.Windows.Forms.DataGridView> 要素間で <xref:System.Windows.Forms.DataGridViewCellStyle> オブジェクトを共有すると、スタイル情報の不要な重複を避けることができます。  また、コントロール レベル、列レベル、および行レベルで設定されたスタイルは、各レベルからセル レベルまで、下方向にフィルター処理されるため、上位のレベルとは異なるスタイル プロパティだけを各レベルで設定することによってスタイルの重複を避けることもできます。  これについては、後の「スタイルの継承」セクションで詳しく説明します。  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle> オブジェクトを取得または設定する主要なプロパティを次の表に示します。  
  
|プロパティ|Classes|Description|  
|-----------|-------------|-----------------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView>、<xref:System.Windows.Forms.DataGridViewColumn>、<xref:System.Windows.Forms.DataGridViewRow>、および派生クラス|コントロール全体 \(ヘッダー セルを含む\)、列、または行内のすべてのセルが使用する既定のスタイルを取得または設定します。|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|コントロール内のすべての行が使用する既定のセル スタイルを取得または設定します。  ヘッダー セルは含まれません。|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|コントロール内の交互の行が使用する既定のセル スタイルを取得または設定します。  帳簿のような効果を出すために使用します。|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|コントロールの行ヘッダーが使用する既定のセル スタイルを取得または設定します。  visual スタイルが有効な場合は、現在のテーマでオーバーライドされます。|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|コントロールの列ヘッダーが使用する既定のセル スタイルを取得または設定します。  visual スタイルが有効な場合は、現在のテーマでオーバーライドされます。|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|<xref:System.Windows.Forms.DataGridViewCell> と派生クラス|セル レベルで指定されたスタイルを取得または設定します。  このスタイルは、上位レベルから継承したスタイルをオーバーライドします。|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell>、<xref:System.Windows.Forms.DataGridViewRow>、<xref:System.Windows.Forms.DataGridViewColumn>、および派生クラス|セル、行、または列に現在適用されているすべてのスタイルを取得します。上位レベルから継承したスタイルを含みます。|  
  
 前述のように、スタイル プロパティがまだ設定されていない場合にスタイル プロパティの値を取得すると、新しい <xref:System.Windows.Forms.DataGridViewCellStyle> オブジェクトのインスタンスが自動的に生成されます。  不要なオブジェクトが作成されないようにするため、行クラスや列クラスには、<xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A> プロパティが設定されているかどうかを確認するためにチェックできる <xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A> プロパティが用意されています。  同様に、セル クラスには、<xref:System.Windows.Forms.DataGridViewCell.Style%2A> プロパティが設定されているかどうかを示す <xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A> プロパティがあります。  
  
 各スタイル プロパティには、対応する <xref:System.Windows.Forms.DataGridView> コントロールの *PropertyName*`Changed` イベントがあります。  行、列、およびセルのプロパティの場合、イベント名は "`Row`"、"`Column`"、または "`Cell`" で始まります \(たとえば、<xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>\)。  これらの各イベントは、対応するスタイル プロパティが異なる <xref:System.Windows.Forms.DataGridViewCellStyle> オブジェクトに設定されているときに発生します。  これらのイベントは、スタイル プロパティから <xref:System.Windows.Forms.DataGridViewCellStyle> オブジェクトを取得してプロパティ値を変更したときには発生しません。  セル スタイル オブジェクト自体に対する変更に対応するには、<xref:System.Windows.Forms.DataGridView.CellStyleContentChanged> イベントを処理します。  
  
## スタイルの継承  
 各 <xref:System.Windows.Forms.DataGridViewCell> は、その <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> プロパティから外観を取得します。  このプロパティが返す <xref:System.Windows.Forms.DataGridViewCellStyle> オブジェクトは、<xref:System.Windows.Forms.DataGridViewCellStyle> 型のプロパティの階層構造から値を継承します。  これらのプロパティを以下に示します。ヘッダー セル以外のセルの <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> が値を取得する順に記載します。  
  
1.  <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=fullName>  
  
2.  <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=fullName>  
  
3.  <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=fullName> \(奇数のインデックス番号を持つ行のセルのみ\)  
  
4.  <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=fullName>  
  
5.  <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=fullName>  
  
6.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>  
  
 行および列のヘッダー セルの場合、<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> プロパティには、指定した順序で、以下に示すソース プロパティの値が設定されます。  
  
1.  <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=fullName>  
  
2.  <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=fullName> または <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=fullName>  
  
3.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>  
  
 このプロセスを説明する図を次に示します。  
  
 ![DataGridViewCellStyle 型のプロパティ](../../../../docs/framework/winforms/controls/media/datagridviewcells1.png "DataGridViewCells1")  
  
 特定の行および列が継承したスタイルにアクセスすることもできます。  列の <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A> プロパティは、次のプロパティから値を継承します。  
  
1.  <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=fullName>  
  
2.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>  
  
 行の <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> プロパティは、次のプロパティから値を継承します。  
  
1.  <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=fullName>  
  
2.  <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=fullName> \(奇数のインデックス番号を持つ行のセルのみ\)  
  
3.  <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=fullName>  
  
4.  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>  
  
 `InheritedStyle` プロパティが返す <xref:System.Windows.Forms.DataGridViewCellStyle> オブジェクトの各プロパティの場合、プロパティ値は、<xref:System.Windows.Forms.DataGridViewCellStyle> クラスの既定値以外の値に、対応するプロパティが設定された適切なリストの最初のセル スタイルから取得されます。  
  
 例のセルの <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> プロパティ値が、そのセルを含む列から継承されるしくみを次の表に示します。  
  
|`DataGridViewCellStyle` 型のプロパティ|取得されるオブジェクトの `ForeColor` 値の例|  
|-------------------------------------|----------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=fullName>|<xref:System.Drawing.Color.Empty?displayProperty=fullName>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=fullName>|<xref:System.Drawing.Color.Red%2A?displayProperty=fullName>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=fullName>|<xref:System.Drawing.Color.Empty?displayProperty=fullName>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=fullName>|<xref:System.Drawing.Color.Empty?displayProperty=fullName>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=fullName>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=fullName>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>|<xref:System.Drawing.Color.Black%2A?displayProperty=fullName>|  
  
 この場合、セルの行の <xref:System.Drawing.Color.Red%2A?displayProperty=fullName> 値はリストの最初の値 \(実際の値\) です。  この値が、セルの <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> の <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> プロパティ値になります。  
  
 さまざまな <xref:System.Windows.Forms.DataGridViewCellStyle> プロパティがさまざまな場所から値を継承できるしくみを次の図に示します。  
  
 ![DataGridView プロパティ &#45; 値の継承](../../../../docs/framework/winforms/controls/media/datagridviewcells2.png "DataGridViewCells2")  
  
 スタイルの継承を利用することにより、同じ情報を複数の場所で指定せずに、コントロール全体に適切なスタイルを指定できます。  
  
 ヘッダー セルは前述のとおりにスタイルを継承しますが、<xref:System.Windows.Forms.DataGridView> コントロールの <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> プロパティおよび <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> プロパティが返すオブジェクトは、<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> プロパティが返すオブジェクトのプロパティ値をオーバーライドする初期プロパティ値を持ちます。  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> プロパティが返すオブジェクトに設定されたプロパティを行ヘッダーと列ヘッダーに適用するときは、<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> プロパティと <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> プロパティが返すオブジェクトの対応するプロパティを、<xref:System.Windows.Forms.DataGridViewCellStyle> クラスに対して示された既定値に設定する必要があります。  
  
> [!NOTE]
>  visual スタイルを有効にすると、行ヘッダーと列ヘッダー \(<xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A> を除く\) のスタイルは現在のテーマによって自動的に設定され、これらのプロパティで指定したすべてのスタイルはオーバーライドされます。  
  
 また、<xref:System.Windows.Forms.DataGridViewButtonColumn> 型、<xref:System.Windows.Forms.DataGridViewImageColumn> 型、および <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> 型も、列の <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> プロパティが返すオブジェクトのいくつかの値を初期化します。  詳細については、各型のリファレンス ドキュメントを参照してください。  
  
## 動的なスタイル設定  
 特定の値でセルのスタイルをカスタマイズするには、<xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=fullName> イベントのハンドラーを実装します。  このイベントのハンドラーは、<xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> 型の引数を受け取ります。  このオブジェクトに含まれるプロパティを使用して、書式を設定するセルの値と <xref:System.Windows.Forms.DataGridView> コントロールにおけるセルの場所を決定します。  また、このオブジェクトには <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A> プロパティも含まれます。このプロパティは、書式を設定するセルの <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> プロパティの値に初期化されます。  このセル スタイル プロパティを変更して、セルの値と場所に適したスタイル情報を指定できます。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView.RowPrePaint> イベントと <xref:System.Windows.Forms.DataGridView.RowPostPaint> イベントもイベント データの <xref:System.Windows.Forms.DataGridViewCellStyle> オブジェクトを受け取りますが、その場合、オプジェクトは読み取り専用の行の <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A> プロパティのコピーです。変更しても、コントロールには反映されません。  
  
 <xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=fullName> や <xref:System.Windows.Forms.DataGridView.CellMouseLeave> などのイベントに応答して、個々のセルのスタイルを動的に変更することもできます。  たとえば、<xref:System.Windows.Forms.DataGridView.CellMouseEnter> イベントのハンドラー内に \(セルの <xref:System.Windows.Forms.DataGridViewCell.Style%2A> プロパティから取得した\) セルの背景色の現在値を格納し、セル上にマウスが配置されたときにセルを強調表示する新しい色を設定できます。  その後、<xref:System.Windows.Forms.DataGridView.CellMouseLeave> イベントのハンドラー内で背景色を元の色に戻すことができます。  
  
> [!NOTE]
>  特定のスタイル値が設定されているかどうかにかかわらず、セルの <xref:System.Windows.Forms.DataGridViewCell.Style%2A> プロパティに格納された値をキャッシュすることは重要です。  スタイル設定を一時的に置き換えた場合、元の "設定なし" の状態に戻すことによって、セルのスタイル設定を再度上位レベルから継承できます。  スタイルが継承されているかどうかにかかわらず、セルに対して有効になっている実際のスタイルを確認する必要があるときは、セルの <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> プロパティを使用します。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewCellStyle>   
 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewBand.InheritedStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=fullName>   
 [Windows フォームの DataGridView コントロールの基本的な書式設定およびスタイル設定](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)   
 [方法 : Windows フォーム DataGridView コントロールの既定のセル スタイルを設定する](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールでのデータの書式設定](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)