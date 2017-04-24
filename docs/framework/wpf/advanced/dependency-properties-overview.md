---
title: "依存関係プロパティの概要 | Microsoft Docs"
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
  - "添付プロパティ"
  - "データ バインディング"
  - "依存関係プロパティ"
  - "プロパティ, 添付"
  - "プロパティ, 概要"
  - "リソース, 参照"
  - "スタイル"
ms.assetid: d119d00c-3afb-48d6-87a0-c4da4f83dee5
caps.latest.revision: 30
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 29
---
# 依存関係プロパティの概要
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] には、[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] プロパティの機能を拡張するために使用できる一連のサービスが用意されています。  通常、これらのサービスをまとめて [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムと呼びます。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムによってサポートされるプロパティは、[依存関係プロパティ](GTMT)と呼ばれています。ここでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムについて、および[依存関係プロパティ](GTMT)の機能について説明します。この説明では、既存の[依存関係プロパティ](GTMT)を XAML およびコードで使用する方法を示します。  また、依存関係プロパティ メタデータなどの依存関係プロパティの特殊な側面や、カスタム クラスで独自の依存関係プロパティを作成する方法についても説明します。  
  
   
  
<a name="prerequisites"></a>   
## 必要条件  
 ここでは、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] およびオブジェクト指向プログラミングに関する基礎知識があることを前提にしています。  このトピックの例に従うには、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] について理解し、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションの作成方法に精通している必要があります。  詳細については、「[チュートリアル: WPF の概要](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)」を参照してください。  
  
<a name="why_dependency_properties"></a>   
## 依存関係プロパティおよび CLR プロパティ  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では通常、プロパティは[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] プロパティとして公開されます。  基本的なレベルでは、これらのプロパティと直接対話でき、これらのプロパティが[依存関係](GTMT)として実装されることを認識することはありません。  ただし、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムの一部またはすべての機能を利用できるように、これらの機能に精通しておく必要があります。  
  
 [依存関係プロパティ](GTMT)の目的は、他の入力の値に基づいてプロパティの値を計算する方法を提供することです。  他の入力には、テーマやユーザー設定などのシステム プロパティ、データ バインディングやアニメーション\/ストーリーボードなどのジャスト イン タイム プロパティ判定機構、リソースやスタイルなどの多目的のテンプレート、要素ツリー内の他の要素との親子のリレーションシップから判断される値などがあります。  また、[依存関係プロパティ](GTMT)を実装して、自己完結型の検証、既定値、他のプロパティに対する変更を監視するコールバック、およびランタイム情報の可能性がある情報に基づいてプロパティ値を強制するシステムを提供できます。  既存のプロパティの実際の実装をオーバーライドしたり新しいプロパティを作成したりするのではなく、依存関係プロパティ メタデータをオーバーライドすることによって、派生クラスで既存のプロパティの特定の特性を変更することもできます。  
  
 SDK リファレンスで、プロパティのマネージ リファレンス ページの「依存関係プロパティの情報」セクションの有無によって、どのプロパティが依存関係プロパティかを特定できます。  「依存関係プロパティの情報」セクションにはその依存関係プロパティの <xref:System.Windows.DependencyProperty> 識別子フィールドへのリンクがあり、そのプロパティに設定されるメタデータ オプションのリスト、クラスごとのオーバーライド情報、およびその他の詳細も示されています。  
  
<a name="back_dependency_properties"></a>   
## 依存関係プロパティによる CLR プロパティの補足  
 [依存関係プロパティ](GTMT)および [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムは、プライベート フィールドでプロパティをサポートする標準パターンの代替実装として、プロパティをサポートする型を提供することによって、プロパティ機能を拡張します。  この型の名前は <xref:System.Windows.DependencyProperty> です。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムを定義するもう 1 つの重要な型は <xref:System.Windows.DependencyObject> です。<xref:System.Windows.DependencyObject> は、[依存関係プロパティ](GTMT)を登録および所有できる基本クラスを定義します。  
  
 [依存関係プロパティ](GTMT)について説明するときにこの[!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] ドキュメントで使用する用語の概要を次に示します。  
  
-   **依存関係プロパティ** : <xref:System.Windows.DependencyProperty> によってサポートされるプロパティ。  
  
-   **依存関係プロパティの識別子**: [依存関係プロパティ](GTMT)の登録時に戻り値として取得され、クラスの静的メンバーとして格納される <xref:System.Windows.DependencyProperty> インスタンス。  この識別子は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムと対話する多くの [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] でパラメーターとして使用されます。  
  
-   **CLR "ラッパー"** : プロパティの実際の get および set 実装。  これらの実装は、依存関係プロパティの識別子を <xref:System.Windows.DependencyObject.GetValue%2A> および <xref:System.Windows.DependencyObject.SetValue%2A> の呼び出しで使用し、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムを使用してプロパティの補足を提供することによって、その識別子を組み込みます。  
  
 次の例では、`IsSpinning` [依存関係プロパティ](GTMT)を定義し、<xref:System.Windows.DependencyProperty> 識別子とサポートされるプロパティの関係を示します。  
  
 [!code-csharp[PropertiesOvwSupport#DPFormBasic](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#dpformbasic)]
 [!code-vb[PropertiesOvwSupport#DPFormBasic](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#dpformbasic)]  
[!code-csharp[PropertiesOvwSupport#DPFormBasic2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#dpformbasic2)]  
  
 プロパティとそれを補足する <xref:System.Windows.DependencyProperty> フィールドの名前付け規則は重要です。  フィールドの名前は常にプロパティの名前であり、サフィックス `Property` が追加されます。  この規則とその理由の詳細については、「[カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)」を参照してください。  
  
<a name="setting_property_values"></a>   
## プロパティ値の設定  
 コードまたは XAML でプロパティを設定できます。  
  
<a name="local_property_values"></a>   
### XAML でのプロパティ値の設定  
 ボタンの背景色を赤に指定する方法を次の XAML の例に示します。  この例では、生成されたコードで XAML 属性の単純な文字列値が WPF XAML パーサーによって [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 型 \(<xref:System.Windows.Media.SolidColorBrush> を使用した <xref:System.Windows.Media.Color>\) に型変換される場合を示します。  
  
 [!code-xml[PropertiesOvwSupport#MostBasicProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#mostbasicproperty)]  
  
 XAML は、プロパティを設定するためのさまざまな構文形式をサポートします。  特定のプロパティに対してどの構文を使用するかは、プロパティで使用される値型、および型コンバーターの有無などのその他の要素によって決定されます。  プロパティ設定の XAML 構文の詳細については、「[XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)」および「[XAML 構文の詳細](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)」を参照してください。  
  
 属性以外の構文の例として、別のボタンの背景を次の XAML の例に示します。  今回は単純な純色を設定するのではなく、背景をイメージに設定し、そのイメージおよびそのイメージのソースを表す要素を、入れ子にした要素の属性として指定します。  これは、プロパティ要素構文の例です。  
  
 [!code-xml[PropertiesOvwSupport#PESyntaxProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#pesyntaxproperty)]  
  
<a name="setting_properties_code"></a>   
### コードでのプロパティの設定  
 [依存関係プロパティ](GTMT)の値をコードで設定するには、通常、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] "ラッパー" によって公開される set 実装を呼び出すだけで済みます。  
  
 [!code-csharp[PropertiesOvwSupport#ProceduralPropertySet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyset)]
 [!code-vb[PropertiesOvwSupport#ProceduralPropertySet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyset)]  
  
 プロパティ値を取得する場合も、基本的に get "ラッパー" 実装を呼び出します。  
  
 [!code-csharp[PropertiesOvwSupport#ProceduralPropertyGet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyget)]
 [!code-vb[PropertiesOvwSupport#ProceduralPropertyGet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyget)]  
  
 また、プロパティ システム [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] <xref:System.Windows.DependencyObject.GetValue%2A> および <xref:System.Windows.DependencyObject.SetValue%2A> を直接呼び出すこともできます。  これは通常、既存のプロパティを使用する場合は不要ですが \(ラッパーの方が便利で、開発者ツール用のより優れたプロパティが公開されます\)、[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] を直接呼び出す方法は、特定のシナリオに適しています。  
  
 プロパティは、XAML で設定してから分離コードを介してコードでアクセスすることもできます。  詳細については、「[WPF における分離コードと XAML](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)」を参照してください。  
  
<a name="functionality"></a>   
## 依存関係プロパティによって提供されるプロパティ機能  
 依存関係プロパティは、フィールドによって補足されるプロパティとは対照的に、プロパティの機能を拡張する機能を提供します。  多くの場合、このような機能のそれぞれが、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 全体の機能セットの特定の機能を表したりサポートしたりします。  
  
-   [リソース](#setting_properties_resources)  
  
-   [データ バインディング](#setting_properties_data_binding)  
  
-   [スタイル](#setting_properties_styles)  
  
-   [アニメーション](#animations)  
  
-   [メタデータのオーバーライド](#metadata)  
  
-   [プロパティ値の継承](#setting_properties_inheritance)  
  
-   [WPF デザイナーの統合](#vs2008_integration)  
  
<a name="setting_properties_resources"></a>   
### リソース  
 依存関係プロパティの値は、リソースを参照することによって設定できます。  リソースは通常、ページのルート要素またはアプリケーションの `Resources` プロパティ値として指定されます \(これらの場所を使用することが、リソースにアクセスするのに最も便利な方法です\)。  <xref:System.Windows.Media.SolidColorBrush> リソースを定義する方法を次の例に示します。  
  
 [!code-xml[PropertiesOvwSupport#ResourcesResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesresource)]  
  
 リソースを定義すると、リソースを参照し、そのリソースを使用してプロパティ値を指定できるようになります。  
  
 [!code-xml[PropertiesOvwSupport#ResourcesReference](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesreference)]  
  
 この特定のリソースは、[DynamicResource のマークアップ拡張機能](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) として参照されます \(WPF XAML では、静的リソース参照または動的リソース参照を使用できます\)。  動的リソース参照を使用するには、依存関係プロパティに設定している必要があるため、これは具体的には、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムによって有効になる動的リソース参照の使用方法になります。  詳細については、「[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)」を参照してください。  
  
> [!NOTE]
>  リソースはローカル値として扱われます。つまり、別のローカル値を設定すると、リソース参照がなくなります。  詳細については、「[依存関係プロパティ値の優先順位](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)」を参照してください。  
  
<a name="setting_properties_data_binding"></a>   
### データ バインディング  
 依存関係プロパティは、データ バインディングを介して値を参照できます。  データ バインドは、XAML で特定のマークアップ拡張機能構文を介して機能するか、コードで <xref:System.Windows.Data.Binding> オブジェクトを介して機能します。  データ バインディングを使用すると、プロパティ値の最終的な決定が、データ ソースから値が取得される実行時まで延期されます。  
  
 XAML で宣言されたバインディングを使用して、<xref:System.Windows.Controls.Button> の <xref:System.Windows.Controls.ContentControl.Content%2A> プロパティを設定する例を次に示します。  バインディングでは、継承されたデータ コンテキストおよび <xref:System.Windows.Data.XmlDataProvider> データ ソース \(この例には示されていません\) が使用されます。  バインディング自体は、データ ソース内で <xref:System.Windows.Data.Binding.XPath%2A> によって目的のソース プロパティを指定します。  
  
 [!code-xml[PropertiesOvwSupport#BasicInlineBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#basicinlinebinding)]  
  
> [!NOTE]
>  バインディングはローカル値として扱われます。つまり、別のローカル値を設定すると、バインディングがなくなります。  詳細については、「[依存関係プロパティ値の優先順位](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)」を参照してください。  
  
 依存関係プロパティまたは <xref:System.Windows.DependencyObject> クラスは、データ バインディング操作に対応する <xref:System.Windows.DependencyObject> ソース プロパティ値の変更の通知を生成する <xref:System.ComponentModel.INotifyPropertyChanged> をネイティブ サポートしません。  データ バインディング ターゲットに対する変更を報告できる、データ バインディングで使用するためのプロパティを作成する方法の詳細については、「[データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」を参照してください。  
  
<a name="setting_properties_styles"></a>   
### スタイル  
 スタイルおよびテンプレートは、依存関係プロパティの使用に関する 2 つの主なシナリオです。  スタイルは、アプリケーション [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] を定義するプロパティを設定する際に特に役立ちます。  通常、スタイルは XAML のリソースとして定義されます。  スタイルには通常、特定のプロパティの "setter" および別のプロパティのリアルタイム値に基づいてプロパティ値を変更する "トリガー" が含まれるため、スタイルはプロパティ システムと対話します。  
  
 非常に単純なスタイル \(<xref:System.Windows.FrameworkElement.Resources%2A> ディクショナリ内で定義されますが、この例には示されていません\) を作成し、そのスタイルを <xref:System.Windows.Controls.Button> の <xref:System.Windows.FrameworkElement.Style%2A> プロパティに直接適用する例を次に示します。  スタイル内の setter によって、スタイルが適用された <xref:System.Windows.Controls.Button> の <xref:System.Windows.Controls.Control.Background%2A> プロパティが緑色に設定されます。  
  
 [!code-xml[PropertiesOvwSupport#SimpleStyleDef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyledef)]  
  
 [!code-xml[PropertiesOvwSupport#SimpleStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyle)]  
  
 詳細については、「[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)」を参照してください。  
  
<a name="animations"></a>   
### アニメーション  
 依存関係プロパティは、アニメーション化することができます。  アニメーションが適用されて実行されると、アニメーション化された値は、それ以外の場合のプロパティの値 \(ローカル値など\) よりも高い優先順位で動作します。  
  
 <xref:System.Windows.Controls.Button> プロパティの <xref:System.Windows.Controls.Control.Background%2A> をアニメーション化する例を次に示します \(技術的には、<xref:System.Windows.Controls.Control.Background%2A> はプロパティ要素構文を使用して空白の <xref:System.Windows.Media.SolidColorBrush> を <xref:System.Windows.Controls.Control.Background%2A> として指定することでアニメーション化され、その <xref:System.Windows.Media.SolidColorBrush> の <xref:System.Windows.Media.SolidColorBrush.Color%2A> プロパティが、直接アニメーション化されるプロパティになります\)。  
  
 [!code-xml[PropertiesOvwSupport#MiniAnimate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#minianimate)]  
  
 プロパティのアニメーション化の詳細については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」および「[ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)」を参照してください。  
  
<a name="metadata"></a>   
### メタデータのオーバーライド  
 [依存関係プロパティ](GTMT)の特定の動作は、[依存関係プロパティ](GTMT)を最初に登録したクラスから派生させるときにプロパティのメタデータをオーバーライドすることで変更できます。  メタデータのオーバーライドは、<xref:System.Windows.DependencyProperty> 識別子に依存します。  メタデータのオーバーライドでは、プロパティを再実装する必要はありません。  メタデータの変更は、プロパティ システムでネイティブに処理されます。各クラスは、基本クラスから継承したすべてのプロパティに対して、型ごとに個別のメタデータを保持する可能性があります。  
  
 依存関係プロパティ <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> のメタデータをオーバーライドする例を次に示します。  この特定の依存関係プロパティ メタデータのオーバーライドは、テーマから既定のスタイルを使用できるコントロールを作成する実装パターンの一部です。  
  
 [!code-csharp[PropertiesOvwSupport#OverrideMetadata](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#overridemetadata)]
 [!code-vb[PropertiesOvwSupport#OverrideMetadata](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#overridemetadata)]  
  
 プロパティ メタデータをオーバーライドまたは取得する方法の詳細については、「[依存関係プロパティのメタデータ](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)」を参照してください。  
  
<a name="setting_properties_inheritance"></a>   
### プロパティ値の継承  
 要素は、オブジェクト ツリー内の親から依存関係プロパティの値を継承できます。  
  
> [!NOTE]
>  プロパティ値の継承動作は、すべての依存関係プロパティにグローバルに有効にはなりません。これは、継承の計算時間がパフォーマンスに影響するからです。  プロパティ値の継承は通常、特定のシナリオでプロパティ値の継承が適切であると示されるプロパティに対してのみ有効にします。  SDK リファレンスで、依存関係プロパティの「依存関係プロパティの情報」セクションを調べて、依存関係プロパティで継承を行うかどうかを決定できます。  
  
 次の例ではバインディングを示し、前述のバインディングの例では示されていなかったバインディングのソースを指定する <xref:System.Windows.FrameworkElement.DataContext%2A> プロパティを設定します。  子オブジェクトの以降のバインディングではソースを指定する必要はなく、親 <xref:System.Windows.Controls.StackPanel> オブジェクトの <xref:System.Windows.FrameworkElement.DataContext%2A> から継承された値を使用できます   \(または、子オブジェクトが独自の <xref:System.Windows.FrameworkElement.DataContext%2A> または <xref:System.Windows.Data.Binding> の <xref:System.Windows.Data.Binding.Source%2A> を直接指定し、そのバインディングのデータ コンテキストに継承された値を意図的に使用しないようにすることもできます\)。  
  
 [!code-xml[PropertiesOvwSupport#InheritanceContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#inheritancecontext)]  
  
 詳細については、「[プロパティ値の継承](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)」を参照してください。  
  
<a name="vs2008_integration"></a>   
### WPF デザイナーの統合  
 依存関係プロパティとして実装されるプロパティを使用するカスタム コントロールは、適切な [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] のサポートを受けます。  1 つの例として、**\[プロパティ\]** ウィンドウで、直接依存関係プロパティと添付依存関係プロパティを編集できる機能が挙げられます。  詳細については、「[コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)」を参照してください。  
  
<a name="value_determination"></a>   
## 依存関係プロパティ値の優先順位  
 [依存関係プロパティ](GTMT)の値を取得する場合、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムに関係する他のプロパティに基づく入力のいずれかを介して、そのプロパティに設定された値を取得する可能性があります。  プロパティの値の取得方法に関するさまざまなシナリオが予測可能な方法で相互作用できるように、依存関係プロパティ値の優先順位が存在しています。  
  
 例を次に示します。  この例には、すべてのボタンおよびそれらの <xref:System.Windows.Controls.Control.Background%2A> プロパティに適用されるスタイルが含まれていますが、<xref:System.Windows.Controls.Control.Background%2A> 値がローカルに設定されているボタンも 1 つ指定されています。  
  
> [!NOTE]
>  SDK ドキュメントでは、依存関係プロパティについて説明するときに、"ローカル値" または "ローカルに設定された値" という用語が使用される場合があります。  ローカルに設定された値は、コードでオブジェクト インスタンスに直接設定されたプロパティ値または XAML で要素の属性として設定されたプロパティ値です。  
  
 原則として、最初のボタンではプロパティが 2 回設定されますが、適用される値は 1 つだけで、優先順位が最も高い値が適用されます。  ローカルに設定された値の優先順位が最も高いため \(実行中のアニメーションを除きますが、この例ではアニメーションは適用されていません\)、最初のボタンの背景に対するスタイル setter の値ではなくローカルに設定された値が使用されます。  2 番目のボタンにはローカル値が設定されていないため \(また、優先順位がスタイル setter より高い値が他にないため\)、そのボタンの背景はスタイル setter に基づきます。  
  
 [!code-xml[PropertiesOvwSupport#MiniPrecedence](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#miniprecedence)]  
  
### 依存関係プロパティの優先順位が存在する理由  
 通常、スタイルを常に適用し、個別の要素のローカルに設定された値を無効にすることは望ましくありません \(また、一般に、スタイルまたは要素の使用は非常に困難です\)。  そのため、スタイルに基づく値は、ローカルに設定された値よりも低い優先順位で動作します。  依存関係プロパティの詳細なリストおよび依存関係プロパティの有効値を決める要因については、「[依存関係プロパティ値の優先順位](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)」を参照してください。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 要素で定義されるプロパティには、依存関係プロパティではないものが多数あります。  概してプロパティは、プロパティ システムによって可能になる 1 つ以上のシナリオ \(データ バインディング、スタイル設定、アニメーション、既定値のサポート、継承、添付プロパティ、または無効化\) をサポートする必要がある場合にのみ依存関係プロパティとして実装されます。  
  
<a name="dp_implement_roadmap"></a>   
## 依存関係プロパティの詳細情報  
  
-   [添付プロパティ](GTMT)は、XAML で特殊な構文をサポートするプロパティの一種です。  多くの場合、添付プロパティは[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] プロパティと 1 対 1 で対応せず、[依存関係プロパティ](GTMT)であるとは限りません。  [添付プロパティ](GTMT)の一般的な目的は、親要素と子要素がどちらも、クラス メンバー リストの一部としてそのプロパティを処理しない場合でも、子要素が親要素にプロパティ値を報告できるようにすることです。  主なシナリオは、子要素から親要素に [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] でどのように表示するかを通知できるようにすることです。例については、<xref:System.Windows.Controls.DockPanel.Dock%2A> または <xref:System.Windows.Controls.Canvas.Left%2A> を参照してください。  詳細については、「[添付プロパティの概要](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)」を参照してください。  
  
-   コンポーネントまたはアプリケーションの開発者は、データ バインディングやスタイルのサポートなどの機能を有効にするために、または無効化および値の強制のサポートのために、独自の[依存関係プロパティ](GTMT)を作成できます。  詳細については、「[カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)」を参照してください。  
  
-   依存関係プロパティは通常、インスタンスにアクセスできる呼び出し元がアクセス可能か、少なくとも検出可能なパブリック プロパティと見なされます。  詳細については、「[依存関係プロパティのセキュリティ](../../../../docs/framework/wpf/advanced/dependency-property-security.md)」を参照してください。  
  
## 参照  
 [カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [読み取り専用の依存関係プロパティ](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md)   
 [XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [WPF アーキテクチャ](../../../../docs/framework/wpf/advanced/wpf-architecture.md)