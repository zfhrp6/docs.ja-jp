---
title: "データ バインドの概要 | Microsoft Docs"
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
  - "バインド (データを), 概要 (データ バインディングの)"
  - "変換 (データ バインディングのための)"
  - "データ バインディング, 概要 (データ バインディングの)"
  - "データ変換 (バインディングのための)"
ms.assetid: c707c95f-7811-401d-956e-2fffd019a211
caps.latest.revision: 78
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 75
---
# データ バインドの概要
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] データ バインディングは、アプリケーションがデータを提示し、データと対話するための簡単で一貫性のある方法を提供します。  要素は、[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] オブジェクトや [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] の形式のさまざまなデータ ソースのデータにバインドできます。  <xref:System.Windows.Controls.Button> などの <xref:System.Windows.Controls.ContentControl> と、<xref:System.Windows.Controls.ListBox> や <xref:System.Windows.Controls.ListView> などの <xref:System.Windows.Controls.ItemsControl> には、単一のデータ項目やデータ項目のコレクションのスタイルを柔軟に設定できるようにするための機能が組み込まれています。  データの最上位に並べ替え、フィルター、およびグループ ビューを生成できます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のデータ バインディング機能には、従来のモデルに比べていくつかの利点があります。たとえば、データ バインディングをネイティブにサポートするさまざまなプロパティ、データの柔軟な [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 表現、ビジネス ロジックと [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] の明確な分離などです。  
  
 このトピックでは、最初に [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] データ バインディングの基本的な概念について説明し、次に <xref:System.Windows.Data.Binding> クラスの使用方法とデータ バインディングのその他の機能について説明します。  
  
   
  
<a name="what_is_data_binding"></a>   
## データ バインディングとは  
 データ バインディングとは、アプリケーションの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] とビジネス ロジックを関連付けるプロセスです。  バインディングが適切に設定されており、データが適切な通知を提供する場合、データの値が変更されると、データにバインドされている要素にその変更が自動的に反映されます。  また、データ バインディングは、要素内のデータの外部表現が変更された場合、基になるデータが自動的に更新されてその変更が反映されるということも意味します。  たとえば、ユーザーが <xref:System.Windows.Controls.TextBox> 要素の値を編集した場合、基になるデータの値が自動的に更新されてその変更が反映されます。  
  
 データ バインディングの代表的な用途としては、サーバーまたはローカルの構成データをフォームなどの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] コントロールに配置することです。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、この概念が、さまざまなプロパティとさまざまなデータ ソースのバインディングにまで拡張されています。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、要素の[依存関係プロパティ](GTMT)を、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] オブジェクト \([!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] オブジェクトや、Web サービスおよび Web プロパティに関連するオブジェクトなど\) や [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データにバインドできます。  
  
 データ バインディングの例としては、次のアプリケーション [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を[データ バインディングのデモ](http://go.microsoft.com/fwlink/?LinkID=163703)からダウンロードして参照してください。  
  
 ![データ バインディングのサンプルのスクリーンショット](../../../../docs/framework/wpf/data/media/databinding-databindingdemo.png "DataBinding\_DataBindingDemo")  
  
 上の図は、オークション品目の一覧を表示するアプリケーションの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] です。  このアプリケーションでは、次のデータ バインディングの機能を示します。  
  
-   <xref:System.Windows.Controls.ListBox> のコンテンツは、*AuctionItem* オブジェクトのコレクションにバインドされています。  *AuctionItem* オブジェクトには、*Description*、*StartPrice*、*StartDate*、*Category*、*SpecialFeatures* などのプロパティがあります。  
  
-   <xref:System.Windows.Controls.ListBox> に表示されるデータ \(*AuctionItem* オブジェクト\) は、各品目の説明と現在の価格が表示されるようにテンプレート化されています。  このテンプレート化には <xref:System.Windows.DataTemplate> を使用しています。  また、各品目の外観は、表示されている *AuctionItem* の *SpecialFeatures* 値に依存します。  *AuctionItem* の *SpecialFeatures* 値が *Color* の場合は、品目の境界線が青色になります。  値が *Highlight* の場合は、品目の境界線がオレンジ色になり、項目に星が表示されます。  データ テンプレートに関する情報については、「[データ テンプレート](#data_templating)」セクションで説明します。  
  
-   ユーザーは、画面上にある <xref:System.Windows.Controls.CheckBox> を使用して、データのグループ化、フィルター処理、または並べ替えを行うことができます。  上のイメージでは、\[Group by category\] と \[Sort by category and date\] の <xref:System.Windows.Controls.CheckBox> がオンになっています。  商品のカテゴリを基にデータがグループ化されており、カテゴリ名がアルファベット順になっています。  このイメージからはわかりづらいですが、各カテゴリ内の品目は開始日で並べ替えられています。  この並べ替えにはコレクション ビューを使用しています。  コレクション ビューについては、「[コレクションへのバインディング](#binding_to_collections)」セクションで説明します。  
  
-   ユーザーが品目を選択すると、その品目の詳細が <xref:System.Windows.Controls.ContentControl> に表示されます。  これはマスター詳細シナリオと呼ばれます。  この種のバインディング シナリオに関する情報については、「[マスター詳細シナリオ](#master_detail_scenario)」セクションで説明します。  
  
-   *StartDate* プロパティの型は <xref:System.DateTime> です。この型は、ミリ秒までの時刻を含む日付を返します。  このアプリケーションでは、カスタム コンバーターが使用されているため、短い形式の日付文字列が表示されます。  これらのコンバーターに関する情報については、「[データ変換](#data_conversion)」セクションで説明します。  
  
 ユーザーが \[Add Product\] ボタンをクリックすると、次のフォームが表示されます。  
  
 ![&#91;Add Product Listing&#93; ページ](../../../../docs/framework/wpf/data/media/databinding-demo-addproductlisting.png "DataBinding\_Demo\_AddProductListing")  
  
 ユーザーは、フォーム内のフィールドを編集し、簡単なプレビュー ペインと詳細なプレビュー ペインで商品一覧をプレビューしてから、\[submit\] をクリックして新しい商品一覧を追加することができます。  既存のグループ化、フィルター処理、および並べ替えの機能が新しいエントリに適用されます。  この場合、上のイメージに入力した品目は、Computer カテゴリ内の 2 番目の品目として表示されます。  
  
 このイメージでは、*Start Date* <xref:System.Windows.Controls.TextBox> で指定されている検証ロジックが示されていません。  ユーザーが無効な日付 \(無効な形式または過去の日付\) を入力した場合は、日付が無効であることが、<xref:System.Windows.Controls.ToolTip> と <xref:System.Windows.Controls.TextBox> の横の赤い感嘆符でユーザーに通知されます。  検証ロジックの作成方法については、「[データの検証](#data_validation)」セクションで説明します。  
  
 上であらましを述べたさまざまなデータ バインディング機能について説明する前に、次のセクションでは、まず [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] データ バインディングを理解するのに不可欠な基本的概念について説明します。  
  
<a name="basic_data_binding_concepts"></a>   
## 基本的なデータ バインディングの概念  
   
  
 バインドする要素の種類やデータ ソースの性質に関係なく、各バインディングは常に、次の図に示されているモデルに従って行われます。  
  
 ![基本的なデータ バインディング ダイアグラム](../../../../docs/framework/wpf/data/media/databindingmostbasic.png "DataBindingMostBasic")  
  
 上の図に示されているように、データ バインディングは、基本的に[バインディング ターゲット](GTMT)と[バインディング ソース](GTMT)間のブリッジです。  この図は、次の基本的な [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] データ バインディングの概念を示しています。  
  
-   通常、各バインディングには、[バインディング ターゲット](GTMT) オブジェクト、ターゲット プロパティ、[バインディング ソース](GTMT)、および使用する[バインディング ソース](GTMT)内の値へのパスの 4 つのコンポーネントがあります。  たとえば、<xref:System.Windows.Controls.TextBox> の内容を *Employee* オブジェクトの *Name* プロパティにバインドする場合、対象オブジェクトは <xref:System.Windows.Controls.TextBox>、対象プロパティは <xref:System.Windows.Controls.TextBox.Text%2A> プロパティ、使用する値は *Name*、ソース オブジェクトは *Employee* オブジェクトになります。  
  
-   ターゲット プロパティには、[依存関係プロパティ](GTMT)を指定する必要があります。  <xref:System.Windows.UIElement> のほとんどのプロパティは[依存関係プロパティ](GTMT)であり、読み取り専用のものを除くほとんどの[依存関係プロパティ](GTMT)は、既定でデータ バインディングをサポートします   \(<xref:System.Windows.DependencyObject> 型だけが[依存関係プロパティ](GTMT)、および <xref:System.Windows.DependencyObject> から派生したすべての <xref:System.Windows.UIElement> を定義できます\)。  
  
-   図には示されていませんが、[バインディング ソース](GTMT) オブジェクトはカスタムの [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] オブジェクトであってもかまいません。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のデータ バインディングでは、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] オブジェクトおよび [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] の形式のデータをサポートします。  いくつか例を挙げると、バインディング ソースは <xref:System.Windows.UIElement>、任意のリスト オブジェクト、[!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] データまたは Web サービスに関連付けられた [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] オブジェクト、または [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データを含む XmlNode のいずれでもかまいません。  詳細については、「[バインディング ソースの概要](../../../../docs/framework/wpf/data/binding-sources-overview.md)」を参照してください。  
  
 バインディングを確立する場合、[バインディング ターゲット](GTMT)を[バインディング ソース](GTMT)にバインドします。[!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] の他のトピックに目を通す際には、この点を覚えておくことが重要です。  たとえば、データ バインディングを使用して基になる [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データを <xref:System.Windows.Controls.ListBox> に表示する場合は、<xref:System.Windows.Controls.ListBox> を [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データにバインドします。  
  
 バインディングを確立するには、<xref:System.Windows.Data.Binding> オブジェクトを使用します。  以降では、<xref:System.Windows.Data.Binding> オブジェクトに関連するさまざまな概念と、このオブジェクトのいくつかのプロパティおよび使用方法について説明します。  
  
<a name="direction_of_data_flow"></a>   
### データ フローの方向  
 既に説明し、上の図の矢印でも示したように、バインディングのデータ フローには、[バインディング ターゲット](GTMT)から[バインディング ソース](GTMT)へのフロー \(ユーザーが <xref:System.Windows.Controls.TextBox> の値を編集したときのソース値の変更など\) と、バインディング ソースが適切な通知を提供する場合の[バインディング ソース](GTMT)から[バインディング ターゲット](GTMT)へのフロー \([バインディング ソース](GTMT)の変更による <xref:System.Windows.Controls.TextBox> の更新など\) があります。  
  
 アプリケーションでユーザーによるデータの変更を可能にし、その変更をソース オブジェクトに反映できるようにする必要が生じる場合があります。  あるいは、ユーザーがソース データを更新できないようにする必要が生じることもあります。  <xref:System.Windows.Data.Binding> オブジェクトの <xref:System.Windows.Data.Binding.Mode%2A> プロパティを設定することで、こうした動作を制御することができます。  次の図は、さまざまな種類のデータ フローを示しています。  
  
 ![データ バインディング データ フロー](../../../../docs/framework/wpf/data/media/databinding-dataflow.png "DataBinding\_DataFlow")  
  
-   <xref:System.Windows.Data.BindingMode> バインディングでは、ソース プロパティが変更されると、ターゲット プロパティも自動的に更新されます。ただし、ターゲット プロパティの変更はソース プロパティに反映されません。  この型のバインディングは、バインドされているコントロールが暗黙的な読み取り専用の場合に適しています。  たとえば、株価情報などのソースにバインドする場合です。また、ターゲット プロパティには、データ バインドされたテーブルの背景色などの変更用コントロール インターフェイスがない可能性もあります。  ターゲット プロパティの変更を監視する必要がない場合は、<xref:System.Windows.Data.BindingMode> バインディング モードを使うことにより、<xref:System.Windows.Data.BindingMode> バインディング モードのオーバーヘッドを回避できます。  
  
-   <xref:System.Windows.Data.BindingMode> バインディングでは、ソース プロパティまたはターゲット プロパティのどちらか一方が変更されると、もう一方も自動的に更新されます。  この型のバインディングは、編集可能なフォームや完全対話型の [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] シナリオに適しています。  ほとんどのプロパティは既定で <xref:System.Windows.Data.BindingMode> バインディングになります。ただし、一部の[依存関係プロパティ](GTMT) \(一般的に、<xref:System.Windows.Controls.TextBox> の <xref:System.Windows.Controls.TextBox.Text%2A> プロパティや <xref:System.Windows.Controls.CheckBox> の <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> プロパティなど、ユーザーが編集できるコントロールのプロパティ\) は既定で <xref:System.Windows.Data.BindingMode> バインディングになります。  [依存関係プロパティ](GTMT)が既定で一方向または双方向のいずれであるかをプログラムにより判断する 1 つの方法は、<xref:System.Windows.DependencyProperty.GetMetadata%2A> を使用してプロパティのプロパティ メタデータを取得してから、<xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A> プロパティのブール値を確認することです。  
  
-   <xref:System.Windows.Data.BindingMode> は <xref:System.Windows.Data.BindingMode> バインディングの逆方向のバインディングです。このバインディングでは、ターゲット プロパティが変更されると、ソース プロパティが更新されます。  シナリオの例の 1 つには、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] からのソース値のみを再評価する必要がある場合があります。  
  
-   図に示されていない <xref:System.Windows.Data.BindingMode> バインディングでは、ソース プロパティによってターゲット プロパティが初期化されます。ただし、それ以降の変更は反映されません。  これは、データ コンテキストまたはデータ コンテキスト内のオブジェクトが変更された場合、その変更はターゲット プロパティに反映されないということを意味します。  この型のバインディングは、現在の状態のスナップショットを使用した方がよい場合や、データが完全に静的である場合に適しています。  また、ソース プロパティの値を使用してターゲット プロパティを初期化するときにデータ コンテキストが事前にわからない場合にも、この型のバインディングは便利です。  基本的に、この型のバインディングは、ソース値が変わらない場合にパフォーマンスを向上させる <xref:System.Windows.Data.BindingMode> バインディングを簡易化したものです。  
  
 ソースの変更を検出するには \(<xref:System.Windows.Data.BindingMode> および <xref:System.Windows.Data.BindingMode> バインディングが該当\)、ソースで <xref:System.ComponentModel.INotifyPropertyChanged> などの適切なプロパティの変更通知機構を実装する必要があります。  <xref:System.ComponentModel.INotifyPropertyChanged> の実装の例については、「[プロパティの変更通知を実装する](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md)」を参照してください。  
  
 バインディング モードの詳細とバインディングの方向を指定する方法の例については、<xref:System.Windows.Data.Binding.Mode%2A> プロパティのページを参照してください。  
  
<a name="what_triggers_source_updates"></a>   
### ソースの更新の要因  
 <xref:System.Windows.Data.BindingMode> または <xref:System.Windows.Data.BindingMode> のバインディングでは、対象プロパティ内の変更をリッスンして、ソースに反映させます。  これを、ソースの更新と呼びます。  たとえば、TextBox のテキストを編集して、基になるソース値を変更できます。  前のセクションで説明したように、データ フローの方向は、バインディングの <xref:System.Windows.Data.Binding.Mode%2A> プロパティの値によって決定されます。  
  
 では、ソース値はテキストの編集中に更新されるのでしょうか。それとも、テキストの編集を終了し、マウスのポインターを TextBox から離した後に更新されるのでしょうか。  ソースの更新の要因は、バインディングの <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> プロパティによって決定されます。  次の図の点線の右矢印は、<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> プロパティの役割を示しています。  
  
 ![UpdateSourceTrigger ダイアグラム](../../../../docs/framework/wpf/data/media/databindingupdatesourcetrigger.png "DataBindingUpdateSourceTrigger")  
  
 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 値が <xref:System.Windows.Data.UpdateSourceTrigger> の場合、<xref:System.Windows.Data.BindingMode> バインディングまたは <xref:System.Windows.Data.BindingMode> バインディングの右矢印が指す値は、ターゲット プロパティが変更された直後に更新されます。  一方、<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 値が <xref:System.Windows.Data.UpdateSourceTrigger> の場合、この値が新しい値に更新されるのは、ターゲット プロパティがフォーカスを失ったときだけです。  
  
 <xref:System.Windows.Data.Binding.Mode%2A> プロパティと同様に、[依存関係プロパティ](GTMT)の既定の <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 値は、依存関係プロパティごとに異なります。  ほとんどの[依存関係プロパティ](GTMT)の既定値は <xref:System.Windows.Data.UpdateSourceTrigger> であるのに対し、<xref:System.Windows.Controls.TextBox.Text%2A> プロパティの既定値は <xref:System.Windows.Data.UpdateSourceTrigger> です。  つまり、通常はターゲット プロパティの変更時にソースが更新されます。こうした動作は、<xref:System.Windows.Controls.CheckBox> などの単純なコントロールに適しています。  ただし、テキスト フィールドの場合、各キーストロークの後に更新を行うと、パフォーマンスが低下する可能性があり、ユーザーは新しい値をコミットする前に BackSpace キーを使用して入力エラーを修正するという通常の操作ができなくなります。  <xref:System.Windows.Controls.TextBox.Text%2A> プロパティの既定値が、<xref:System.Windows.Data.UpdateSourceTrigger> ではなく <xref:System.Windows.Data.UpdateSourceTrigger> に設定されているのはこのためです。  
  
 [依存関係プロパティ](GTMT)の既定の <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 値を確認する方法については、<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> プロパティのページを参照してください。  
  
 次の表は、各 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 値のシナリオ例を示しています。これらのシナリオでは、<xref:System.Windows.Controls.TextBox> を例として使用しています。  
  
|UpdateSourceTrigger 値|ソース値が更新されるタイミング|TextBox のシナリオ例|  
|---------------------------|---------------------|--------------------|  
|LostFocus \(<xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=fullName> の既定値\)|TextBox コントロールがフォーカスを失ったとき|検証ロジックに関連付けられている <xref:System.Windows.Controls.TextBox> \(「データの検証」セクションを参照\)|  
|PropertyChanged|<xref:System.Windows.Controls.TextBox> に入力したとき|チャット ルーム ウィンドウの <xref:System.Windows.Controls.TextBox> コントロール|  
|Explicit|アプリケーションが <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> を呼び出したとき|編集可能なフォームの <xref:System.Windows.Controls.TextBox> コントロール \(ユーザーが送信ボタンをクリックした場合のみソース値を更新する\)|  
  
 例については、「[TextBox テキストでソースを更新するタイミングを制御する](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)」を参照してください。  
  
<a name="creating_a_binding"></a>   
## バインディングの作成  
   
  
 前のセクションで説明したいくつかの概念を要約するために、<xref:System.Windows.Data.Binding> を使用してバインディングを設定します。通常、各バインディングには、バインディング ターゲット、ターゲット プロパティ、バインディング ソース、および使用するソース値へのパスの 4 つのコンポーネントがあります。  このセクションでは、バインディングの設定方法について説明します。  
  
 次に例を示します。この例では、*SDKSample* 名前空間内で定義されている *MyData* という名前のクラスをバインディング ソース オブジェクトに設定しています。  デモの目的で、*MyData* クラスは *ColorName* という名前の文字列プロパティを持っており、プロパティの値は "Red" に設定されています。  したがって、この例では赤い背景のボタンが作成されます。  
  
 [!code-xml[BindNonTextProperty#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page1.xaml#1)]  
  
 バインディング宣言構文の詳細とコードでバインディングを設定する方法の例については、「[バインディング宣言の概要](../../../../docs/framework/wpf/data/binding-declarations-overview.md)」を参照してください。  
  
 上の基本的な図にこの例を適用すると、次のような図が得られます。  Background プロパティは既定で <xref:System.Windows.Data.BindingMode> バインディングをサポートするため、これは <xref:System.Windows.Data.BindingMode> バインディングになります。  
  
 ![データ バインディング ダイアグラム](../../../../docs/framework/wpf/data/media/databindingbuttonbackgroundexample.png "DataBindingButtonBackgroundExample")  
  
 *ColorName* プロパティは文字列型で <xref:System.Windows.Controls.Control.Background%2A> プロパティは <xref:System.Windows.Media.Brush> 型であるにもかかわらず、このバインディングが正常に機能することに疑問を持たれるかもしれません。  これは既定の型変換が実行されるためです。型変換については「[データ変換](#data_conversion)」セクションで説明します。  
  
<a name="specifying_the_binding_source"></a>   
### バインディング ソースの指定  
 前の例では、<xref:System.Windows.Controls.DockPanel> 要素の <xref:System.Windows.FrameworkElement.DataContext%2A> プロパティを設定することで、バインディング ソースを指定しています。  次に、<xref:System.Windows.Controls.Button> は、その親要素である <xref:System.Windows.Controls.DockPanel> から <xref:System.Windows.FrameworkElement.DataContext%2A> 値を継承します。  繰り返しますが、バインディング ソース オブジェクトは、バインディングの 4 つの必須コンポーネントの 1 つです。  したがって、バインディング ソース オブジェクトが指定されていない場合、バインディングは機能しません。  
  
 バインディング ソース オブジェクトを指定する方法はいくつかあります。  親要素の <xref:System.Windows.FrameworkElement.DataContext%2A> プロパティを使用する方法は、複数のプロパティを同じソースにバインドする場合に役立ちます。  ただし、個々のバインディング宣言でバインディング ソースを指定する方が適している場合もあります。  前の例の場合は、<xref:System.Windows.FrameworkElement.DataContext%2A> プロパティを使用する代わりに、ボタンのバインディング宣言で直接 <xref:System.Windows.Data.Binding.Source%2A> プロパティを設定することでバインディング ソースを指定できます。次に例を示します。  
  
 [!code-xml[BindNonTextProperty#BackgroundBindingCompact](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindNonTextProperty/CS/Page2.xaml#backgroundbindingcompact)]  
  
 <xref:System.Windows.FrameworkElement.DataContext%2A> プロパティを要素に直接設定したり、<xref:System.Windows.FrameworkElement.DataContext%2A> 値を先祖から継承したり \(最初の例のボタンなど\)、<xref:System.Windows.Data.Binding> の <xref:System.Windows.Data.Binding.Source%2A> プロパティの設定でバインディング ソースを明示的に指定する方法以外に、<xref:System.Windows.Data.Binding.ElementName%2A> プロパティまたは <xref:System.Windows.Data.Binding.RelativeSource%2A> プロパティを使用してバインディング ソースを指定する方法もあります。  <xref:System.Windows.Data.Binding.ElementName%2A> プロパティは、アプリケーション内の他の要素にバインドする場合 \(スライダーを使用してボタンの幅を調整する場合など\) に役立ちます。  <xref:System.Windows.Data.Binding.RelativeSource%2A> プロパティは、<xref:System.Windows.Controls.ControlTemplate> または <xref:System.Windows.Style> でバインディングを指定する場合に役立ちます。  詳細については、「[バインディング ソースを指定する](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)」を参照してください。  
  
<a name="specifying_the_path_to_the_value"></a>   
### 値へのパスの指定  
 バインディング ソースがオブジェクトである場合は、<xref:System.Windows.Data.Binding.Path%2A> プロパティを使用して、バインディングで使用する値を指定します。  [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データにバインドする場合は、<xref:System.Windows.Data.Binding.XPath%2A> プロパティを使用して値を指定します。  場合によっては、データが [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] であっても <xref:System.Windows.Data.Binding.Path%2A> プロパティを使用できます。  たとえば、\(XPath クエリの結果として\) 返された XmlNode の Name プロパティにアクセスする場合は、<xref:System.Windows.Data.Binding.XPath%2A> プロパティに加えて <xref:System.Windows.Data.Binding.Path%2A> プロパティを使用する必要があります。  
  
 構文の詳細および例については、<xref:System.Windows.Data.Binding.Path%2A> プロパティと <xref:System.Windows.Data.Binding.XPath%2A> プロパティのページを参照してください。  
  
 使用する値への <xref:System.Windows.Data.Binding.Path%2A> はバインディングの 4 つの必須コンポーネントの 1 つであると強調しましたが、オブジェクト全体にバインドするシナリオでは、使用する値は[バインディング ソース](GTMT) オブジェクトと同一になります。  このような場合には、<xref:System.Windows.Data.Binding.Path%2A> を指定する必要はありません。  次に例を示します。  
  
 [!code-xml[MasterDetail#EmptyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MasterDetail/CSharp/Page1.xaml#emptybinding)]  
  
 上の例では、空のバインディング構文 \({Binding}\) を使用しています。  この場合、<xref:System.Windows.Controls.ListBox> は、親の DockPanel 要素から DataContext を継承します \(この例には示されていません\)。  パスを指定しない場合、既定でオブジェクト全体にバインドされます。  つまり、この例では、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> プロパティをオブジェクト全体にバインドしているため、パスが省略されたことになります   \(詳細については、「[コレクションへのバインド](#binding_to_collections)」セクションを参照してください\)。  
  
 このシナリオは、コレクションにバインドする場合だけでなく、オブジェクトの単一のプロパティの代わりにオブジェクト全体にバインドする場合にも役立ちます。  たとえば、ソース オブジェクトが文字列型で、その文字列自体にバインドする場合などです。  もう 1 つの一般的なシナリオは、複数のプロパティを持つオブジェクトに要素をバインドする場合です。  
  
 カスタム ロジックを適用して、バインドしたターゲット プロパティでデータが有効になるようにしなければならない場合があることに注意してください。  カスタム ロジックは、カスタム コンバーターの形式になることがあります \(既定の型変換が存在しない場合\)。  コンバーターの詳細については、「[データ変換](#data_conversion)」を参照してください。  
  
<a name="binding_bindingexpression"></a>   
### Binding と BindingExpression  
 データ バインディングのその他の機能と使用方法について説明する前に、<xref:System.Windows.Data.BindingExpression> クラスについて説明した方がよいでしょう。  前のセクションで説明したように、<xref:System.Windows.Data.Binding> クラスは、バインディング宣言で使用する高レベルのクラスです。<xref:System.Windows.Data.Binding> クラスは、バインディングの特性を指定するためのさまざまなプロパティを提供します。  関連クラスである <xref:System.Windows.Data.BindingExpression> クラスは、ソースとターゲットとの関連付けを維持する、基になるオブジェクトです。  バインディングには、複数のバインディング式で共有可能な情報がすべて含まれています。  <xref:System.Windows.Data.BindingExpression> は、共有できないインスタンス式であり、<xref:System.Windows.Data.Binding> に関するインスタンス情報がすべて含まれています。  
  
 次に例を示します。*myDataObject* は *MyData* クラスのインスタンス、*myBinding* は <xref:System.Windows.Data.Binding> ソース オブジェクト、*MyData* クラスは *MyDataProperty* という名前の文字列プロパティを含む定義済みクラスです。  この例では、<xref:System.Windows.Controls.TextBlock> のインスタンスである *mytext* のテキスト コンテンツを、*MyDataProperty* にバインドします。  
  
 [!code-csharp[CodeOnlyBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 同じ *myBinding* オブジェクトを使用して、他のバインディングを作成できます。  たとえば、*myBinding* オブジェクトを使用して、チェック ボックスのテキスト コンテンツを *MyDataProperty* にバインドできます。  このシナリオには、*myBinding* オブジェクトを共有する <xref:System.Windows.Data.BindingExpression> のインスタンスが 2 つあります。  
  
 <xref:System.Windows.Data.BindingExpression> オブジェクトは、データ バインドされたオブジェクト上の <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> を呼び出した結果の戻り値を使用して取得できます。  以下のトピックでは、<xref:System.Windows.Data.BindingExpression> クラスの使用方法の一部を示します。  
  
-   [バインドされているターゲット プロパティからのバインディング オブジェクトの取得](../../../../docs/framework/wpf/data/how-to-get-the-binding-object-from-a-bound-target-property.md)  
  
-   [TextBox テキストでソースを更新するタイミングを制御する](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)  
  
<a name="data_conversion"></a>   
## データ変換  
 前の例では、ボタンの <xref:System.Windows.Controls.Control.Background%2A> プロパティが "Red" という値を持つ文字列プロパティにバインドされているため、ボタンの色が赤になります。  これが機能するのは、文字列値を <xref:System.Windows.Media.Brush> に変換する型コンバーターが <xref:System.Windows.Media.Brush> 型に存在するためです。  
  
 この情報を「[バインディングの作成](#creating_a_binding)」セクションの図に追加すると、次のような図が得られます。  
  
 ![データ バインディング ダイアグラム](../../../../docs/framework/wpf/data/media/databindingbuttondefaultconversion.png "DataBindingButtonDefaultConversion")  
  
 では、文字列型のプロパティの代わりに、<xref:System.Windows.Media.Color> 型の *Color* プロパティがバインディング ソース オブジェクトにある場合はどうなるのでしょうか。  この場合、バインディングを機能させるには、最初に *Color* プロパティの値を、<xref:System.Windows.Controls.Control.Background%2A> で受け入れられる値に変換する必要があります。  次の例に示すように、<xref:System.Windows.Data.IValueConverter> インターフェイスを実装して、カスタム コンバーターを作成する必要があります。  
  
 [!code-csharp[ColorPicker_snip#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColorPicker_snip/CSharp/ColorPickerLib/ColorPicker.cs#16)]
 [!code-vb[ColorPicker_snip#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ColorPicker_snip/visualbasic/colorpickerlib/colorpicker.vb#16)]  
  
 詳細については、<xref:System.Windows.Data.IValueConverter> のリファレンス ページを参照してください。  
  
 ここでは、既定の変換の代わりにカスタム コンバーターを使用します。したがって、上の図は次のようになります。  
  
 ![データ バインディング ダイアグラム](../../../../docs/framework/wpf/data/media/databindingconvertercolorexample.png "DataBindingConverterColorExample")  
  
 繰り返しますが、バインディング ターゲットの型に型コンバーターが存在していれば、既定の変換を使用できる場合があります。  この動作は、ターゲットで使用できる型コンバーターによって異なります。  不確かな場合は、独自のコンバーターを作成してください。  
  
 型コンバーターを実装することが理にかなっている代表的なシナリオとして、以下が挙げられます。  
  
-   カルチャに応じてデータを異なる形式で表示する必要がある場合。  たとえば、特定のカルチャで使用される値や標準を基に、通貨コンバーターやカレンダーの日付\/時刻コンバーターを実装できます。  
  
-   使用中のデータが必ずしもプロパティのテキスト値を変更するためのものではなく、イメージのソースや表示テキストの色またはスタイルなど、その他の値を変更するためのものである場合。  この場合は、コンバーターを使用して、不適切と思われるプロパティのバインディング \(テキスト フィールドとテーブル セルの Background プロパティのバインディングなど\) を変換できます。  
  
-   複数のコントロールまたはコントロールの複数のプロパティを同じデータにバインドする場合。  この場合、同じバインディングをソース情報として使用したまま、プライマリ バインディングでテキストを表示し、その他のバインディングで表示に関する特定の問題を処理することができます。  
  
-   ターゲット プロパティにバインディングのコレクションが含まれる <xref:System.Windows.Data.MultiBinding> \(これについてはまだ説明していません\) を使用する場合。  <xref:System.Windows.Data.MultiBinding> の場合は、カスタム <xref:System.Windows.Data.IMultiValueConverter> を使用して、バインディングの値から最終的な値を生成します。  たとえば、同じまたは異なるバインディング ソース オブジェクトの値である赤、青、緑の値から色の値を計算できます。  例および詳細については、<xref:System.Windows.Data.MultiBinding> クラスのページを参照してください。  
  
<a name="binding_to_collections"></a>   
## コレクションへのバインド  
   
  
 バインディング ソース オブジェクトは、プロパティにデータが含まれる単一のオブジェクト、または \(データベースへのクエリの結果など\) 通常はグループ化されるポリモーフィック オブジェクトのデータ コレクションのいずれかとして処理することができます。  これまでは単一オブジェクトへのバインディングについてのみ説明してきましたが、データ コレクションへのバインディングも一般的なシナリオです。  たとえば、一般的なシナリオでは、「[データ バインディングとは](#what_is_data_binding)」セクションで示したアプリケーションのように、<xref:System.Windows.Controls.ListBox>、<xref:System.Windows.Controls.ListView>、<xref:System.Windows.Controls.TreeView> などの <xref:System.Windows.Controls.ItemsControl> を使用してデータ コレクションを表示します。  
  
 幸いなことに、上の基本的な図を引き続き適用できます。  <xref:System.Windows.Controls.ItemsControl> をコレクションにバインドしている場合、この図は次のようになります。  
  
 ![データ バインディング ItemsControl ダイアグラム](../../../../docs/framework/wpf/data/media/databindingitemscontrol.png "DataBindingItemsControl")  
  
 この図に示されているように、コレクション オブジェクトに <xref:System.Windows.Controls.ItemsControl> をバインドする場合、使用するプロパティは <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> プロパティです。  <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> プロパティは、<xref:System.Windows.Controls.ItemsControl> のコンテンツと考えることができます。  <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> プロパティは、既定では、<xref:System.Windows.Data.BindingMode> バインディングをサポートします。したがって、バインディングは <xref:System.Windows.Data.BindingMode> になることに注意してください。  
  
<a name="how_to_implement_collections"></a>   
### コレクションを実装する方法  
 <xref:System.Collections.IEnumerable> インターフェイスを実装するすべてのコレクションを列挙できます。  ただし、コレクションへの挿入や削除によって [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] が自動的に更新されるように動的バインディングを設定するには、コレクションで <xref:System.Collections.Specialized.INotifyCollectionChanged> インターフェイスを実装する必要があります。  このインターフェイスは、基になるコレクションが変更されるたびに発生するイベントを公開します。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、<xref:System.Collections.Specialized.INotifyCollectionChanged> インターフェイスを公開するデータ コレクションの組み込み実装である <xref:System.Collections.ObjectModel.ObservableCollection%601> クラスを提供します。  ソース オブジェクトからターゲットへのデータ値の転送を完全にサポートするためには、バインド可能なプロパティをサポートするコレクション内の各オブジェクトに <xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスも実装する必要があります。  詳細については、「[バインディング ソースの概要](../../../../docs/framework/wpf/data/binding-sources-overview.md)」を参照してください。  
  
 独自のコレクションを実装する前に、<xref:System.Collections.ObjectModel.ObservableCollection%601> または既存のコレクション クラスのいずれか \(特に <xref:System.Collections.Generic.List%601>、<xref:System.Collections.ObjectModel.Collection%601>、<xref:System.ComponentModel.BindingList%601> など\) の使用を検討します。  高度なシナリオがあり、独自のコレクションを実装する場合は、<xref:System.Collections.IList> の使用を検討してください。これにより、インデックスによって個別にアクセスできるオブジェクトの非ジェネリック コレクションが利用可能になり、最適なパフォーマンスが実現されます。  
  
<a name="collection_views"></a>   
### コレクション ビュー  
 <xref:System.Windows.Controls.ItemsControl> をデータ コレクションにバインドすると、データの並べ替え、フィルター処理、またはグループ化が必要になる場合があります。  これらの処理を実行するには、<xref:System.ComponentModel.ICollectionView> インターフェイスを実装したクラスであるコレクション ビューを使用します。  
  
   
  
<a name="what_are_collection_views"></a>   
#### コレクション ビューとは  
 コレクション ビューは、基になるソース コレクションそのものを操作せずに、並べ替え、フィルター、およびグループ クエリに基づいてソース コレクションを移動および表示できるようにする、バインディング ソース コレクションの最上位層です。  また、コレクション ビューは、コレクション内の現在の項目へのポインターを維持します。  ソース コレクションが <xref:System.Collections.Specialized.INotifyCollectionChanged> インターフェイスを実装している場合は、<xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> イベントによって発生した変更がビューに反映されます。  
  
 ビューは基になるソース コレクションを変更しないため、各ソース コレクションは関連付けられた複数のビューを持つことができます。  たとえば、*Task* オブジェクトのコレクションを持つことができます。  ビューを使用することにより、同じデータを異なる方法で表示できます。  たとえば、優先順位で並べ替えたタスクをページの左側に表示し、領域ごとにグループ化されたタスクをページの右側に表示できます。  
  
<a name="how_to_create_a_view"></a>   
#### ビューを作成する方法  
 ビューを作成および使用する方法の 1 つは、ビュー オブジェクトを直接インスタンス化し、それをバインディング オブジェクトとして使用することです。  たとえば、「[データ バインディングとは](#what_is_data_binding)」セクションで示した[データ バインディングのデモ](http://go.microsoft.com/fwlink/?LinkID=163703) アプリケーションを参照してください。  このアプリケーションは、<xref:System.Windows.Controls.ListBox> をデータ コレクションに直接バインドするのではなく、データ コレクション上のビューにバインドするように実装されています。  次の例は、[データ バインディングのデモ](http://go.microsoft.com/fwlink/?LinkID=163703) アプリケーションから抽出したものです。  <xref:System.Windows.Data.CollectionViewSource> クラスは、<xref:System.Windows.Data.CollectionView> から継承するクラスの [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] プロキシです。  この例では、現在のアプリケーション オブジェクトの *AuctionItems* コレクション \(<xref:System.Collections.ObjectModel.ObservableCollection%601> 型\) に、ビューの <xref:System.Windows.Data.CollectionViewSource.Source%2A> をバインドしています。  
  
 [!code-xml[DataBindingLab#WindowResources1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources1)]  
[!code-xml[DataBindingLab#CollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#collectionviewsource)]  
[!code-xml[DataBindingLab#WindowResources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#windowresources2)]  
  
 次に、*listingDataView* リソースを、アプリケーション内の要素 \(<xref:System.Windows.Controls.ListBox> など\) のバインディング ソースに設定します。  
  
 [!code-xml[DataBindingLab#Master1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xml[DataBindingLab#Master2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
  
 同じコレクションに対して別のビューを作成するには、別の <xref:System.Windows.Data.CollectionViewSource> インスタンスを作成し、そのインスタンスに異なる `x:Key` 名を付けます。  
  
 次の表は、既定のコレクション ビューとして作成されるビュー データの型、またはソース コレクションの型に基づく <xref:System.Windows.Data.CollectionViewSource> で作成されるビュー データの型を示しています。  
  
|ソース コレクションの型|コレクション ビューの型|説明|  
|------------------|------------------|--------|  
|<xref:System.Collections.IEnumerable>|<xref:System.Windows.Data.CollectionView> に基づく内部型|項目をグループ化できません。|  
|<xref:System.Collections.IList>|<xref:System.Windows.Data.ListCollectionView>|最も高速です。|  
|<xref:System.ComponentModel.IBindingList>|<xref:System.Windows.Data.BindingListCollectionView>||  
  
##### 既定のビューの使用  
 コレクション ビューを作成および使用する 1 つの方法は、コレクション ビューをバインディング オブジェクトとして指定することです。  また、WPF は、バインディング ソースとして使用されるすべてのコレクション用の既定のコレクション ビューを作成します。  コレクションに直接バインドする場合、WPF はその既定のビューにバインドします。  この既定のビューは、同じコレクションへのすべてのバインディングで共有されます。そのため、1 つのバインドされたコントロールまたはコードによって既定のビューに加えられた変更 \(後で説明する、現在の項目のポインターの並べ替えや変更など\) は、同じコレクションへの他のすべてのバインディングにも反映されます。  
  
 既定のビューを取得するには、<xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> メソッドを使用します。  例については、「[データ コレクションの既定のビューを取得する](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)」を参照してください。  
  
##### ADO.NET DataTables を持つコレクション ビュー  
 パフォーマンスを向上させるため、ADO.NET <xref:System.Data.DataTable> オブジェクトまたは <xref:System.Data.DataView> オブジェクトのコレクション ビューは、並べ替えとフィルター処理を <xref:System.Data.DataView> に委任します。  これにより、データ ソースのすべてのコレクション ビューが、並べ替えとフィルター処理を共有するようになります。  各コレクション ビューが個別に並べ替えとフィルター処理を行うことができるようにするには、各コレクション ビューをそれ自体の <xref:System.Data.DataView> オブジェクトで初期化します。  
  
<a name="sorting"></a>   
#### 並べ替え  
 既に説明したように、ビューでは、コレクションに並べ替え順序を適用できます。  基になるコレクションに並べ替え順序が存在している場合、関連する固有の順序がデータに適用されたり適用されなかったりすることがあります。  コレクション上のビューを使用すると、指定した比較条件に基づいて、順序を強制したり既定の順序を変更したりできます。  これはクライアント ベースのデータ ビューであるため、ユーザーが対応する列の値に応じてテーブル データの列を並べ替える必要がある場合によく使用されます。  ビューを使用すると、こうしたユーザーによる並べ替えを適用できます。この場合も基になるコレクションを変更する必要はありません。また、コレクションのコンテンツに対してクエリを再度実行する必要さえありません。  例については、「[ヘッダーがクリックされたときに GridView 列を並べ替える](../../../../docs/framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md)」を参照してください。  
  
 次の例は、「[データ バインディングとは](#what_is_data_binding)」セクションで示したアプリケーション [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] である \[Sort by category and date\] <xref:System.Windows.Controls.CheckBox> の並べ替えロジックを示しています。  
  
 [!code-csharp[DataBindingLab#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#8)]
 [!code-vb[DataBindingLab#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#8)]  
  
<a name="filtering"></a>   
#### フィルター処理  
 ビューでは、コレクションにフィルターを適用することもできます。  つまり、この特定のビューは、コレクションに項目が存在する場合でも、コレクション全体の特定のサブセットのみを表示するためのものです。  データの条件に基づいてフィルター処理することができます。  たとえば、「[データ バインディングとは](#what_is_data_binding)」セクションで示したアプリケーションの \[Show only bargains\] <xref:System.Windows.Controls.CheckBox> には、25 ドル以上の品目をフィルターで除外するロジックが含まれています。  この <xref:System.Windows.Controls.CheckBox> をオンにすると、次のコードが実行され、*ShowOnlyBargainsFilter* が <xref:System.Windows.Data.CollectionViewSource.Filter> イベント ハンドラーとして設定されます。  
  
 [!code-csharp[DataBindingLab#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 *ShowOnlyBargainsFilter* イベント ハンドラーの実装例を次に示します。  
  
 [!code-csharp[DataBindingLab#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
 <xref:System.Windows.Data.CollectionViewSource> の代わりに <xref:System.Windows.Data.CollectionView> クラスのいずれかを直接使用している場合は、<xref:System.Windows.Data.CollectionView.Filter%2A> プロパティを使用してコールバックを指定します。  例については、「[ビュー内のデータをフィルター処理する](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)」を参照してください。  
  
<a name="grouping"></a>   
#### グループ化  
 <xref:System.Collections.IEnumerable> コレクションを表示する内部クラスを除いて、すべてのコレクション ビューがグループ化の機能をサポートします。このため、ユーザーは、コレクション ビュー内でコレクションを論理グループに分割できます。  グループには、ユーザーがグループの一覧を提供する明示的なグループと、データに基づいて動的にグループが生成される暗黙的なグループがあります。  
  
 次の例は、\[Group by category\] <xref:System.Windows.Controls.CheckBox> のロジックを示しています。  
  
 [!code-csharp[DataBindingLab#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#6)]
 [!code-vb[DataBindingLab#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#6)]  
  
 他のグループ化の例については、「[GridView を実装する ListView の項目をグループ化する](../../../../docs/framework/wpf/controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md)」を参照してください。  
  
<a name="current_record_pointers"></a>   
#### 現在の項目のポインター  
 ビューでは、現在の項目の概念もサポートされます。  コレクション ビュー内のオブジェクト間を移動できます。  オブジェクト間を移動するときは、コレクション内の特定の場所に存在するオブジェクトを取得できるようにする項目ポインターを移動しています。  例については、「[データ CollectionView のオブジェクト間を移動する](../../../../docs/framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md)」を参照してください。  
  
 WPF がコレクションにバインドするときは必ずビュー \(ユーザーが指定したビュー、またはコレクションの既定のビュー\) を使用するため、コレクションへのすべてのバインディングには現在の項目のポインターがあります。  ビューにバインドするたきには、`Path` 値のスラッシュ \("\/"\) 文字がそのビューの現在の項目を指定します。  次の例では、データ コンテキストがコレクション ビューになります。  最初の行はコレクションにバインドします。  2 番目の行はコレクション内の現在の項目にバインドします。  3 行目は、コレクション内の現在の項目の `Description` プロパティにバインドします。  
  
```xaml  
<Button Content="{Binding }" />  
<Button Content="{Binding Path=/}" />  
<Button Content="{Binding Path=/Description}" />   
```  
  
 スラッシュとプロパティ構文をスタックして、コレクション階層を走査することもできます。  次の例では、ソース コレクションの現在の項目のプロパティである、`Offices` という名前の、コレクションの現在の項目にバインドします。  
  
```xaml  
<Button Content="{Binding /Offices/}" />  
```  
  
 現在の項目のポインターは、コレクションに適用される並べ替えまたはフィルター処理によって影響を受けることがあります。  並べ替えでは、選択した最後の項目に現在の項目のポインターが維持されますが、コレクション ビューはその項目を中心にして再構築されます   \(リストの先頭にあった、選択された項目が、リストの中央部に移動することが考えられます\)。選択されていた項目がフィルター処理後にビュー内に残っている場合、その項目は保持されます。  それ以外の場合、現在の項目のポインターは、フィルター処理されたコレクション ビューの最初の項目に設定されます。  
  
<a name="master_detail_scenario"></a>   
#### マスター詳細シナリオ  
 現在の項目の概念は、コレクション内の項目間の移動だけでなく、バインディングのマスター詳細シナリオでも役立ちます。  「[データ バインディングとは](#what_is_data_binding)」セクションのアプリケーション [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] をもう一度考えてみましょう。  このアプリケーションでは、<xref:System.Windows.Controls.ListBox> 内の選択内容によって <xref:System.Windows.Controls.ContentControl> に表示されるコンテンツが決定されます。  つまり、<xref:System.Windows.Controls.ListBox> の項目を選択すると、その項目の詳細が <xref:System.Windows.Controls.ContentControl> に表示されます。  
  
 複数のコントロールを同じビューにバインドするだけで、マスター詳細シナリオを実装することができます。  次に示すのは[データ バインディングのデモ](http://go.microsoft.com/fwlink/?LinkID=163703)からの例で、<xref:System.Windows.Controls.ListBox> のマークアップおよび <xref:System.Windows.Controls.ContentControl> です。これらは「[データ バインディングとは](#what_is_data_binding)」セクションのアプリケーション [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] で参照しました。  
  
 [!code-xml[DataBindingLab#Master1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master1)]  
[!code-xml[DataBindingLab#Master2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#master2)]  
[!code-xml[DataBindingLab#Detail](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml#detail)]  
  
 両方のコントロールが同じソース \(*listingDataView* 静的リソース\) にバインドされていることに注意してください \(「[ビューを作成する方法](#how_to_create_a_view)」セクションにあるこのリソースの定義を参照\)。  これが機能するのは、シングルトン オブジェクト \(この場合は <xref:System.Windows.Controls.ContentControl>\) をコレクション ビューにバインドした場合、そのシングルトン オブジェクトが自動的にビューの <xref:System.Windows.Data.CollectionView.CurrentItem%2A> にバインドされるためです。  <xref:System.Windows.Data.CollectionViewSource> オブジェクトによって現在の項目と選択した項目が自動的に同期されることに注意してください。  この例とは異なり、リスト コントロールが <xref:System.Windows.Data.CollectionViewSource> オブジェクトにバインドされない場合は、<xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> プロパティを `true` に設定して、現在の項目と選択した項目が同期されるようにする必要があります。  
  
 その他の例については、「[コレクションにバインドして選択に基づく情報を表示する](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)」および「[階層データでマスター詳細パターンを使用する](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)」を参照してください。  
  
 上記の例ではテンプレートが使用されています。  実際、テンプレート \(<xref:System.Windows.Controls.ContentControl> によって明示的に使用されるテンプレートと <xref:System.Windows.Controls.ListBox> によって暗黙的に使用されるテンプレート\) を使用しない場合、データは意図したとおりの形式で表示されません。  次のセクションでは、データ テンプレートについて説明します。  
  
<a name="data_templating"></a>   
## データ テンプレート  
 データ テンプレートを使用しない場合、「[データ バインディングとは](#what_is_data_binding)」セクションのアプリケーション [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] は、次のようになります。  
  
 ![データ テンプレートのないデータ バインディング デモ](../../../../docs/framework/wpf/data/media/databindingdemotemplates.png "DataBindingDemoTemplates")  
  
 前のセクションの例で示したように、<xref:System.Windows.Controls.ListBox> コントロールおよび <xref:System.Windows.Controls.ContentControl> の両方が、*AuctionItems* のコレクション オブジェクト全体 \(具体的には、コレクション オブジェクトのビュー\) にバインドされます。  データ コレクションの表示方法を特に指定していない場合は、基になるコレクション内の各オブジェクトの文字列表現が <xref:System.Windows.Controls.ListBox> に表示され、バインド先のオブジェクトの文字列形式が <xref:System.Windows.Controls.ContentControl> に表示されます。  
  
 この問題を解決するには、アプリケーションで <xref:System.Windows.DataTemplate> を定義します。  前のセクションの例で示したように、<xref:System.Windows.Controls.ContentControl> は *detailsProductListingTemplate* <xref:System.Windows.DataTemplate> を明示的に使用します。  <xref:System.Windows.Controls.ListBox> コントロールは、コレクション内の *AuctionItem* オブジェクトを表示する際に、次の <xref:System.Windows.DataTemplate> を暗黙的に使用します。  
  
 [!code-xml[DataBindingLab#AuctionItemDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#auctionitemdatatemplate)]  
  
 これら 2 つの <xref:System.Windows.DataTemplate> を使用すると、「[データ バインディングとは](#what_is_data_binding)」セクションで示した UI が表示されます。  この UI のスクリーンショットからわかるように、<xref:System.Windows.DataTemplate> を使用すると、コントロール内にデータを配置できるだけでなく、優れた視覚効果をデータに対して定義することができます。  たとえば、上の <xref:System.Windows.DataTemplate> では、<xref:System.Windows.DataTrigger> を使用しています。これにより、*HighLight* の値が *SpecialFeatures* に設定されている *AuctionItem* が、星の付いたオレンジ色の境界線で表示されます。  
  
 データ テンプレートの詳細については、「[データ テンプレートの概要](../../../../docs/framework/wpf/data/data-templating-overview.md)」を参照してください。  
  
<a name="data_validation"></a>   
## データの検証  
   
  
 ユーザー入力を受け取るほとんどのアプリケーションでは、ユーザーが必要な情報を入力したことを確認するための検証ロジックが必要になります。  型、範囲、形式、またはその他のアプリケーション固有の要件に基づいて、検証チェックを実行することができます。  ここでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] におけるデータ検証のしくみについて説明します。  
  
<a name="validation_rules"></a>   
### 検証規則とバインディングの関連付け  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] データ バインディング モデルでは、<xref:System.Windows.Data.Binding.ValidationRules%2A> を <xref:System.Windows.Data.Binding> オブジェクトに関連付けることができます。  たとえば、次の例では <xref:System.Windows.Controls.TextBox> を `StartPrice` という名前のプロパティにバインドし、<xref:System.Windows.Controls.ExceptionValidationRule> オブジェクトを <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=fullName> プロパティにバインドします。  
  
 [!code-xml[DataBindingLab#DefaultValidation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#defaultvalidation)]  
  
 <xref:System.Windows.Controls.ValidationRule> オブジェクトは、プロパティ値が有効であるかどうかを確認します。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、次の 2 種類の組み込み <xref:System.Windows.Controls.ValidationRule> オブジェクトがあります。  
  
-   <xref:System.Windows.Controls.ExceptionValidationRule> では、バインディング ソース プロパティの更新中にスローされる例外をチェックします。  前の例では、`StartPrice` の型は整数です。  ユーザーが整数に変換できない値を入力すると、例外がスローされ、バインディングが無効としてマークされます。  また、<xref:System.Windows.Controls.ExceptionValidationRule> を明示的に設定するには、<xref:System.Windows.Data.Binding> オブジェクトまたは <xref:System.Windows.Data.MultiBinding> オブジェクトで、<xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> プロパティを `true` に設定する構文も使用できます。  
  
-   <xref:System.Windows.Controls.DataErrorValidationRule> オブジェクトは、<xref:System.ComponentModel.IDataErrorInfo> インターフェイスを実装するオブジェクトで発生するエラーをチェックします。  この検証規則の使用例については、「<xref:System.Windows.Controls.DataErrorValidationRule>」を参照してください。  また、<xref:System.Windows.Controls.DataErrorValidationRule> を明示的に設定するには、<xref:System.Windows.Data.Binding> オブジェクトまたは <xref:System.Windows.Data.MultiBinding> オブジェクトで、<xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> プロパティを `true` に設定する構文も使用できます。  
  
 <xref:System.Windows.Controls.ValidationRule> クラスを継承し、<xref:System.Windows.Controls.ValidationRule.Validate%2A> メソッドを実装することにより、独自の検証規則を作成することもできます。  次の例は、「[データ バインディングとは](#what_is_data_binding)」セクションで示した \[Add Product Listing\] の \[Start Date\] <xref:System.Windows.Controls.TextBox> で使用される規則を示しています。  
  
 [!code-csharp[DataBindingLab#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/FutureDateRule.cs#2)]
 [!code-vb[DataBindingLab#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/FutureDateRule.vb#2)]  
  
 次の例に示すように、*StartDateEntryForm* <xref:System.Windows.Controls.TextBox> では、この *FutureDateRule* が使用されます。  
  
 [!code-xml[DataBindingLab#CustomValidation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#customvalidation)]  
  
 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> の値が <xref:System.Windows.Data.UpdateSourceTrigger> であるため、バインディング エンジンは、キーストロークが発生するたびにソース値を更新します。つまり、<xref:System.Windows.Data.Binding.ValidationRules%2A> コレクション内のすべての規則もまた、キーストロークが発生するたびにバインディング エンジンによってチェックされることになります。  詳細については、「検証プロセス」セクションで説明します。  
  
<a name="invalidation_feedback"></a>   
### 視覚的フィードバックの提供  
 ユーザーが無効な値を入力した場合には、アプリケーションの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 上でエラーに関するフィードバックを提供する必要があります。  このようなフィードバックを提供する方法として、<xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=fullName> 添付プロパティをカスタム <xref:System.Windows.Controls.ControlTemplate> に設定する方法があります。  前のサブセクションで示したように、*StartDateEntryForm* <xref:System.Windows.Controls.TextBox> では、*validationTemplate* という名前の <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> が使用されます。  *validationTemplate* の定義を次の例に示します。  
  
 [!code-xml[DataBindingLab#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/AddProductWindow.xaml#1)]  
  
 <xref:System.Windows.Controls.AdornedElementPlaceholder> 要素は、装飾されているコントロールの位置を指定します。  
  
 また、<xref:System.Windows.Controls.ToolTip> を使用してエラー メッセージを表示することもできます。  *StartDateEntryForm* および *StartPriceEntryForm* の両 <xref:System.Windows.Controls.TextBox> では、*textStyleTextBox* スタイルが使用されています。これにより、エラー メッセージを表示する <xref:System.Windows.Controls.ToolTip> が作成されます。  *textStyleTextBox* の定義を次の例に示します。  バインドされている要素のプロパティで 1 つ以上のバインディングにエラーが発生すると、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> [添付プロパティ](GTMT)が `true` になります。  
  
 [!code-xml[DataBindingLab#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#14)]  
  
 カスタム <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> と <xref:System.Windows.Controls.ToolTip> を使用している場合、検証エラーが発生すると、*StartDateEntryForm* <xref:System.Windows.Controls.TextBox> は次のようになります。  
  
 ![データ バインディング検証エラー](../../../../docs/framework/wpf/data/media/databindingdemo-validation.png "DataBindingDemo\_Validation")  
  
 <xref:System.Windows.Data.Binding> に検証規則が関連付けられていても、バインドされているコントロールに対して <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> を指定していない場合は、検証エラーが発生したときのユーザーへの通知に既定の <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> が使用されます。  既定の <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> は、装飾層に赤い境界線を定義するコントロール テンプレートです。  既定の <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> と <xref:System.Windows.Controls.ToolTip> を使用している場合、検証エラーが発生すると、*StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> の [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] は次のようになります。  
  
 ![データ バインディング検証エラー](../../../../docs/framework/wpf/data/media/databindingdemo-validationdefault.png "DataBindingDemo\_ValidationDefault")  
  
 ダイアログ ボックス内のすべてのコントロールを検証するロジックを提供する方法の例については、「[ダイアログ ボックスの概要](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)」の「カスタム ダイアログ ボックス」セクションを参照してください。  
  
<a name="validation_process"></a>   
### 検証プロセス  
 検証は、通常、ターゲットの値がバインディング ソース プロパティに転送されると発生します。  検証は、<xref:System.Windows.Data.BindingMode> バインディングと <xref:System.Windows.Data.BindingMode> バインディングで行われます。  「[ソースの更新の要因](#what_triggers_source_updates)」セクションで説明したように、ソースの更新の要因は、<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> プロパティの値によって異なります。  
  
 ここでは、*検証*プロセスについて説明します。  このプロセスの最中に検証エラーなどのエラーが発生すると、プロセスが中止されることに注意してください。  
  
1.  バインディング エンジンは、該当する <xref:System.Windows.Data.Binding> について <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> が <xref:System.Windows.Controls.ValidationStep> に設定されているカスタム <xref:System.Windows.Controls.ValidationRule> オブジェクトが定義されているかどうかをチェックします。このとき、どれかでエラーが発生するか、すべてが合格するまで、各 <xref:System.Windows.Controls.ValidationRule> の <xref:System.Windows.Controls.ValidationRule.Validate%2A> メソッドを呼び出します。  
  
2.  次に、バインディング エンジンはコンバーターを呼び出します \(存在する場合\)。  
  
3.  コンバーターが正常終了した場合、バインディング エンジンは、該当する <xref:System.Windows.Data.Binding> について <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> が <xref:System.Windows.Controls.ValidationStep> に設定されているカスタム <xref:System.Windows.Controls.ValidationRule> オブジェクトが定義されているかどうかをチェックします。このとき、いずれかでエラーが発生するか、すべてが合格するまで、<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> が <xref:System.Windows.Controls.ValidationStep> に設定されている各 <xref:System.Windows.Controls.ValidationRule> の <xref:System.Windows.Controls.ValidationRule.Validate%2A> メソッドを呼び出します。  
  
4.  バインディング エンジンがソース プロパティを設定します。  
  
5.  バインディング エンジンは、該当する <xref:System.Windows.Data.Binding> について <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> が <xref:System.Windows.Controls.ValidationStep> に設定されているカスタム <xref:System.Windows.Controls.ValidationRule> オブジェクトが定義されているかどうかをチェックします。このとき、いずれかでエラーが発生するか、すべてが合格するまで、<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> が <xref:System.Windows.Controls.ValidationStep> に設定されている各 <xref:System.Windows.Controls.ValidationRule> の <xref:System.Windows.Controls.ValidationRule.Validate%2A> メソッドを呼び出します。  <xref:System.Windows.Controls.DataErrorValidationRule> がバインディングに関連付けられており、その <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> が既定の <xref:System.Windows.Controls.ValidationStep> に設定されている場合、この時点で <xref:System.Windows.Controls.DataErrorValidationRule> がチェックされます。  また、この時点で、<xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> が `true` に設定されているバインディングもチェックされます。  
  
6.  バインディング エンジンは、該当する <xref:System.Windows.Data.Binding> について <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> が <xref:System.Windows.Controls.ValidationStep> に設定されているカスタム <xref:System.Windows.Controls.ValidationRule> オブジェクトが定義されているかどうかをチェックします。このとき、いずれかでエラーが発生するか、すべてが合格するまで、<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> が <xref:System.Windows.Controls.ValidationStep> に設定されている各 <xref:System.Windows.Controls.ValidationRule> の <xref:System.Windows.Controls.ValidationRule.Validate%2A> メソッドを呼び出します。  
  
 このプロセスの最中に <xref:System.Windows.Controls.ValidationRule> が合格しなかった場合、バインディング エンジンは <xref:System.Windows.Controls.ValidationError> オブジェクトを作成し、それをバインドされている要素の <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=fullName> コレクションに追加します。  バインディング エンジンは、各手順で <xref:System.Windows.Controls.ValidationRule> オブジェクトを実行する前に、バインドされた要素の <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=fullName> [添付プロパティ](GTMT)にその手順で以前追加されたすべての <xref:System.Windows.Controls.ValidationError> を削除します。  たとえば、<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> が <xref:System.Windows.Controls.ValidationStep> に設定された <xref:System.Windows.Controls.ValidationRule> が不合格になった場合、次回このプロセスが発生したとき、バインディング エンジンはそのような <xref:System.Windows.Controls.ValidationError> を、<xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> が <xref:System.Windows.Controls.ValidationStep> に設定されている <xref:System.Windows.Controls.ValidationRule> を呼び出す直前に削除します。  
  
 <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=fullName> が空でない場合、その要素の <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> [添付プロパティ](GTMT)は `true` に設定されます。  また、<xref:System.Windows.Data.Binding> の <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> プロパティが `true` に設定されている場合、バインディング エンジンはその要素の <xref:System.Windows.Controls.Validation.Error?displayProperty=fullName> [添付イベント](GTMT)を発生させます。  
  
 また、どちらの方向 \(ターゲットからソース、またはソースからターゲット\) でも、有効な値を転送すると <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=fullName> [添付プロパティ](GTMT)が消去されることに注意してください。  
  
 バインディングに <xref:System.Windows.Controls.ExceptionValidationRule> が関連付けられているか、<xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> プロパティが `true` に設定されており、バインディング エンジンがソースを設定したときに例外がスローされた場合、バインディング エンジンは <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> が存在するかどうかをチェックします。  <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> コールバックを使用して、例外を処理するためのカスタム ハンドラーを提供することもできます。  <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> が <xref:System.Windows.Data.Binding> で指定されていない場合、バインディング エンジンは例外を使用して <xref:System.Windows.Controls.ValidationError> を作成し、それをバインドされている要素の <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=fullName> コレクションに追加します。  
  
<a name="debugging_mechanism"></a>   
## デバッグ機構  
 バインディング関連のオブジェクトに対して <xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=fullName> 添付プロパティを設定すると、特定のバインディングのステータス情報を取得できます。  
  
## 参照  
 <xref:System.Windows.Controls.DataErrorValidationRule>   
 [WPF Version 4.5 の新機能](../../../../docs/framework/wpf/getting-started/whats-new.md)   
 [LINQ クエリの結果にバインドする](../../../../docs/framework/wpf/data/how-to-bind-to-the-results-of-a-linq-query.md)   
 [データ バインド](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [データ バインディングのデモ](http://go.microsoft.com/fwlink/?LinkID=163703)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)   
 [ADO.NET データ ソースにバインドする](../../../../docs/framework/wpf/data/how-to-bind-to-an-ado-net-data-source.md)