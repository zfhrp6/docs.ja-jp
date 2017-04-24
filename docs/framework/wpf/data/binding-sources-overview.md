---
title: "バインディング ソースの概要 | Microsoft Docs"
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
  - "バインド (データを), バインディング ソース"
  - "バインディング ソース"
  - "データ バインディング, バインディング ソース"
ms.assetid: 2df2cd11-6aac-4bdf-ab7b-ea5f464cd5ca
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# バインディング ソースの概要
データ バインディングでは、データの取得元のオブジェクトを[バインディング ソース](GTMT) オブジェクトと呼びます。  ここでは、バインディング ソースとして使用できるオブジェクトの種類について説明します。  
  
   
  
<a name="binding_sources"></a>   
## バインディング ソースの種類  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] データ バインディングでは、次の種類の[バインディング ソース](GTMT)がサポートされます。  
  
|バインディング ソース|Description|  
|-----------------|-----------------|  
|[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] オブジェクト|任意の[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] オブジェクトのパブリック プロパティ、サブプロパティ、およびインデクサーにバインドできます。  バインディング エンジンは、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] リフレクションを使用してプロパティの値を取得します。  また、<xref:System.ComponentModel.ICustomTypeDescriptor> を実装しているオブジェクトや、登録された <xref:System.ComponentModel.TypeDescriptionProvider> を持つオブジェクトも、バインディング エンジンと連携できます。<br /><br /> バインディング ソースとして使用できるクラスの実装方法の詳細については、このトピックで後述する「[バインディング ソースとしてクラスを実装する](#classes)」を参照してください。|  
|動的オブジェクト|<xref:System.Dynamic.IDynamicMetaObjectProvider> インターフェイスを実装するオブジェクトの使用可能なプロパティおよびインデクサーにバインドできます。  コードのメンバーにアクセスできる場合は、そのメンバーにバインドできます。  たとえば、動的オブジェクトを使用して `someObjet.AProperty` によってコードのメンバーにアクセスできる場合は、バインド パスを `AProperty` に設定することでそのメンバーにバインドできます。|  
|[!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] オブジェクト|<xref:System.Data.DataTable> などの [!INCLUDE[TLA2#tla_adonet](../../../../includes/tla2sharptla-adonet-md.md)] オブジェクトにバインドできます。[!INCLUDE[TLA2#tla_adonet](../../../../includes/tla2sharptla-adonet-md.md)] <xref:System.Data.DataView> は <xref:System.ComponentModel.IBindingList> インターフェイスを実装し、バインド エンジンがリッスンする変更通知を提供します。|  
|[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] オブジェクト|<xref:System.Xml.XmlNode>、<xref:System.Xml.XmlDocument>、または <xref:System.Xml.XmlElement> にバインドして、`XPath` クエリを実行できます。  マークアップ内の[バインディング ソース](GTMT)である [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データに簡単にアクセスするには、<xref:System.Windows.Data.XmlDataProvider> オブジェクトを使用します。  詳細については、「[XMLDataProvider と XPath クエリを使用して XML データにバインドする](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)」を参照してください。<br /><br /> <xref:System.Xml.Linq.XElement> または <xref:System.Xml.Linq.XDocument> にバインドしたり、LINQ to XML を使用してこれらの型のオブジェクトに対して実行したクエリの結果にバインドしたりすることもできます。  LINQ to XML を使用してマークアップ内のバインディング ソースである XML データに簡単にアクセスするには、<xref:System.Windows.Data.ObjectDataProvider> オブジェクトを使用します。  詳細については、「[XDocument、XElement、または LINQ for XML クエリの結果にバインドする](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)」を参照してください。|  
|<xref:System.Windows.DependencyObject> オブジェクト|任意の <xref:System.Windows.DependencyObject> の[依存関係プロパティ](GTMT)にバインドできます。  例については、「[2 つのコントロールのプロパティをバインドする](../../../../docs/framework/wpf/data/how-to-bind-the-properties-of-two-controls.md)」を参照してください。|  
  
<a name="classes"></a>   
## バインディング ソースとしてクラスを実装する  
 バインディング ソースは独自に作成できます。  ここでは、 クラスをバインディング ソースとして使用する目的で実装する場合に認識しておく必要のある事項について説明します。  
  
### 変更通知を提供する  
 <xref:System.Windows.Data.BindingMode> または <xref:System.Windows.Data.BindingMode> バインディング \(バインディング ソース プロパティが動的に変更される場合は [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を更新する必要があるため\) を使用している場合は、適切なプロパティ変更通知機構を実装する必要があります。  推奨される機構としては、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] クラスまたは動的クラスによる <xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスの実装があります。  詳細については、「[プロパティの変更通知を実装する](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md)」を参照してください。  
  
 <xref:System.ComponentModel.INotifyPropertyChanged> を実装しない [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] オブジェクトを作成する場合は、バインディングで使用されるデータが常に最新の状態を保つように、独自の通知システムを用意する必要があります。  変更通知を提供するには、変更を通知する必要のある各プロパティの `PropertyChanged` パターンをサポートします。  このパターンをサポートするには、各プロパティに対して *PropertyName*Changed イベントを定義します。ここで、*PropertyName* はそのプロパティの名前です。  プロパティが変更されるたびに、このイベントが発生するようにします。  
  
 バインディング ソースがこれらのいずれかの通知機構を実装している場合、ターゲットは自動的に更新されます。  なんらかの理由でバインディング ソースが適切なプロパティ変更通知を提供しない場合は、<xref:System.Windows.Data.BindingExpression.UpdateTarget%2A> メソッドを使用してターゲット プロパティを明示的に更新できます。  
  
### その他の特性  
 注意する必要のあるその他の重要な点を、次の一覧に示します。  
  
-   オブジェクトを [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で作成する場合、クラスには既定のコンストラクターが必要です。  [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] などの一部の [!INCLUDE[TLA2#tla_net](../../../../includes/tla2sharptla-net-md.md)] 言語では、既定のコンストラクターがあらかじめ作成されている場合があります。  
  
-   バインディングのバインディング ソース プロパティとして使用するプロパティは、クラスのパブリック プロパティである必要があります。  明示的に定義されたインターフェイス プロパティには、基本実装を持たない保護プロパティ、プライベート プロパティ、内部プロパティ、および仮想プロパティの場合と同様に、バインディングのためにアクセスすることはできません。  
  
-   パブリック フィールドにバインドすることはできません。  
  
-   クラスで宣言したプロパティの型は、バインディングに渡される型です。  ただし、バインディングで最終的に使用される型は、バインディング ソース プロパティの型ではなく、[バインディング ターゲット](GTMT) プロパティの型に依存します。  型が異なっている場合は、カスタム プロパティがバインディングに最初に渡される方法を処理するためのコンバーターを作成することが考えられます。  詳細については、「<xref:System.Windows.Data.IValueConverter>」を参照してください。  
  
<a name="objects"></a>   
## オブジェクト全体をバインディング ソースとして使用する  
 オブジェクト全体をバインディング ソースとして使用できます。  <xref:System.Windows.Data.Binding.Source%2A> プロパティまたは <xref:System.Windows.FrameworkElement.DataContext%2A> プロパティを使用してバインディング ソースを指定し、次に、`{Binding}` のように、空白のバインディング宣言を指定できます。  この方法が役立つシナリオとしては、型文字列のオブジェクトへのバインディング、必要な複数のプロパティを持つオブジェクトへのバインディング、またはコレクション オブジェクトへのバインディングなどがあります。  コレクション オブジェクト全体へのバインディングの例については、「[階層データでマスター詳細パターンを使用する](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)」を参照してください。  
  
 カスタム ロジックを適用して、バインドしたターゲット プロパティでデータが有効になるようにしなければならない場合があることに注意してください。  カスタム ロジックは、カスタム コンバーター \(既定の型変換が存在しない場合\) のフォーム、または <xref:System.Windows.DataTemplate> に含まれていなければなりません。  コンバーターの詳細については、「[データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」の「データ変換」セクションを参照してください。  データ テンプレートの詳細については、「[データ テンプレートの概要](../../../../docs/framework/wpf/data/data-templating-overview.md)」を参照してください。  
  
<a name="collections"></a>   
## コレクション オブジェクトをバインディング ソースとして使用する  
 多くの場合、バインディング ソースとして使用する必要のあるオブジェクトは、複数のカスタム オブジェクトのコレクションです。  各オブジェクトは、反復されるバインディングの 1 つのインスタンスのソースとして使用されます。  たとえば、複数の `CustomerOrder` オブジェクトで構成される `CustomerOrders` コレクションがあり、アプリケーションはそのコレクションを反復処理して、存在する注文の数と、各注文に含まれるデータを判別する場合があります。  
  
 <xref:System.Collections.IEnumerable> インターフェイスを実装するすべてのコレクションを列挙できます。  ただし、コレクションへの挿入や削除によって [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] が自動的に更新されるように動的バインディングを設定するには、コレクションで <xref:System.Collections.Specialized.INotifyCollectionChanged> インターフェイスを実装する必要があります。  このインターフェイスは、基になるコレクションが変更されるたびに発生する必要があるイベントを公開します。  
  
 <xref:System.Collections.ObjectModel.ObservableCollection%601> クラスは、<xref:System.Collections.Specialized.INotifyCollectionChanged> インターフェイスを公開するデータ コレクションの組み込み実装です。  コレクション内の個々のデータ オブジェクトは、前のセクションで説明されている要件を満たす必要があります。  例については、「[ObservableCollection を作成およびバインドする](../../../../docs/framework/wpf/data/how-to-create-and-bind-to-an-observablecollection.md)」を参照してください。  独自のコレクションを実装する前に、<xref:System.Collections.ObjectModel.ObservableCollection%601> または既存のコレクション クラスのいずれか \(特に <xref:System.Collections.Generic.List%601>、<xref:System.Collections.ObjectModel.Collection%601>、<xref:System.ComponentModel.BindingList%601> など\) の使用を検討します。  
  
 WPF がコレクションに直接バインドされることはありません。  コレクションをバインディング ソースとして指定した場合、WPF は実際にはそのコレクションの既定のビューにバインドされます。  既定のビューの詳細については、「[データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」を参照してください。  
  
 高度なシナリオがあり、独自のコレクションを実装する場合は、<xref:System.Collections.IList> インターフェイスの使用を検討してください。  <xref:System.Collections.IList> により、インデックスによって個別にアクセスできるオブジェクトの非ジェネリック コレクションが利用可能になり、パフォーマンスが向上します。  
  
<a name="permissions"></a>   
## データ バインディングに必要なアクセス許可  
 データ バインディングを使用する場合、アプリケーションの信頼レベルを考慮する必要があります。  完全な信頼または部分信頼で実行されているアプリケーションにバインドできるプロパティの種類を次の表に要約します。  
  
|プロパティの型<br /><br /> \(すべてのアクセス修飾子\)|動的オブジェクト プロパティ|動的オブジェクト プロパティ|CLR プロパティ|CLR プロパティ|依存関係プロパティ|依存関係プロパティ|  
|---------------------------------|--------------------|--------------------|---------------|---------------|---------------|---------------|  
|**信頼レベル**|**完全信頼**|**部分信頼**|**完全信頼**|**部分信頼**|**完全信頼**|**部分信頼**|  
|パブリック クラス|○|○|○|○|○|○|  
|パブリック クラス以外|○|Ｘ|○|Ｘ|○|○|  
  
 次の表は、データ バインディングで必要とされるアクセス許可についての重要事項の説明です。  
  
-   [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] プロパティの場合、データ バインディングは、バインディング エンジンがリフレクションを使用してバインディング ソース プロパティにアクセスできる限り、機能します。  それ以外の場合、バインディング エンジンは、プロパティを見つけることができないと警告を発し、可能であればフォールバック値または既定値を使用します。  
  
-   コンパイル時または実行時に定義される動的オブジェクトのプロパティにバインドできます。  
  
-   いつでも[依存関係プロパティ](GTMT)にバインドできます。  
  
 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] バインディングで必要とされるアクセス許可も同様です。部分信頼サンドボックスでは、指定されたデータへのアクセス許可がない場合、<xref:System.Windows.Data.XmlDataProvider> は失敗します。  
  
 匿名型のオブジェクトは内部オブジェクトです。  完全信頼で実行する場合のみ、匿名型のプロパティにバインドできます。  匿名型の詳細については、「[匿名型 \(C\# プログラミング ガイド\)](../Topic/Anonymous%20Types%20\(C%23%20Programming%20Guide\).md)」または「[匿名型 \(Visual Basic\)](../Topic/Anonymous%20Types%20\(Visual%20Basic\).md)」\(Visual Basic\) を参照してください。  
  
 部分信頼セキュリティの詳細については、「[WPF 部分信頼セキュリティ](../../../../docs/framework/wpf/wpf-partial-trust-security.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Data.ObjectDataProvider>   
 <xref:System.Windows.Data.XmlDataProvider>   
 [バインディング ソースを指定する](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)   
 [LINQ to XML による WPF のデータ バインドの概要](../Topic/WPF%20Data%20Binding%20with%20LINQ%20to%20XML%20Overview.md)   
 [データ バインド](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)