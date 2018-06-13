---
title: GridView の概要
ms.date: 03/30/2017
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
ms.openlocfilehash: 776897d490b2748e240cf7b9a4ea21364284c4c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557682"
---
# <a name="gridview-overview"></a>GridView の概要
<xref:System.Windows.Controls.GridView> 表示モードのいずれかのビュー モードは、<xref:System.Windows.Controls.ListView>コントロール。 <xref:System.Windows.Controls.GridView>とユーザーの対話型の列見出しとして通常のボタンを使用するテーブル内の項目コレクションを表示するクラスとそのサポート クラスを有効にします。 このトピックでは、<xref:System.Windows.Controls.GridView>クラスし、その用途について説明します。  
  
  
  
<a name="DefiningaListViewthatusesGridViewView"></a>   
## <a name="what-is-a-gridview-view"></a>GridView のビューとは?  
 <xref:System.Windows.Controls.GridView>ビュー モードでは、列のデータ フィールドのバインドとフィールドを識別する列ヘッダーを表示することによってデータ項目の一覧が表示されます。 既定値<xref:System.Windows.Controls.GridView>スタイルを列見出しとしてボタンを実装します。 列ヘッダーのボタンを使用して、重要なユーザー操作機能を実装することができます。ユーザーが並べ替えに列ヘッダーをクリックするなど、<xref:System.Windows.Controls.GridView>特定の列の内容に合わせてデータ。  
  
> [!NOTE]
>  ボタン コントロールが<xref:System.Windows.Controls.GridView>、列ヘッダーの使用に由来<xref:System.Windows.Controls.Primitives.ButtonBase>です。  
  
 次の図は、<xref:System.Windows.Controls.GridView>の表示<xref:System.Windows.Controls.ListView>コンテンツ。  
  
 **ListView コンテンツの GridView ビュー**  
  
 ![スタイル化 ListView](../../../../docs/framework/wpf/controls/media/styledlistview.PNG "StyledListView")  
  
 <xref:System.Windows.Controls.GridView> 列がによって表される<xref:System.Windows.Controls.GridViewColumn>オブジェクトで、そのコンテンツを自動的にサイズことができます。 必要に応じて、明示的に設定できます、<xref:System.Windows.Controls.GridViewColumn>幅を指定します。 列のサイズは、列ヘッダー間のグリッパーをドラッグすることで変更できます。 ことができますも動的に追加、削除、置換、およびにこの機能が組み込まれているために、列を並べ替える<xref:System.Windows.Controls.GridView>です。 ただし、<xref:System.Windows.Controls.GridView>表示されるデータを直接更新することはできません。  
  
 次の例は、定義する方法を示します、<xref:System.Windows.Controls.GridView>従業員データを表示します。 この例では<xref:System.Windows.Controls.ListView>定義、`EmployeeInfoDataSource`として、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>です。 プロパティ定義<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>バインド<xref:System.Windows.Controls.GridViewColumn>へのコンテンツ`EmployeeInfoDataSource`データのカテゴリ。  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 次の図は、前の例により作成されるテーブルを示しています。  
  
 **GridView、ItemsSource からデータを表示します。**  
  
 ![GridView 出力を含む ListView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")  
  
<a name="GridViewLayoutandStyle"></a>   
## <a name="gridview-layout-and-style"></a>GridView のレイアウトとスタイル  
 列のセルと列ヘッダーの<xref:System.Windows.Controls.GridViewColumn>同じ幅を持ちます。 既定では、各列の幅がコンテンツに合わせて調整されます。 列を固定幅に設定することもできます。  
  
 関連するデータのコンテンツは水平方向の行に表示されます。 たとえば前の図では、各従業員の姓と名と ID 番号が横一列に並ぶため 1 つのセットとして表示されています。  
  
<a name="DefiningandStylingColumnsinaGridView"></a>   
### <a name="defining-and-styling-columns-in-a-gridview"></a>GridView の列の定義およびスタイル設定  
 表示するデータ フィールドを定義するときに、<xref:System.Windows.Controls.GridViewColumn>を使用して、 <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>、 <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>、または<xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A>プロパティです。 <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>プロパティ テンプレートのプロパティのいずれかのよりも優先されます。  
  
 列のコンテンツの配置を指定する、 <xref:System.Windows.Controls.GridView>、定義、<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>です。 使用しないでください、<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>と<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>プロパティ<xref:System.Windows.Controls.ListView>を使用して表示されるコンテンツ、<xref:System.Windows.Controls.GridView>です。  
  
 列ヘッダーのテンプレートとスタイルのプロパティを指定するには、使用、 <xref:System.Windows.Controls.GridView>、 <xref:System.Windows.Controls.GridViewColumn>、および<xref:System.Windows.Controls.GridViewColumnHeader>クラスです。 詳細については、[GridView の列ヘッダーのスタイルとテンプレートの概要](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md)を参照してください。  
  
<a name="AddingVisualElementstoaGridViewView"></a>   
### <a name="adding-visual-elements-to-a-gridview"></a>GridView への視覚的要素の追加  
 などの視覚要素を追加する<xref:System.Windows.Controls.CheckBox>と<xref:System.Windows.Controls.Button>コントロールに、<xref:System.Windows.Controls.GridView>モードのビューで、テンプレートまたはスタイルを使用します。  
  
 1 回だけを表示できるデータ項目として明示的に視覚的要素を定義する場合、<xref:System.Windows.Controls.GridView>です。 この制限が存在する理由は 1 つの要素は 1 つの親しか持てないためです。したがって視覚的要素をビジュアル ツリーに 1 回だけ表示できます。  
  
<a name="StylingRowsinaGridViewView"></a>   
### <a name="styling-rows-in-a-gridview"></a>GridView での行のスタイル設定  
 使用して、<xref:System.Windows.Controls.GridViewRowPresenter>と<xref:System.Windows.Controls.GridViewHeaderRowPresenter>書式設定および行を表示するクラス、<xref:System.Windows.Controls.GridView>です。 スタイルの行に方法の例については、<xref:System.Windows.Controls.GridView>モードを表示しを参照してください[ListView を実装する GridView で行をスタイル](../../../../docs/framework/wpf/controls/how-to-style-a-row-in-a-listview-that-implements-a-gridview.md)です。  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>   
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>ItemContainerStyle 使用時の配置問題  
 列ヘッダーとセルの配置の問題を防ぐためには、プロパティを設定またはしないテンプレート内のアイテムの幅に影響を指定する、<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>です。 たとえば、設定しないでください、<xref:System.Windows.FrameworkElement.Margin%2A>プロパティかを指定、<xref:System.Windows.Controls.ControlTemplate>を追加、<xref:System.Windows.Controls.CheckBox>を<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>で定義されている、<xref:System.Windows.Controls.ListView>コントロール。 代わりに、指定のプロパティと列の幅を定義するクラスに影響を与えるテンプレート、<xref:System.Windows.Controls.GridView>表示モード。  
  
 例については、追加する、<xref:System.Windows.Controls.CheckBox>内の行に<xref:System.Windows.Controls.GridView>モードを表示、追加、<xref:System.Windows.Controls.CheckBox>を<xref:System.Windows.DataTemplate>、し、設定、<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>にプロパティ<xref:System.Windows.DataTemplate>です。  
  
<a name="InteractingwithaGridViewControl"></a>   
## <a name="user-interactions-with-a-gridview"></a>ユーザーによる GridView の操作  
 使用すると、 <xref:System.Windows.Controls.GridView> 、アプリケーションでユーザーが対話および変更の書式設定、<xref:System.Windows.Controls.GridView>です。 たとえばユーザーは、列の順序の変更、列のサイズの変更、テーブルのアイテムの選択、コンテンツのスクロールを実行できます。 ユーザーが列ヘッダーのボタンをクリックしたときに応答するイベント ハンドラーを定義することもできます。 イベント ハンドラーに表示されるデータの並べ替えのように操作を実行できる、<xref:System.Windows.Controls.GridView>列の内容に従ってします。  
  
 次の一覧でさらに詳しくを使用しての機能について説明します<xref:System.Windows.Controls.GridView>ユーザーの操作。  
  
-   **ドラッグ アンド ドロップで列の順序を変更する**  
  
     ユーザーが内の列を並べ替えることができます、<xref:System.Windows.Controls.GridView>が列見出しの上でマウスの左ボタンを押すと、新しい位置にその列をドラッグし、します。 ユーザーが列ヘッダーをドラッグしている間、そのヘッダーの浮動バージョンと、列を挿入する場所を示す黒い実線が表示されます。  
  
     ヘッダーの浮動小数点バージョンの既定のスタイルを変更する場合は、指定、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.GridViewColumnHeader>となる型トリガーされたときに、<xref:System.Windows.Controls.GridViewColumnHeader.Role%2A>プロパティに設定されている<xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>です。 詳細については、[ドラッグした GridView 列ヘッダーのスタイルを作成する](../../../../docs/framework/wpf/controls/how-to-create-a-style-for-a-dragged-gridview-column-header.md)を参照してください。  
  
-   **内容に合わせて列のサイズを変更する**  
  
     ユーザーは列ヘッダーの右側にあるグリッパーをダブルクリックすると、内容に合わせて列のサイズを変更できます。  
  
    > [!NOTE]
    >  設定することができます、<xref:System.Windows.Controls.GridViewColumn.Width%2A>プロパティを`Double.NaN`を同じ効果を生成します。  
  
-   **行の項目を選択する**  
  
     内の 1 つまたは複数の項目を選択できる、<xref:System.Windows.Controls.GridView>です。  
  
     変更する場合、<xref:System.Windows.Style>のアイテムを選択し、次を参照してください。 [ListView で選択した項目のスタイルを使用してトリガー](../../../../docs/framework/wpf/controls/how-to-use-triggers-to-style-selected-items-in-a-listview.md)です。  
  
-   **スクロールして画面に表示されていない内容を表示する**  
  
     場合のサイズ、<xref:System.Windows.Controls.GridView>がないのに十分な大きさのすべての項目を表示する、ユーザーが水平方向にスクロールまたは垂直方向にスクロール バーを使用すると、これによって提供される、<xref:System.Windows.Controls.ScrollViewer>コントロール。 A<xref:System.Windows.Controls.Primitives.ScrollBar>は、すべてのコンテンツが特定の方向に表示されている場合に表示されません。 列ヘッダーは、垂直スクロール バーでのスクロール操作ではなく水平方向のスクロール操作を行います。  
  
-   **列ヘッダーのボタンをクリックして列を操作する**  
  
     ユーザーは並べ替えアルゴリズムを指定しておけば、列ヘッダーのボタンをクリックして列に表示されているデータを並べ替えることができます。  
  
     処理することができます、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>並べ替えアルゴリズムなどの機能を提供するために列ヘッダーのボタンのイベントです。 処理するために、 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 、1 つの列ヘッダーのイベントにイベント ハンドラーを設定する、<xref:System.Windows.Controls.GridViewColumnHeader>です。 処理するイベント ハンドラーを設定する、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>すべての列ヘッダーのイベントのハンドラーを設定する、<xref:System.Windows.Controls.ListView>コントロール。  
  
<a name="Obtaining_Other_Custom_Views"></a>   
## <a name="obtaining-other-custom-views"></a>その他のカスタム ビューの取得  
 <xref:System.Windows.Controls.GridView>から派生するクラス、<xref:System.Windows.Controls.ViewBase>抽象クラスでは 1 つの可能な表示モード、<xref:System.Windows.Controls.ListView>クラスです。 他のカスタム ビューを作成する<xref:System.Windows.Controls.ListView>から派生することによって、<xref:System.Windows.Controls.ViewBase>クラスです。 カスタム ビュー モードの例については、[ListView のカスタム ビュー モードを作成する](../../../../docs/framework/wpf/controls/how-to-create-a-custom-view-mode-for-a-listview.md)を参照してください。  
  
<a name="GridViewSupportingClasses"></a>   
## <a name="gridview-supporting-classes"></a>GridViewサポート クラス  
 次のクラスのサポート、<xref:System.Windows.Controls.GridView>表示モード。  
  
-   <xref:System.Windows.Controls.GridViewColumn>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeader>  
  
-   <xref:System.Windows.Controls.GridViewRowPresenter>  
  
-   <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
  
-   <xref:System.Windows.Controls.GridViewColumnCollection>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.ListViewItem>  
 <xref:System.Windows.Controls.GridViewColumn>  
 <xref:System.Windows.Controls.GridViewColumnHeader>  
 <xref:System.Windows.Controls.GridViewRowPresenter>  
 <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
 <xref:System.Windows.Controls.ViewBase>  
 [ListView の概要](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [ヘッダーがクリックされたときに GridView 列を並べ替える](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)  
 [方法トピック](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
