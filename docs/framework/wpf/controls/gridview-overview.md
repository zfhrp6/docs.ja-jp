---
title: "GridView の概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コントロール, ListView"
  - "GridView 表示モード"
  - "ListView コントロール, GridView 表示モード"
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
caps.latest.revision: 26
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 25
---
# GridView の概要
<xref:System.Windows.Controls.GridView> 表示モードは、<xref:System.Windows.Controls.ListView> コントロールの表示モードの 1 つです。  <xref:System.Windows.Controls.GridView> クラスおよびそのサポート クラスを使用すると、一般的にボタンを対話型列ヘッダーとして使用するテーブルに項目コレクションを表示することができます。  ここでは、<xref:System.Windows.Controls.GridView> クラスについて説明し、その使用方法を示します。  
  
   
  
<a name="DefiningaListViewthatusesGridViewView"></a>   
## GridView ビューとは  
 <xref:System.Windows.Controls.GridView> 表示モードでは、データ フィールドを列にバインドし、列ヘッダーを表示してフィールドを識別することによって、データ項目のリストを表示します。  既定の <xref:System.Windows.Controls.GridView> スタイルは、列ヘッダーとしてボタンを実装します。  列ヘッダーにボタンを使用すると、重要なユーザー操作機能を実装できます。たとえば、ユーザーは列ヘッダーをクリックして、特定の列のコンテンツに従って <xref:System.Windows.Controls.GridView> データを並べ替えることができます。  
  
> [!NOTE]
>  <xref:System.Windows.Controls.GridView> で列ヘッダーに使用されるボタン コントロールは、<xref:System.Windows.Controls.Primitives.ButtonBase> から派生します。  
  
 <xref:System.Windows.Controls.ListView> コンテンツの <xref:System.Windows.Controls.GridView> ビューを次の図に示します。  
  
 **ListView コンテンツの GridView ビュー**  
  
 ![スタイル設定された ListView](../../../../docs/framework/wpf/controls/media/styledlistview.png "StyledListView")  
  
 <xref:System.Windows.Controls.GridView> の列は <xref:System.Windows.Controls.GridViewColumn> オブジェクトによって表されます。このオブジェクトのサイズは、コンテンツのサイズに自動的に設定されます。  必要に応じて、<xref:System.Windows.Controls.GridViewColumn> を特定の幅に明示的に設定できます。  列ヘッダー間のグリッパーをドラッグすることによって、列のサイズを変更できます。  また、列の追加、削除、置換、および並べ替え機能が <xref:System.Windows.Controls.GridView> に組み込まれているため、この機能を動的に実行することができます。  ただし、<xref:System.Windows.Controls.GridView> では、表示されるデータを直接更新することはできません。  
  
 従業員データを表示する <xref:System.Windows.Controls.GridView> を定義する方法を次の例に示します。  この例では、<xref:System.Windows.Controls.ListView> で `EmployeeInfoDataSource` が <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> として定義されています。  <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> のプロパティ定義によって、<xref:System.Windows.Controls.GridViewColumn> のコンテンツが `EmployeeInfoDataSource` データ カテゴリにバインドされます。  
  
 [!code-xml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 前述の例で作成したテーブルを次の図に示します。  
  
 **ItemsSource のデータを表示する GridView**  
  
 ![GridView 出力を含む ListView](../../../../docs/framework/wpf/controls/media/listviewgridview.png "ListViewGridView")  
  
<a name="GridViewLayoutandStyle"></a>   
## GridView レイアウトおよびスタイル  
 <xref:System.Windows.Controls.GridViewColumn> の列のセルおよび列ヘッダーの幅は同じです。  既定では、各列の幅は、そのコンテンツに合わせて設定されます。  必要に応じて、列を固定幅に設定できます。  
  
 関連するデータ コンテンツは、水平行に表示されます。  たとえば、前の図では、各従業員の氏名および ID 番号が水平行に示されているため、これらが 1 つのセットとして表示されています。  
  
<a name="DefiningandStylingColumnsinaGridView"></a>   
### GridView の列の定義およびスタイル設定  
 <xref:System.Windows.Controls.GridViewColumn> に表示するデータ フィールドを定義する場合は、<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>、<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>、または <xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A> プロパティを使用します。  <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> プロパティは、他の 2 つのテンプレート プロパティよりも優先されます。  
  
 <xref:System.Windows.Controls.GridView> の列のコンテンツの配置を指定するには、<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> を定義します。  <xref:System.Windows.Controls.GridView> を使用して表示する <xref:System.Windows.Controls.ListView> のコンテンツには、<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> および <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> プロパティを使用しないでください。  
  
 列ヘッダーのテンプレート プロパティとスタイル プロパティを指定するには、<xref:System.Windows.Controls.GridView>、<xref:System.Windows.Controls.GridViewColumn>、および <xref:System.Windows.Controls.GridViewColumnHeader> クラスを使用します。  詳細については、「[GridView の列ヘッダー スタイルおｙびテンプレートの概要](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md)」を参照してください。  
  
<a name="AddingVisualElementstoaGridViewView"></a>   
### GridView へのビジュアル要素の追加  
 <xref:System.Windows.Controls.CheckBox> コントロールや <xref:System.Windows.Controls.Button> コントロールなどのビジュアル要素を <xref:System.Windows.Controls.GridView> 表示モードに追加するには、テンプレートまたはスタイルを使用します。  
  
 ビジュアル要素をデータ項目として明示的に定義した場合、その要素は <xref:System.Windows.Controls.GridView> に一度しか表示できません。  この制限は、要素は親を 1 つしか持つことができず、[ビジュアル ツリー](GTMT)に一度しか表示されないために適用されます。  
  
<a name="StylingRowsinaGridViewView"></a>   
### GridView の行のスタイル設定  
 <xref:System.Windows.Controls.GridViewRowPresenter> および <xref:System.Windows.Controls.GridViewHeaderRowPresenter> クラスを使用して、<xref:System.Windows.Controls.GridView> の行を書式設定して表示します。  <xref:System.Windows.Controls.GridView> 表示モードの行のスタイルを設定する方法の例については、「[GridView を実装する ListView で行のスタイルを設定する](../../../../docs/framework/wpf/controls/how-to-style-a-row-in-a-listview-that-implements-a-gridview.md)」を参照してください。  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>   
### ItemContainerStyle を使用する際の配置の問題  
 列ヘッダーとセル間の配置の問題を回避するため、<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> の項目の幅に影響を与えるプロパティを設定したりテンプレートを指定したりしないようにしてください。  たとえば、<xref:System.Windows.FrameworkElement.Margin%2A> プロパティを設定したり、<xref:System.Windows.Controls.ListView> コントロールで定義されている <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> に <xref:System.Windows.Controls.CheckBox> を追加する <xref:System.Windows.Controls.ControlTemplate> を指定したりしないでください。  代わりに、列の幅に影響を与えるプロパティおよびテンプレートを、<xref:System.Windows.Controls.GridView> 表示モードを定義するクラスで直接指定してください。  
  
 たとえば、<xref:System.Windows.Controls.CheckBox> を <xref:System.Windows.Controls.GridView> 表示モードの行に追加するには、<xref:System.Windows.Controls.CheckBox> を <xref:System.Windows.DataTemplate> に追加して、<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> プロパティをその <xref:System.Windows.DataTemplate> に設定します。  
  
<a name="InteractingwithaGridViewControl"></a>   
## GridView でのユーザーの操作  
 アプリケーションで <xref:System.Windows.Controls.GridView> を使用する場合、ユーザーは <xref:System.Windows.Controls.GridView> の書式設定を操作および変更できます。  たとえば、ユーザーは列の並べ替え、列のサイズ変更、テーブルでの項目の選択、コンテンツのスクロールなどを実行できます。  また、ユーザーが列ヘッダー ボタンをクリックしたときに応答するイベント ハンドラーを定義することもできます。  イベント ハンドラーは、列のコンテンツに従って <xref:System.Windows.Controls.GridView> に表示されるデータを並べ替える操作などを実行できます。  
  
 <xref:System.Windows.Controls.GridView> を使用したユーザー操作のための機能の詳細を次に示します。  
  
-   **ドラッグ アンド ドロップを使用した列の並べ替え。**  
  
     ユーザーは、マウスが列ヘッダー上にあるときにその左ボタンを押してその列を新しい位置にドラッグすることで、<xref:System.Windows.Controls.GridView> の列を並べ替えることができます。  ユーザーが列ヘッダーをドラッグするとき、フローティング バージョンのヘッダーと、列を挿入する位置を示す黒い実線が表示されます。  
  
     フローティング バージョンのヘッダーの既定のスタイルを変更する場合は、<xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> プロパティが <xref:System.Windows.Controls.GridViewColumnHeaderRole> に設定されているときにトリガーされる <xref:System.Windows.Controls.GridViewColumnHeader> 型の <xref:System.Windows.Controls.ControlTemplate> を指定します。  詳細については、「[ドラッグされた GridView 列ヘッダーのスタイルを作成する](../../../../docs/framework/wpf/controls/how-to-create-a-style-for-a-dragged-gridview-column-header.md)」を参照してください。  
  
-   **コンテンツに合わせた列のサイズ変更。**  
  
     ユーザーは、列ヘッダーの右にあるグリッパーをダブルクリックして、列のサイズをそのコンテンツに合わせて変更することができます。  
  
    > [!NOTE]
    >  <xref:System.Windows.Controls.GridViewColumn.Width%2A> プロパティを `Double.NaN` に設定して、同じ効果を得ることができます。  
  
-   **行項目の選択。**  
  
     ユーザーは、<xref:System.Windows.Controls.GridView> の 1 つ以上の項目を選択できます。  
  
     選択された項目の <xref:System.Windows.Style> を変更する場合は、「[トリガーを使用して、ListView で選択された項目のスタイルを設定する](../../../../docs/framework/wpf/controls/how-to-use-triggers-to-style-selected-items-in-a-listview.md)」を参照してください。  
  
-   **最初に画面に表示されていないコンテンツを表示するためのスクロール。**  
  
     <xref:System.Windows.Controls.GridView> のサイズがすべての項目を表示できる十分な大きさではない場合、ユーザーは、<xref:System.Windows.Controls.ScrollViewer> コントロールによって提供されるスクロール バーを使用して水平方向または垂直方向にスクロールできます。  特定の方向ですべてのコンテンツが表示可能な場合、<xref:System.Windows.Controls.Primitives.ScrollBar> は非表示になります。  列ヘッダーは垂直スクロール バーでスクロールされませんが、水平方向にはスクロールされます。  
  
-   **列ヘッダー ボタンをクリックすることによる列の操作。**  
  
     並べ替えアルゴリズムが提供されている場合、列ヘッダー ボタンをクリックすると、ユーザーは列に表示されるデータを並べ替えることができます。  
  
     並べ替えアルゴリズムなどの機能を提供するには、列ヘッダー ボタンの <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントを処理します。  単一の列ヘッダーの <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントを処理するには、<xref:System.Windows.Controls.GridViewColumnHeader> に対してイベント ハンドラーを設定します。  すべての列ヘッダーの <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントを処理するイベント ハンドラーを設定するには、<xref:System.Windows.Controls.ListView> コントロールに対してハンドラーを設定します。  
  
<a name="Obtaining_Other_Custom_Views"></a>   
## その他のカスタム ビューの取得  
 <xref:System.Windows.Controls.ViewBase> 抽象クラスから派生した <xref:System.Windows.Controls.GridView> クラスは、<xref:System.Windows.Controls.ListView> クラスの使用可能な表示モードの一例です。  <xref:System.Windows.Controls.ViewBase> クラスから派生させて、<xref:System.Windows.Controls.ListView> のその他のカスタム ビューを作成できます。  カスタム表示モードの例については、「[ListView のカスタム表示モードを作成する](../../../../docs/framework/wpf/controls/how-to-create-a-custom-view-mode-for-a-listview.md)」を参照してください。  
  
<a name="GridViewSupportingClasses"></a>   
## GridView のサポート クラス  
 次のクラスは <xref:System.Windows.Controls.GridView> 表示モードをサポートします。  
  
-   <xref:System.Windows.Controls.GridViewColumn>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeader>  
  
-   <xref:System.Windows.Controls.GridViewRowPresenter>  
  
-   <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
  
-   <xref:System.Windows.Controls.GridViewColumnCollection>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
  
## 参照  
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.ListViewItem>   
 <xref:System.Windows.Controls.GridViewColumn>   
 <xref:System.Windows.Controls.GridViewColumnHeader>   
 <xref:System.Windows.Controls.GridViewRowPresenter>   
 <xref:System.Windows.Controls.GridViewHeaderRowPresenter>   
 <xref:System.Windows.Controls.ViewBase>   
 [ListView の概要](../../../../docs/framework/wpf/controls/listview-overview.md)   
 [ヘッダーがクリックされたときに GridView 列を並べ替える](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)   
 [方法のトピック](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)