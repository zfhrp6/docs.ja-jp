---
title: "添付プロパティの概要 | Microsoft Docs"
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
  - "添付プロパティ [WPF デザイナー]"
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
caps.latest.revision: 28
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 27
---
# 添付プロパティの概要
添付プロパティはXAML で定義されている概念です。  添付プロパティの目的は、任意のオブジェクトに対して設定可能な一種のグローバル プロパティとして使用することです。  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] では添付プロパティは従来のプロパティ 「ラッパー」を持たない依存関係プロパティの特殊な形式で一般に定義されます。  
  
   
  
<a name="prerequisites"></a>   
## 必要条件  
 このトピックでは、ユーザーが [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] クラスの既存の依存関係プロパティの使用という観点から依存関係プロパティを理解し、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」トピックを通読していることを前提としています。  このトピックの例に従うには[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] するアプリケーションの作成方法を XAML を理解していることも必要です。  
  
<a name="attached_properties_usage"></a>   
## 添付プロパティを使用する理由  
 添付プロパティの目的の 1 つは、実際には親要素で定義されるプロパティについて、子要素がそれぞれ別の値を指定できるようにすることです。  このシナリオは、たとえば、子要素を[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] にどのように表示するかを子要素から親要素に通知させるという状況に応用されます。  <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> プロパティがその一例です。  <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> プロパティが添付プロパティとして作成されるのは、このプロパティが <xref:System.Windows.Controls.DockPanel> 自体ではなく <xref:System.Windows.Controls.DockPanel> に含まれる要素に対して設定するように設計されているためです。  <xref:System.Windows.Controls.DockPanel> クラスでは、<xref:System.Windows.Controls.DockPanel.DockProperty> という名前の静的 <xref:System.Windows.DependencyProperty> フィールドが定義されており、[添付プロパティ](GTMT)のパブリック アクセサーとして <xref:System.Windows.Controls.DockPanel.GetDock%2A> メソッドと <xref:System.Windows.Controls.DockPanel.SetDock%2A> メソッドが定義されています。  
  
<a name="attached_properties_xaml"></a>   
## XAML での添付プロパティ  
 XAML では、*AttachedPropertyProvider*.*PropertyName* という構文を使用して添付プロパティを設定します。  
  
 次の XAML <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> を設定する例を示しています :  
  
 [!code-xml[PropertiesOvwSupport#APBasicUsage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]  
  
 使用方法が静的プロパティに少し似ていることに注意してください。名前で指定されたインスタンスを参照するのではなく、[添付プロパティ](GTMT)を所有および登録する <xref:System.Windows.Controls.DockPanel> 型を常に参照します。  
  
 また構成操作のみですXAML の添付プロパティがマークアップに設定した属性であるためです。  スタイル トリガーなどの値を比較する間接的機能があります \(詳細については" " [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md) を直接 XAML のプロパティを取得できません。  
  
### WPF での添付プロパティの実装  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ではUI 表示に関連する [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の型になる添付プロパティのほとんどは依存関係プロパティとして実装されます。  添付プロパティは依存関係プロパティが [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の概念でありXAML の概念です。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の添付プロパティが依存関係プロパティであるためプロパティ メタデータなどの依存関係プロパティの概念やの既定値をプロパティ メタデータ サポートします。  
  
<a name="howused"></a>   
## 所有する型が添付プロパティを使用する方法  
 添付プロパティはどのオブジェクトに対しても設定可能ですが、プロパティを設定することで具体的な結果が得られたり、その値が他のオブジェクトから使用されたりするわけではありません。  大まかにいって、添付プロパティの目的は、さまざまなクラス階層または論理上のリレーションシップから発生するオブジェクトのそれぞれが、添付プロパティを定義する型に対して共通の情報を報告できるようにすることです。  添付プロパティを定義する型は一般に、次のいずれかのモデルに従います。  
  
-   添付プロパティを定義する型は、添付プロパティの値を設定する要素の親要素になることができるように設計されています。  この型は、なんらかのオブジェクト ツリー構造に対して内部ロジックを通じて自身の子オブジェクトを反復処理し、値を取得し、その値に対するなんらかの処理を行います。  
  
-   添付プロパティを定義する型は、さまざまな親要素およびコンテンツ モデルの子要素として使用されます。  
  
-   添付プロパティを定義する型は、サービスを表します。  その他の型は、添付プロパティの値を設定します。  プロパティを設定する要素がサービスのコンテキスト内で評価されるときに、サービス クラスの内部ロジックを通じて添付プロパティの値が取得されます。  
  
### 親要素で定義された添付プロパティの例  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] が添付プロパティを定義する最も一般的なシナリオは、親要素が子要素のコレクションをサポートすると同時に、親要素が実装した動作の詳細を子要素ごとに別個に報告させるというものです。  
  
 <xref:System.Windows.Controls.DockPanel> では <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> 添付プロパティが定義され、<xref:System.Windows.Controls.DockPanel> のレンダリング ロジックの一部としてクラス レベルのコードが設定されています \(具体的には <xref:System.Windows.Controls.DockPanel.MeasureOverride%2A> と <xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A>\)。  <xref:System.Windows.Controls.DockPanel> のインスタンスは、直接の子要素が <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> の値を設定しているかどうかを常に確認します。  設定されている場合は、その値を入力とするレンダリング ロジックを、その子要素に適用します。  入れ子になった <xref:System.Windows.Controls.DockPanel> インスタンスは、それぞれ自身の直接の子要素のコレクションを扱いますが、その動作は実装で <xref:System.Windows.Controls.DockPanel> が <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> 値を処理する方法によって異なります。  直接の親以外の要素に作用する添付プロパティも、理論的には可能です。  <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> 添付プロパティが設定されている要素が、作用対象の <xref:System.Windows.Controls.DockPanel> 親要素を持たない場合も、エラーや例外は発生しません。  これは、グローバル プロパティ値が設定されたけれども、その情報を利用できる親 <xref:System.Windows.Controls.DockPanel> が現在存在しないことを意味します。  
  
<a name="attached_properties_code"></a>   
## コードでの添付プロパティ  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の添付プロパティには、get および set のアクセスを容易にするための標準的な [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] "ラッパー" メソッドはありません。  これは、添付プロパティが設定されたインスタンスの [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 名前空間に、その添付プロパティが属しているとは限らないからです。  ただしXAML プロセッサが XAML の解析時にこれらの値を設定する必要があります。  有効な添付プロパティの使用方法をサポートするには添付プロパティの所有者型がフォーム `Get`*PropertyName* と `Set`*PropertyName* の専用アクセサー メソッドを実装する必要があります。  この専用アクセサー メソッドは、コードで添付プロパティを取得または設定するときにも役立ちます。  コードの観点から言うと、添付プロパティは、プロパティ アクセサーではなくメソッド アクセサーを持つバッキング フィールドに似ています。そしてそのバッキング フィールドは、任意のオブジェクトに存在し得るもので、具体的な定義を必要とするものではありません。  
  
 コードで添付プロパティを設定する方法を次の例に示します。  この例では、`myCheckBox` は <xref:System.Windows.Controls.CheckBox> クラスのインスタンスです。  
  
 [!code-csharp[PropertiesOvwSupport#APCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
 [!code-vb[PropertiesOvwSupport#APCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]  
  
 `myCheckBox` がコードの 3 行目で `myDockPanel` の子要素として追加されていない XAML の例と同様にコードの 4 行目も例外は発生しませんがプロパティ値は <xref:System.Windows.Controls.DockPanel> の親と対話していないため何も行われません。  子要素で <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> 値が設定されていて、親要素の <xref:System.Windows.Controls.DockPanel> が存在する場合にのみ、レンダリングされたアプリケーション内で有効な動作が実行されます。  この場合、添付プロパティを設定した後でツリーにアタッチすることも、  ツリーにアタッチした後で添付プロパティを設定することもできます。  どちらの操作順序でも結果は同じになります。  
  
<a name="attached_properties_metadata"></a>   
## 添付プロパティのメタデータ  
 プロパティを登録するときに、<xref:System.Windows.FrameworkPropertyMetadata> を設定してプロパティの特性を指定します。たとえば、プロパティがレンダリングやサイズ測定に影響を及ぼすかどうかを指定します。  通常、[添付プロパティ](GTMT)のメタデータは、[依存プロパティ](GTMT)のメタデータと違いはありません。  オーバーライドで添付プロパティ メタデータに既定値を指定した場合、その値は、オーバーライドしたクラスのインスタンスの暗黙の添付プロパティの既定値となります。  具体的には、なんらかのプロセスが、`Get` メソッド アクセサーを通じて添付プロパティの値をクエリするときに、メタデータを設定したクラスのインスタンスを指定した場合、その添付プロパティの値が他では特に設定されていないときには、既定値が通知されます。  
  
 プロパティ値の継承を有効にするときには、添付プロパティ以外の依存関係プロパティではなく、添付プロパティを使用する必要があります。  詳細については、「[プロパティ値の継承](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)」を参照してください。  
  
<a name="custom"></a>   
## カスタム添付プロパティ  
  
<a name="create_attached_properties"></a>   
### いつ添付プロパティを作成するか  
 [添付プロパティ](GTMT)を作成するのは、プロパティを定義するクラス以外のクラスでプロパティを設定するための機構が必要な場合です。  この最も一般的なシナリオはレイアウトです。  既存のレイアウト プロパティの例としては、<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName>、<xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=fullName>、<xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=fullName> などがあります。  これによって実現するシナリオは、レイアウト制御要素の子要素として存在する要素が、レイアウト親要素に対して個別にレイアウト要件を表現するというものです。親が添付プロパティとして定義したプロパティ値を、個々の子要素が設定します。  
  
 添付プロパティを使用するシナリオには、この他に、クラスによってサービスを表す場合に、クラスとサービスとをより透過的に統合できるようにするというものがあります。  
  
 さらに別のシナリオとしては、[!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] の [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]のサポート \(**\[プロパティ\]** ウィンドウでの編集など\) に対応するというものもあります。  詳細については、「[コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)」を参照してください。  
  
 既に述べたように、プロパティ値の継承を使用する場合には、添付プロパティとして登録する必要があります。  
  
<a name="how_do_i_create_attached_properties"></a>   
### 添付プロパティの作成方法  
 クラスで定義する[添付プロパティ](GTMT)が、他の型での使用のみを目的としている場合は、このクラスが <xref:System.Windows.DependencyObject> から派生していなくてもかまいません。  ただし添付プロパティの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の全体的なモデルには依存関係プロパティと <xref:System.Windows.DependencyObject> から派生している必要があります。  
  
 添付プロパティを依存関係プロパティとして定義するには、<xref:System.Windows.DependencyProperty> 型の `public` `static` `readonly` フィールドを宣言します。  このフィールドを定義するには、<xref:System.Windows.DependencyProperty.RegisterAttached%2A> メソッドの戻り値を使用します。  フィールド名は、添付プロパティと同じ名前に文字列 `Property` を付加したものである必要があります。識別するフィールドとそのフィールドが表すプロパティに関する、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で確立された命名パターンに従うためです。  添付プロパティ プロバイダーは添付プロパティのアクセサーとして *PropertyName* と `Set`*PropertyName* の静的 `Get` メソッドを提供する必要があります。; 添付プロパティを使用してプロパティ システムでこの操作を行うとが発生します。  
  
> [!NOTE]
>  添付プロパティの get アクセサーを省略すると、そのプロパティのデータ バインディングは、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] や Expression Blend などのデザイン ツールで動作しません。  
  
#### Get アクセサー  
 *PropertyName* アクセサーのシグネチャの `Get` 形式は次のとおりです。:  
  
 `public static object Get` *PropertyName* `(object`  `target` `)`  
  
-   `target` オブジェクトは、実装内で具体的な型として指定できます。  たとえば、<xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=fullName> メソッドでは、このパラメーターの型が <xref:System.Windows.UIElement> となっています。これは、添付プロパティが <xref:System.Windows.UIElement> インスタンスに対してのみ設定されることになっているからです。  
  
-   戻り値は、実装内で具体的な型として指定できます。  たとえば、<xref:System.Windows.Controls.DockPanel.GetDock%2A> メソッドの戻り値の型は <xref:System.Windows.Controls.Dock> ですが、この値はその列挙体にのみ設定可能だからです。  
  
#### Set アクセサー  
 *PropertyName* アクセサーのシグネチャの `Set` 形式は次のとおりです。:  
  
 `public static void Set` *PropertyName* `(object`  `target` `, object`  `value` `)`  
  
-   `target` オブジェクトは、実装内で具体的な型として指定できます。  たとえば、<xref:System.Windows.Controls.DockPanel.SetDock%2A> メソッドのこのオブジェクトの型は <xref:System.Windows.UIElement> となっています。これは、添付プロパティが <xref:System.Windows.UIElement> インスタンスに対してのみ設定されることになっているからです。  
  
-   `value` オブジェクトは、実装の中で具体的な型として指定できます。  たとえば、<xref:System.Windows.Controls.DockPanel.SetDock%2A> メソッドのこのパラメーターの型は <xref:System.Windows.Controls.Dock> となっています。この値は、その列挙体にのみ設定可能だからです。  マークアップの添付プロパティの添付プロパティが検出されたときにこのメソッドの値はXAML ローダーからの入力であることに注意してください。  入力はマークアップで XAML 属性値として指定される値です。  したがって、属性値 \(最終的には文字列\) から適切な型を作成するには、使用する型でサポートされる型変換、値のシリアライザー、またはマークアップ拡張機能が必要です。  
  
 次の例では依存関係プロパティの登録 \(<xref:System.Windows.DependencyProperty.RegisterAttached%2A> のメソッドを使用\) と*PropertyName* と `Get` `Set`*PropertyName* のアクセサーを示します。  この例では、添付プロパティ名は `IsBubbleSource` です。  したがって、アクセサーの名前は `GetIsBubbleSource` および `SetIsBubbleSource` となります。  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
#### 添付プロパティの属性  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、[!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] がいくつか定義されています。これらは、リフレクション プロセス、およびリフレクションとプロパティ情報の一般的なユーザー \(デザイナーなど\) に対して、添付プロパティについての情報を提供することを目的としています。  添付プロパティはスコープの型であるためを XAML を使用する特定の技術の実装で定義されているすべての添付プロパティのグローバル リストを含む圧倒的なユーザーを回避する方法が必要です。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] が添付プロパティに対して定義する [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] を使用することで、特定の添付プロパティをプロパティ ウィンドウに表示するかどうかという状況に対応できます。  これらの属性は、独自のカスタム添付プロパティに適用することもできます。  [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] の目的と構文については、以下の該当するリファレンス ページを参照してください。  
  
-   <xref:System.Windows.AttachedPropertyBrowsableAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>  
  
<a name="more"></a>   
## 添付プロパティの詳細情報  
  
-   添付プロパティの作成方法の詳細については[添付プロパティを登録する](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md) を参照してください。  
  
-   依存関係プロパティと添付プロパティの使用方法のより高度なシナリオについては、「[カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)」を参照してください。  
  
-   プロパティを添付プロパティおよび依存関係プロパティとして登録するけれども "ラッパー" 実装も公開するということも可能です。  この場合プロパティは XAML の添付プロパティの構文によって設定するとその要素または要素のです。  標準の使用法と添付での使用法の両方について適切なシナリオを持つプロパティの例が、<xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=fullName> です。  
  
## 参照  
 <xref:System.Windows.DependencyProperty>   
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [添付プロパティを登録する](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md)